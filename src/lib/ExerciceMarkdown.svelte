<script>
  import { onMount } from 'svelte';
  import markdownit from 'markdown-it';
  import mkKatex from 'markdown-it-katex';

  export let src = '';
  let html = '';

  onMount(async () => {
    const res = await fetch(src);
    const mdText = await res.text();
    const md = markdownit({ html: true, linkify: true }).use(mkKatex);
    html = md.render(mdText);
  });
</script>

<!-- KaTeX CSS pour le rendu des formules -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.16.9/dist/katex.min.css">

<div class="prose max-w-none">
  {@html html}
</div> 