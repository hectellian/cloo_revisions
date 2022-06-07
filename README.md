# CLOO notes

## Enumérations

## Généricité et variance

Apres avoir defini une simple classe, pendant l'appel d'une de ses methodes il est possible d'avoir un type different de celui voulu, il est donc
necessaire de tester les instances pour etre sur d'avoir le bon type. Ceci rajoute enormement de code non necessaire et on peut ce perdre facilement.

Viens alors les _generiques_ $\rightarrow$ rajoute une forme de polymorphisme par parametricite permettant d'ajouter un objet d'un certain type

Definition d'une classe avec un generique en Java:

```java
public class Stack<T> { // T n'est connu que a la compilation
...
}
// Creation d'une stack de strings
Stack<String> stack = new Stack<String>();
```

Autre utilisation $\rightarrow$ Tableau dynamique:

```java
var l = new ArrayList<String>();
```

## Héritage et agrégation

- ### **Agregation**

  Membres d’une classe $\rightarrow$ aussi refs vers instances

## Héritage et polymorphisme

## Héritage: redéfinition des méthodes

- Mécanisme qui permet à une classe d’obtenir la structure et le comportement de la super classe
- Toute classe $\rightarrow$ implémentation par défaut de plusieurs méthodes <- **Object class hérédité**:

```java
public String toString();
```

```java
public boolean equals();
```

```java
public int hashCode();
```

## Identité et Égalité

- ### **Identite**

  - Opérateur `==` retourne vrai ssi les 2 refs pointent sur la m instance

---

- ### **Egalite**

  - Methode `equals`
  - Par défaut $\rightarrow$ m effet que identite
  - Redéfinition $\rightarrow$ pour tester l'égalité entre valeurs

---

- ### **Code de hachage**

  - Valeur numérique calc pour chaque instance
  - Si `x.equals(y)` $\Rightarrow$ `x.hashCode()` = `y.hashCode()`
  - Redefinition `equals` $\Rightarrow$ redefinition hashCode
  - **Criteres**:
    - Aussi rapide que possible
    - m champs que `equals`
    - Repose sur appel à l'autre
    - Retourne des valeurs réparties sur `int`

---

- ### **Value Object vs Entity**

  - 2 types de Objects:
    - **Value Objects**: Definis par la valeur de leur champs
      - si m valeurs $\Rightarrow$ m objet
      - Egalite $\rightarrow$ Toujours redefinir `equals`
    - **Entity Objects**:
      - Definis par la structure de leur champs
      - m objet peut avoir des valeurs différentes au cours du temps
      - Identite
      - Gerer cycle de vie

## Lambda expressions

## Mutabilité et immutabilité

- **Par défaut** $\rightarrow$ tout est **mutable** [JAVA]
- Variable:

```java
int i = 12; // mutable
```

Mot cle final $\rightarrow$ rendre immutable

```java
final int i = 12; //immutable
```

> Ne pourra jamais changer dans le futur

---

## Polymorphisme et interfaces

- ### Sous-Typage

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

- ### Polymorphisme

  - Plusieurs comportements -$\rightarrow$ unique symbol
    - ad-hoc $\rightarrow$ surchage
    - par sous-typage $\rightarrow$ interface
    - par parametricite

---

- ### Interface

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

- ### Fake It Till Make It

  - utilisation d'interface pour remplacer un composant pas encore ecrit
  - _mock implementation_ ou _dommy object_ en anglais, une fausse implementation pour les tests.

- ATTENTION AU EXCES

---

- ### Exceptions et Erreurs

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

- ### Lever une exception:

  - Pourquoi? $\rightarrow$ Anticiper un probleme
  - Java $\rightarrow$ mot cle `throw` suivi d’une instanciation de l’exception

- Important de creer un gestionnaire $\rightarrow$ dependace a des choses que l'on ne peut pas controler

- ### Gerer une exception (different comportements)

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

- ### Problemes des exceptions

  - Plein de code partout pour gerer
  - Exception non attrapée $\rightarrow$ propagation et donc problemes
  - Comment faire?
    - Utiliser exceptionnellement
    - Anticiper le probleme
    - Utiliser le type retour
    - Ne pas utiliser pour la logique

---



## Principe de substitution de Liskov

## Références et construction

- Inference de type:
- mot cle `var`
- privilegier la lisibilite $\rightarrow$ **pas abuser**

```java
var i = 12; // detection de type int
```

---

