<script>import '../app.css';
import { onMount } from 'svelte';

onMount(() => {
  if (!window.MathJax) {
    window.MathJax = {
      tex: {
        inlineMath: [['$', '$'], ['\\(', '\\)']],
        displayMath: [['$$', '$$'], ['\\[', '\\]']]
      }
    };
    const script = document.createElement('script');
    script.id = 'MathJax-script';
    script.async = true;
    script.src = 'https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js';
    document.head.appendChild(script);
  }
});

export function typesetMath() {
  console.log('typesetMath called');
  if (window.MathJax && window.MathJax.typesetPromise) {
    window.MathJax.typesetPromise();
  } else {
    setTimeout(typesetMath, 100);
  }
}


</script>

<slot />
