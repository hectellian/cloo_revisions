# Polymorphisme et interfaces

## Sous-Typage

- T <: U <$\Rightarrow$ Tout les type de T sont des types de U
- Si T <: U on peut assigner une valeur de type T à une ref de type U
- Relation **transitive**
- On peut assigner a une ref de type Object
  - Compilateur perd la trace du sous-jacent
- Test du type sous-jacent d'une instance avec `instanceof` $\rightarrow$ a l'execution
- Forcer la conversion d'un type a l'execution
  - Erreur de compilation si non $\iff$
      > tout combiner avec `if` pour proteger la conversion

---

## Polymorphisme

- Plusieurs comportements -$\rightarrow$ unique symbol
  - ad-hoc $\rightarrow$ surchage
  - par sous-typage $\rightarrow$ interface
  - par parametricite $\rightarrow$ generics

---

## Interface

- Abstraction permettent d'exprimer des contraintes sur la presence de methode et signatures
- sous-typage
- forme de contract, analogue a un protocole de communication
- syntaxe similaire a une classe:
  - methode abstraite $\rightarrow$ non implémentée
  - pas de champs
  - pas de membres prives
- mot cle `implements`
- doit implementer toutes les méthodes abstraites
- **Limitations**:
  - pas de constructeur abstrait $\rightarrow$ il existe une _abstract factory_
  - pas de champs abstraits

---

## Fake It Till Make It

- utilisation d'interface pour remplacer un composant pas encore ecrit
- _mock implementation_ ou _dommy object_ en anglais, une fausse implementation pour les tests.

- ATTENTION AU EXCES

---

## Exceptions et Erreurs

- **Throwable**
  - super type de toutes les exceptions et erreurs
- **Error**
  - ne **doit pas** etre geree
  - problèmes graves dus a l’env:
    - manques de memoire
    - bug dans la JVM
    - etc…
- **Exceptions**
  - **doit** etre geree
  - problèmes imprévisibles à gérer:
    - problèmes d’IO
    - time-out
    - _thread_ interrompu
- **RuntimeException**
  - **peut** etre geree
  - liés à des erreurs de programmation:
    - dépassement de tableau
    - arg invalide
    - erreur de conversion
    - etc…

## Lever une exception

- Pourquoi? $\rightarrow$ Anticiper un probleme
- Java $\rightarrow$ mot cle `throw` suivi d’une instanciation de l’exception

- Important de creer un gestionnaire $\rightarrow$ dependace a des choses que l'on ne peut pas controler

## Gerer une exception (different comportements)

- Terminer l'application
- Journaliser ou notifier l'exception
- Utiliser une valeur par default
- Ressayer
- Essayer un plan B
- Lever une autre exception
- Ignorer (mauvaise idee)

- **Gestionnaire d'exception Java**

  - 3 parties:
  
    1. Tentative d'execution de code $\rightarrow$ `try`
    2. Capture d'exceptions produite $\rightarrow$ `catch`
    3. (Optionel) Code execute dans tous les cas a la fin $\rightarrow$ toujours execute

---

## Problemes des exceptions

- Plein de code partout pour gerer
- Exception non attrapée $\rightarrow$ propagation et donc problemes
- Comment faire?
  - Utiliser exceptionnellement
  - Anticiper le probleme
  - Utiliser le type retour
  - Ne pas utiliser pour la logique
