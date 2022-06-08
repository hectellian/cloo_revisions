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
    3. (Optionel) Code execute dans tous les cas a la fin $\rightarrow$ `finally` (toujours execute)

---

## Problemes des exceptions

- Plein de code partout pour gerer
- Exception non attrapée $\rightarrow$ propagation et donc problemes
- Comment faire?
  - Utiliser exceptionnellement
  - Anticiper le probleme
  - Utiliser le type retour
  - Ne pas utiliser pour la logique
