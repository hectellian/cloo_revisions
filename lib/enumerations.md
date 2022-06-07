# Enumérations

## Definition

Une énumération est un ensemble prédéfini de constantes. Par exemple:

- mois dans l'année: janvier, février,...
- état d'une porte: ouvert, fermé, vérouillé
- couleurs aux échecs
- couleurs de cartes
- ...

Selon les langages ses constantes sont représenté par le système de différentes manières, en C par exemple ses constantes sont enfait des entiers, cela peut nôtament causer des erreurs de nomage, alors qu'en java il s'agit d'un type a part entière.

Les énumérations sont particulièrement utiles pour tester des égalités prédéfinit ou des états. Elles sont généralement utilisées en combinaisons avec des switch case puisqu'elles possèdent des valeurs fixe.

## Exemple d'énumération en *java*

Déclaration d'une énumération:

```java
public enum DoorState {
    OPEN, CLOSED, LOCKED
}
```

Utilisation d'une énumération:

```java
import static DoorState.*;

DoorState open( DoorState current ) {
    if( current == CLOSED )
        return OPEN;
    else if( current == LOCKED )
        throw new IllegalStateException("Cannot open a locked door");
    else throw new IllegaleStateException("Door is already open !");
}
```

Utilisation en combinaison avec un `switch case`:

```java
import static DoorState.*;

DoorState open( DoorState current ) {
    switch(current) {
        case CLOSED:
            return OPEN;
        case LOCKED:
            throw new IllegalStateException("Cannot open a locked door");
        case OPEN:
            throw new IllegaleStateException("Door is already open !");
    }
}
```

$\uparrow$

Taken from [Ethan](https://github.com/dracoanguis/Objet-Oriente/blob/main/Preparation_Oral.md#enumérations)
