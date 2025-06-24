<script>
  export const titre = "Dérivation simple";
  import Exercice from '$lib/Exercice.svelte';

  let enonce = `
  Soit $f(x) = x^2 + 3x + 2$. Calculez $f'(x)$. pour $x \\in \\mathbb{R}$.
  `;
  let correction = `
  La dérivée est $f'(x) = 2x + 3$.
  `;
</script>

<Exercice
  titre={titre}
  enonce={enonce}
  correction={correction}
  difficulte={2}
  chapitre="Dérivation"
/> 