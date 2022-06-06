# CLOO notes

## Enumérations

## Généricité et variance

## Héritage et agrégation

- **Agregation**:
Membres d’une classe -> aussi refs vers instances

## Héritage et polymorphisme

## Héritage: redéfinition des méthodes

- Mécanisme qui permet à une classe d’obtenir la structure et le comportement de la super classe
- Toute classe -> implémentation par défaut de plusieurs méthodes <- **Object class hérédité**:

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

- **Identite**:
    - Opérateur == retourne vrai ssi les 2 refs pointent sur la m instance

---
- **Egalite**:
    - Methode `equals`
    - Par défaut -> m effet que identite
    - Redéfinition -> pour tester l'égalité entre valeurs

---
- **Code de hachage**:
    - Valeur numérique calc pour chaque instance
    - Si x.equals(y) => x.hashCode() = y.hashCode()
    - Redefinition `equals` => redefinition hashCode
    - **Criteres**:
        - Aussi rapide que possible
        - m champs que equals
        - Repose sur appel à l'autre
        - Retourne des valeurs réparties sur `int`

---

- **Value Object vs Entity** 
    - 2 types de Objects:
        - **Value Objects**: Definis par la valeur de leur champs
          - si m valeurs => m objet 
          - Egalite -> Toujours redefinir `equals`
        - **Entity Objects**:
          - Definis par la structure de leur champs
          - m objet peut avoir des valeurs différentes au cours du temps
          - Identite
          - Gerer cycle de vie

## Lambda expressions

## Mutabilité et immutabilité

- **Par défaut** -> tout est **mutable** [JAVA]
- Variable:

```java
int i = 12; // mutable
```

Mot cle final -> rendre immutable

```java
final int i = 12; //immutable
```

> Ne pourra jamais changer dans le futur

---

## Polymorphisme et interfaces

- Polymorphisme
  - Plusieurs comportements --> unique symbol
    - ad-hoc -> surchage
    - par sous-typage -> interface
    - par parametricite

---

- Interface
  - Abstraction permettent d'exprimer des contraintes sur la presence de methode et signatures
  - sous-typage
  - forme de contract, analogue a un protocole de communication
  - syntaxe similaire a une classe:
    - methode abstraite -> non implémentée
    - pas de champs
    - pas de membres prives
  - mot cle `implements`
  - doit implementer toutes les méthodes abstraites
  - **Limitations**:
    - pas de constructeur abstrait -> il existe une *abstract factory*
    - pas de champs abstraits

---

- Fake It Till Make It:
  - utilisation d'interface pour remplacer un composant pas encore ecrit
  - *mock implementation* ou *dommy object* en anglais, une fausse implementation pour les tests.

- ATTENTION AU EXCES

## Principe de substitution de Liskov

## Références et construction

- Inference de type:
- mot cle `var`
- privilegier la lisibilite -> **pas abuser**

```java
var i = 12; // detection de type int
```

---

- Déclaration de tableau:

```java
int[] x = new int[12]; // tab of size 12 int
```

> - Tableau vide
> - Taille fixe
> - Init dans le tas (**heap**)
> - x est une reference
>     - Similaire à un pointeur
> - **Garbage-Collector** -> free la mémoire quand plus aucune références ne pointe sur un objet <=> `free()` en c

---

- **Encapsulation**:
    - Approche consistant à cacher l'état et l'implémentation des données, derrière des fonction de plus haut
    - Avantage:
        - Plus evolutif
        - Plus reutilisable
        - Plus simple à apprendre
        - Plus testable
    - Inconvenient:
        - Plus difficile a optimiser

---
- Package:
    - Regrouper les classes
    - Espaces de noms (namespace) pour éviter les collisions
    - Hierarchique

---
- Classes et instances:
    - Definition: **Classe** -> type compose [JAVA]
        - **Instance** -> valeur d’une classe
        - **Objet** -> instance ou classe
        - **Membre** -> variable ou fonction déclarées
        - **Champ** -> variable membre
        - **Méthode** -> fonction membre
    - L’operateur . (point) permet d'accéder aux champs et méthodes d’une instance
    -  **Constructeur**:
        - Construit l’instance
        - m nom que l’instance
        - Pas de return
        - Appelé après l’alloc de l’instance
        - **Surcharge** -> plusieurs constructeurs
        - Pas de constructeurs => un par défaut genere, vide
    - Reference **`this`**
        - Chaque instance a un accès vers elle m -> `this`
        - Utilisation des membres localement cachés par autre variables
        - Lisibilite
        - Return instances de sois m

```java
Point p = new Point(1.0, 0.5);
```

---
- Sémantique par référence:
    - S’applique toujours au instances
    - cf. voir tableaux exemples


    - On peut définir plusieurs méthodes ou constructeurs avec le **m nom** dans la m classe si les **args sont différents** -> **surcharge**

        > **m effet final**

## Références et passage d'argument

- Fonctions:

```java
static type nom(parametres);
```

> - Aussi appelé méthode de classes
> - L’appel de la fonction copie les arguments

- modification aucun effet en dehors de la fonction
> Exemple pas a pas -> cours p.29-34

## Références, méthodes et mutabilité

- Considérer **immutabilité par défaut**
    - Plus simple a analyser
    - Moins de bugs
    - Thread safe
    - Plus facile de changer d’avis

## Visibilité et contrôle d'accès

- Modificateurs d'accès:
    - Control d'accès des membres:
        - `public` -> accès/utilisation partout
        - `private` -> acces/utilisation uniquement par les instances de la m classe
        - `default` -> accès/utilisation uniquement dans le m package
        - `protected`
- Recommendations:
    - Tout champs -> `private`
    - Moins de méthode `public` possible
- Accès lecture (**getter**) et écriture (**setter**) -> pratique **systématique déconseillées**:
    - Fuite des détails d'implémentation
    - Contraintes et coordination plus difficile
    - Synchronisation plus difficile
    - // TODO: add from [why getter and setter are evil](https://web.archive.org/web/20200729073721/https://www.infoworld.com/article/2073723/why-getter-and-setter-methods-are-evil.html)
