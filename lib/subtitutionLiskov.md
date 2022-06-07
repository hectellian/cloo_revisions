# Principe de substitution de Liskov

Une relation _is-a_ entre 2 classes est **necessaire** mais pas **suffisante** pour que l'utilisation d'heritage soit coherante et sensee

Avant tout, il est important de savoir ce qu'est la programmation par contrat

---

## Programmation par contrat

Pour chaque operation, on peut definir des **contraintes**:

- **Pre-conditions** : Contraintes qui doivent etre realisees _avant_ d'effectier l'operation
  - Type des args $\rightarrow$ Java: compilateur
  - Valeur des args $\rightarrow$ verifier les valeurs
  - Etat de l'objet courant $\rightarrow$ ne pas pouvoir utiliser `write` sur un fichier fermé
- **Post-conditions** : Contraintes qui doivent etre realise _apres_ avoir effectue l'operation
  - Type de retour $\rightarrow$ Java compilateur
  - Valeur de retour
  - Etat de l'objet courant
  - Etat des args
- **Invariants** : contraintes toujours realisees. A la fois pre et post conditions
  - Valeur de l'objet courant

---

Viens alors le **principe de substitution de Liskov**:

- Si **S** est une sous classe de **T** $\rightarrow$ on doit pourvoir utiliser une instasnce **S** chaque fois qu'une instance de **T** est attendue, _sans causer de problemes_
- Pour toute sous-classe:
  - Les pre-conditions des methodes de la super classe ne peuvent eter durcies $\rightarrow$ ne peut pas rendre les conditions plus strictes
  - Les post-conditions des methodes de la super classe ne peuvent etre assouplies $\rightarrow$ conditions plus strictes possible
  - Les invariants de la super classe doivent etre preserves tels quels

Definition de Barbara Liskov:

- Soit $\phi$(x) une propriete prouvable a propos d'objets x de type T. Alors $\phi$(y) devrait etre vrai pour un objet y de type S ou S est un sous type de T

Contrairement a l'intuiation, la relation de sout-typage (is-a) n'implique pas une compatibilite de structure, mais de **comportement** $\rightarrow$ ne pas penser en structure mais en comportement

Le comportement depend du programme, donc la question de savoir si **Foo** est une sous classe de **Bar** ne peut etre tranchee sans avoir determine le comportement desire $\rightarrow$ seulement quand on connais le comportement exact on peut savoir si Foo est une sous classe de Bar
