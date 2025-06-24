<script>
  import ExerciceMarkdown from '$lib/ExerciceMarkdown.svelte';
  // Import dynamique de tous les exercices Svelte du dossier src/exercices
  const modules = import.meta.glob('../exercices/*.svelte');

  let exercices = [];
  let selected = 0;
  let loading = true;

  // Charger dynamiquement tous les composants et leur titre (const titre)
  Promise.all(
    Object.entries(modules).map(async ([path, loader]) => {
      const mod = await loader();
      // On récupère le composant et la constante titre exportée
      return {
        titre: mod.titre ?? path.split('/').pop().replace('.svelte', ''),
        composant: mod.default
      };
    })
  ).then(list => {
    // Ajouter l'exercice Markdown à la fin de la liste
    exercices = [
      ...list,
      {
        titre: 'Dérivation (Markdown)',
        composant: ExerciceMarkdown,
        markdownSrc: '/src/exercices_md/derivation.md'
      },
      {
        titre: 'Théorème du point fixe de Knaster-Tarski (cas particulier)',
        composant: ExerciceMarkdown,
        markdownSrc: '/src/exercices_md/exo3.md'
      }
    ];
    loading = false;
  });

  let SelectedComponent;
  let selectedMarkdownSrc = '';
  $: if (exercices.length > 0) {
    SelectedComponent = exercices[selected].composant;
    selectedMarkdownSrc = exercices[selected].markdownSrc;
  }
</script>

<div class="flex min-h-screen bg-gray-50">
  <!-- Menu vertical -->
  <nav class="w-64 bg-white border-r p-4">
    <h2 class="text-lg font-bold mb-4">Exercices</h2>
    {#if loading}
      <div>Chargement...</div>
    {:else}
      <ul>
        {#each exercices as exo, i}
          <li>
            <button
              class="w-full text-left px-2 py-1 rounded hover:bg-gray-100 mb-1 {selected === i ? 'bg-blue-100 font-semibold' : ''}"
              on:click={() => selected = i}
            >
              {exo.titre}
            </button>
          </li>
        {/each}
      </ul>
    {/if}
  </nav>

  <!-- Zone centrale -->
  <main class="flex-1 flex items-center justify-center p-8">
    <div class="max-w-xl w-full">
      {#if !loading && SelectedComponent}
        {#if SelectedComponent === ExerciceMarkdown}
          <ExerciceMarkdown src={selectedMarkdownSrc} />
        {:else}
          <svelte:component this={SelectedComponent} />
        {/if}
      {/if}
    </div>
  </main>
</div>