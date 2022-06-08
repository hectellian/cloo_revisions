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
