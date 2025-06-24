<script>
  export const titre = "Intégrale simple";
  import Exercice from '$lib/Exercice.svelte';
  let enonce = `
  on pose $$f(x) = x^2$$ et on veut calculer l'intégrale de $$f$$ entre 0 et 1.
  `;
  let correction = `
  <p>
                Cet exercice propose de démontrer un cas particulier du théorème du point fixe de Knaster-Tarski.
                L'ensemble $$\\mathcal{A}$$ est l'ensemble des "pré-points fixes" de $f$. Notons que $$\\mathcal{A}$$ n'est pas vide, car $$\emptyset \in \mathcal{P}(E)$$ et $$\emptyset \subseteq f(\emptyset)$$, donc $$\emptyset \in \mathcal{A}$$.
            </p>
            
            <h3>1. Montrons que $M \\subseteq f(M)$</h3>
            <p>
                Par définition, $M$ est la réunion de tous les ensembles $A$ qui sont dans $\\mathcal{A}$.
                Soit $A \\in \\mathcal{A}$. Par définition de $\\mathcal{A}$, on a $A \\subseteq f(A)$.
            </p>
            <p>
                De plus, par définition de la réunion $M$, on a $A \\subseteq M$.
            </p>
            <p>
                Puisque $f$ est croissante, de $A \\subseteq M$, on peut déduire que $f(A) \\subseteq f(M)$.
            </p>
            <p>
                En combinant les inclusions, nous avons pour un $A$ quelconque dans $\\mathcal{A}$ :
                \[ A \subseteq f(A)
            </p>
            <p>
                Puisqu'elle est vraie pour tous les $A \\in \\mathcal{A}$, elle est vraie pour leur réunion.
                Ainsi, la réunion de tous ces $A$ est elle-même incluse dans $f(M)$.
                \\[ \\bigcup_{A \\in \\mathcal{A}} A \\subseteq f(M) \\]
                Or, $M = \\bigcup_{A \\in \\mathcal{A}} A$. On a donc bien montré que $M \\subseteq f(M)$.
            </p>
            <p>
                <em>Remarque :</em> Le fait que $M \\subseteq f(M)$ signifie que $M$ est lui-même un élément de $\\mathcal{A}$. C'est donc le plus grand pré-point fixe de $f$.
            </p>

            <h3>2. Montrons que $f(M) \\subseteq M$</h3>
            <p>
                Nous venons de montrer que $M \\subseteq f(M)$.
                Puisque l'application $f$ est croissante, on peut appliquer $f$ à chaque membre de cette inclusion :
                \\[ f(M) \\subseteq f(f(M)) \\]
            </p>
            <p>
                Cette nouvelle relation $f(M) \\subseteq f(f(M))$ nous dit quelque chose d'intéressant sur l'ensemble $f(M)$.
                Elle signifie que l'ensemble $X = f(M)$ vérifie la propriété $X \\subseteq f(X)$.
            </p>
            <p>
                Par définition de l'ensemble $\\mathcal{A}$, tout ensemble vérifiant cette propriété est un membre de $\\mathcal{A}$.
                Donc, $f(M) \\in \\mathcal{A}$.
            </p>
            <p>
                 Maintenant, rappelons la définition de $M$ : $M$ est la réunion de <strong>tous</strong> les éléments de $\mathcal{A}$.
                Puisque $f(M)$ est un élément de $\\mathcal{A}$, il est l'un des ensembles que l'on réunit pour former $M$.
                Par conséquent, $f(M)$ doit être inclus dans la réunion de tous les éléments, c'est-à-dire $M$.
                \\[ f(M) \\subseteq M \\]
            </p>

            <h3>Conclusion</h3>
            <p>
                Nous avons démontré les deux inclusions :
                <ol>
                    <li>$M \\subseteq f(M)$</li>
                    <li>$f(M) \\subseteq M$</li>
                </ol>
                Par double inclusion, on conclut que $f(M) = M$.
                L'application $f$ admet donc bien un point fixe.
            </p>
  
  `;
</script>

<Exercice
  titre={titre}
  enonce={enonce}
  correction={correction}
  difficulte={3}
  chapitre="Intégration"
/> 