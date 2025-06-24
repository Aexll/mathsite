# Exercice 3 : Théorème du point fixe de Knaster-Tarski (cas particulier)

## Énoncé

Soit $E$ un ensemble. On munit $\mathcal{P}(E)$ de la relation d'inclusion $\subseteq$.
Soit $f: \mathcal{P}(E) \to \mathcal{P}(E)$ une application croissante, c'est-à-dire que pour tous $X, Y \in \mathcal{P}(E)$, si $X \subseteq Y$, alors $f(X) \subseteq f(Y)$.

On veut montrer que $f$ possède un point fixe (un ensemble $M$ tel que $f(M)=M$).

Pour cela, on pose $\mathcal{A} = \{A \in \mathcal{P}(E) \mid A \subseteq f(A)\}$ et $M = \bigcup_{A \in \mathcal{A}} A$.

Montrer que $M \subseteq f(M)$, puis que $f(M) \subseteq M$, pour en déduire que $f(M)=M$.

---

## Correction

Cet exercice propose de démontrer un cas particulier du théorème du point fixe de Knaster-Tarski.
L'ensemble $\mathcal{A}$ est l'ensemble des "pré-points fixes" de $f$. Notons que $\mathcal{A}$ n'est pas vide, car $\emptyset \in \mathcal{P}(E)$ et $\emptyset \subseteq f(\emptyset)$, donc $\emptyset \in \mathcal{A}$.

### 1. Montrons que $M \subseteq f(M)$

Par définition, $M$ est la réunion de tous les ensembles $A$ qui sont dans $\mathcal{A}$.
Soit $A \in \mathcal{A}$. Par définition de $\mathcal{A}$, on a $A \subseteq f(A)$.

De plus, par définition de la réunion $M$, on a $A \subseteq M$.

Puisque $f$ est croissante, de $A \subseteq M$, on peut déduire que $f(A) \subseteq f(M)$.

En combinant les inclusions, nous avons pour un $A$ quelconque dans $\mathcal{A}$ :

$$A \subseteq f(A) \subseteq f(M)$$

Cette relation est vraie pour **tous** les ensembles $A \in \mathcal{A}$.

Puisqu'elle est vraie pour tous les $A \in \mathcal{A}$, elle est vraie pour leur réunion.
Ainsi, la réunion de tous ces $A$ est elle-même incluse dans $f(M)$ :

$$\bigcup_{A \in \mathcal{A}} A \subseteq f(M)$$

Or, $M = \bigcup_{A \in \mathcal{A}} A$. On a donc bien montré que $M \subseteq f(M)$.

*Remarque :* Le fait que $M \subseteq f(M)$ signifie que $M$ est lui-même un élément de $\mathcal{A}$. C'est donc le plus grand pré-point fixe de $f$.

### 2. Montrons que $f(M) \subseteq M$

Nous venons de montrer que $M \subseteq f(M)$.
Puisque l'application $f$ est croissante, on peut appliquer $f$ à chaque membre de cette inclusion :

$$f(M) \subseteq f(f(M))$$

Cette nouvelle relation $f(M) \subseteq f(f(M))$ nous dit quelque chose d'intéressant sur l'ensemble $f(M)$.
Elle signifie que l'ensemble $X = f(M)$ vérifie la propriété $X \subseteq f(X)$.

Par définition de l'ensemble $\mathcal{A}$, tout ensemble vérifiant cette propriété est un membre de $\mathcal{A}$.
Donc, $f(M) \in \mathcal{A}$.

Maintenant, rappelons la définition de $M$ : $M$ est la réunion de **tous** les éléments de $\mathcal{A}$.
Puisque $f(M)$ est un élément de $\mathcal{A}$, il est l'un des ensembles que l'on réunit pour former $M$.
Par conséquent, $f(M)$ doit être inclus dans la réunion de tous les éléments, c'est-à-dire $M$ :

$$f(M) \subseteq M$$

### Conclusion

Nous avons démontré les deux inclusions :

1. $M \subseteq f(M)$
2. $f(M) \subseteq M$

Par double inclusion, on conclut que $f(M) = M$.
L'application $f$ admet donc bien un point fixe. 