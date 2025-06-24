<script>
  export let titre = '';
  export let enonce = '';
  export let correction = '';
  export let difficulte = 1;
  export let chapitre = '';
</script>

<div class="border rounded-lg p-4 mb-4 bg-white shadow">
  <div class="flex items-center justify-between mb-2">
    <h2 class="text-xl font-bold">{titre}</h2>
    <div class="flex items-center">
      {#each Array(5) as _, i}
        <span class={i < difficulte ? 'text-yellow-400' : 'text-gray-300'}>★</span>
      {/each}
    </div>
  </div>
  <div class="text-sm text-gray-500 mb-2">Chapitre : <span class="font-medium text-gray-700">{chapitre}</span></div>
  <div class="mb-2">
    <div class="font-semibold">Énoncé :</div>
    <div class="ml-2">
      <slot name="enonce">
        {@html enonce}
      </slot>
    </div>
  </div>
  <details class="mt-2">
    <summary class="cursor-pointer font-semibold text-blue-600">Correction</summary>
    <div class="ml-2 mt-1">
      <slot name="correction">
        {@html correction}
      </slot>
    </div>
  </details>
</div> 