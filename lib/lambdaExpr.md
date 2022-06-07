# Lambda Expressions

En *java*, il existe plusieurs objets annonymes, les *Lambda Expressions* et les *Classes Annonymes*.

Les *lambdas expressions* sont un concepte commun de l'orienté objet qui repose en vérité sur une approche plus fonctionnelle de programmation. Contrairement aux *Classes Annonymes* qui sont un spécifique *java*.

## Classes Annonymes

Les *classes Annonymes* sont comme leurs noms l'indique des *classes*, celles-ci sont définie autour d'une interface. C'est-à-dire qu'il existe une *interface* qui définie les méthode nécessaire et la classe annonymes définie leur implémentation. Par exemple:

```java
public interface Armure {
    public int absorb(int dmg);
}

public class Main {

    public static void main(String[] args){
        Armure chain_mail = new Armure() {
            public int absorb(int dmg){
                int ndmg = dmg-15;
                if (ndmg>0) {return ndmg;}
                return 0;
            }
        };

        var leather_arm = new Armure(){
            public int absorb(int dmg){
                if (dmg-1 > 0) {return dmg-1;}
                return 0;
            }
        };
    }
}
```

On peut voir ici que `chain_mail` et `leather_arm` sont deux *classes annonymes* différentes qui représentes deux implémentations possible de l'*interface* `Armure`.

## Expressions Lambdas

Les *Expressions Lambdas* est un concepte nommé en référence au *Lambda calcul*, il s'agit d'un concept récurrent de l'orienté objets, on le voit nôtament en *python*, *java* ou encore *swift*.

Le principe est simple, il s'agit d'une fonction non nommé qui peut-être passé en paramètre ou encore retouné par une autre fonction.
Par exemple en *java*:

```java
(int a, int b) -> {a+b}; //ou encore:
(a,b) -> a+b;
```

Ou en *python*:

```python
lambda a,b: a+b
```

## Lambda Expressions VS Classes Anonymes

En *java* une *expression lambda* peut aussi être combiné avec une *interface* du façon similaire à une *classe annonyme*, à condition que cette *interface* ne possède qu'une unique fonction. Par exemple, si on reprend l'*interface* `Armure` précédente:

```java
Armure chain_mail = (int dmg) -> {
    if (dmg > 15) {return dmg-15;}
    return 0;
};
```

Il est important de noter que à l'inverse d'une *classe annonyme*, le type d'une *lambda expression* ne peut-être inférer le type de retour, elles ne sont pas utilisable avec le mot-clef `var`.

De plus, sûr un grand nombre d'opération les *lambda expressions* se révèle beaucoup moins coûteuse en temps de calcul et mémoire aue leur contre-partir classé.

## Extensions des Lambda Expression et Classes Annonymes

Ces deux concepts se mélange particulièrement bien avec le concept de généricité avec des types générique. Par exemple, en *java* dans le cas d'un générateur de valeur aléatoire:

```java
import java.util.Random;

public interface RandomGenerator<T>{
    public T single(Random rng);
}

public class Main {
    public static RandomGenerator<HealingPotion> anonymous_healingPotionRG(HealingPotion hp)  {
        return new RandomGenerator<>() {
            public HealingPotion single(Random rng){
                return hp.genItem(rng);
            }
        };
    }
    public static RandomGenerator<HealingPotion> lambda_healingPotionRG(HealingPotion hp){
        return (Random rng) -> {return hp.genItem(rng);};
    }

    public static void main(String[] args){
        HealingPotion potionAnonyme = anonymous_healingPotionRG(new HealingPotion()).single(gameRNG);

        HealingPotion potionLambda = lambda_healingPotionRG(new HealingPotion()).single(gameRNG);
    }
}
```

Les deux fonctions font exactement la même chose, elles génèrent toute les deux un objet de l'interface demander. Mais on peut tou de suite voir que la version avec une *lambda expression* est beaucoup plus légère et compréhensible que sa contrepartie.

De plus, le mélange avec les *types générique* est particulièrement facile.

Un autre point particulièrement utils des *lambda expressions* en *java* est que celles-ci se conforme aux *interfaces* demandé en paramètres pour différentes tels que les *stream* par exemple la méthode `map` d'un *stream* prend en paramètre une fonction ou la méthode `filter` prend en paramètre un *prédicat*.

$\uparrow$

Taken from [Ethan](https://github.com/dracoanguis/Objet-Oriente/blob/main/Preparation_Oral.md#expressions-lambdas)