- ### Déclaration de tableau

  - Taille fixe
  - Init dans le tas (**heap**)
  - x est une reference
    - Similaire à un pointeur
  - **Garbage-Collector** $\rightarrow$ free la mémoire quand plus aucune références ne pointe sur un objet <$\Rightarrow$ `free()` en c

```java
int[] x = new int[12]; // tab of size 12 int
```

> Tableau vide

---

- ### **Encapsulation**

  - Approche consistant à cacher l'état et l'implémentation des données, derrière des fonction de plus haut
  - **Avantage**:
    - Plus evolutif
    - Plus reutilisable
    - Plus simple à apprendre
    - Plus testable
  - **Inconvenient**:
    - Plus difficile a optimiser

---

- ### Package

  - Regrouper les classes
  - Espaces de noms (**namespace**) pour éviter les collisions
  - Hierarchique

---

- ### Classes et instances

  - Definition: **Classe** $\rightarrow$ type compose [JAVA]
    - **Instance** $\rightarrow$ valeur d’une classe
    - **Objet** $\rightarrow$ instance ou classe
    - **Membre** $\rightarrow$ variable ou fonction déclarées
    - **Champ** $\rightarrow$ variable membre
    - **Méthode** $\rightarrow$ fonction membre
  - L’operateur `.` (**point**) permet d'accéder aux champs et méthodes d’une instance
  - **Constructeur**:
    - Construit l’instance
    - m nom que l’instance
    - Pas de return
    - Appelé après l’alloc de l’instance
    - **Surcharge** $\rightarrow$ plusieurs constructeurs
    - Pas de constructeurs $\Rightarrow$ un par défaut genere, vide
  - Reference **`this`**
    - Chaque instance a un accès vers elle m $\rightarrow$ `this`
    - Utilisation des membres localement cachés par autre variables
    - Lisibilite
    - Return instances de sois m
  - JAVA: Toutes classes derivent d'une autre classe $\rightarrow$ Object
    - 2 effets de derivation
      - sous-typage
      - heritage

```java
Point p = new Point(1.0, 0.5);
```

---

- ### Sémantique par référence

  - S’applique toujours au instances
  - cf. voir tableaux exemples

  - On peut définir plusieurs méthodes ou constructeurs avec le **m nom** dans la m classe si les **args sont différents** $\rightarrow$ **surcharge**

    > **m effet final**

## Références et passage d'argument

- ### Fonctions

```java
static type nom(parametres);
```

> - Aussi appelé méthode de classes

- L’appel de la fonction copie les arguments
  - modification aucun effet en dehors de la fonction
    > Exemple pas a pas $\rightarrow$ cours p.29-34

## Références, méthodes et mutabilité

- Considérer **immutabilité par défaut**
  - Plus simple a analyser
  - Moins de bugs
  - Thread safe
  - Plus facile de changer d’avis

## Visibilité et contrôle d'accès

visibilite $\rightarrow$ propriété contextuel $\Rightarrow$ dépendante de l'endroit ou on se trouve. On peut voir certains attirbut a un endroit mais pas un autre

Contrôle d'accès $\rightarrow$ notion fortement liée à la visibilité $\Rightarrow$ ce qui ne peut pas etre vu, ne peut pas etre directement accedé

- ### Modificateurs d'accès

  - differents mots-clefs liés à la visibilité et à l'accès
  - Control d'accès des membres en Java:
    - `public` $\rightarrow$ accès/utilisation partout
    - `private` $\rightarrow$ acces/utilisation uniquement par les instances de la m classe
    - `default` $\rightarrow$ ($\iff$ aucun mot clé) accès/utilisation uniquement dans le m package
    - `protected` $\rightarrow$ accès/utilisation uniquement dans le m package ou est definie sa classe à l'exception d'une sous-classe de la classe de l'attribut.

- ### **Recommendations**

  - Tout champs $\rightarrow$ `private`
  - Moins de méthode `public` possible
  - Utilisation de methodes _getter_ et _setter_ pour recuperer des informations `private`

---

- Accès lecture (**getter**) et écriture (**setter**) $\rightarrow$ pratique **systématique déconseillées**:
  - Fuite des détails d'implémentation
  - Contraintes et coordination plus difficile
  - Synchronisation plus difficile
  - cf. [why getter and setter are evil](https://web.archive.org/web/20200729073721/https://www.infoworld.com/article/2073723/why-getter-and-setter-methods-are-evil.html)
- **Recommendations**:
  - retourner des _interfaces_ $\rightarrow$ cacher les details d'implementation
    - Plus simple a modifier si l'on decide de changer un type par exemple
