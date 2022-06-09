# Références et construction

- Inference de type:
- mot cle `var`
- privilegier la lisibilite $\rightarrow$ **pas abuser**

```java
var i = 12; // detection de type int
```

---

## Déclaration de tableau

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

## **Encapsulation**

- Approche consistant à cacher l'état et l'implémentation des données, derrière des fonction de plus haut
- **Avantage**:
  - Plus evolutif
  - Plus reutilisable
  - Plus simple à apprendre
  - Plus testable
- **Inconvenient**:
  - Plus difficile a optimiser

---

## Package

- Regrouper les classes
- Espaces de noms (**namespace**) pour éviter les collisions
- Hierarchique

---

## Classes et instances

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

## Sémantique par référence

- S’applique toujours au instances
- cf. voir tableaux exemples

- On peut définir plusieurs méthodes ou constructeurs avec le **m nom** dans la m classe si les **args sont différents** $\rightarrow$ **surcharge**

  > **m effet final**

---

## Gerer une [exception](polymorphismeInterfaces.md) (different comportements)

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
    3. (Optionel) Code execute dans tous les cas a la fin $\rightarrow$ `finally` (toujours execute)

---

## Streams

Un **Stream** $\rightarrow$ flux de données

Permet de faire des opérations sur un flux de données, plus rapidement et facilement que d'utiliser une boucle

Il existe 2 types d'opérations sur un flux:

- **Intermediaires**:
  - Produisent un **Stream**
  - Generalement pareseuses (**lazy**) $\rightarrow$ effectuee que en cas de besoin
  - Generalement _stateless_ $\rightarrow$ peuvent process chaque element sans avoir vu le suivant
  - Peuvent court-circuiter le parcours
  - Exemples:
    - `limit(long n)`
    - `skip(long n)`
    - `map(Function<? super T, ? extends R> f)`
    - `filter(Predicate<? super T> p)`
- **Terminales:**
  - Produisent une valeur ou un effet de bord
  - Strictes (inverse de _lazy_)
  - Peuvent court-circuiter le parcours
  - Exemples:
    - Predicats:

Exemple en _java_:

```java
// somme des valeurs non negatives
double sum = lines
  .mapToDouble(Double::parseDouble)
  .filter(x -> x > 0.0)
  .sum();

Stream<Item> items = bag.stream(); // stream of items
```

On peut eviter le **boxing** en utilisant les streams, il existe des version specialises de Stream:

- `IntStream`
- `DoubleStream`
- `LongStream`
