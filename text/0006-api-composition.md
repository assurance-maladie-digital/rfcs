- Date de début : 25/07/2023
- Version majeure cible : v3
- PR d'implémentation : N/A

## Résumé

Cette RFC propose l'ajout de l'[API Composition] comme syntaxe alternative à la syntaxe de classes via [Vue Class Component], pour la création de composants Vue.

## Motivation

L'API Composition de Vue offre plusieurs avantages par rapport à la syntaxe de classes [Vue Class Component], notamment :

Meilleure séparation des préoccupations : 
L'API Composition permet de séparer clairement la logique de l'état et du comportement du composant des détails de la configuration et des options de Vue, ce qui rend le code plus facile à comprendre et à maintenir.

Meilleure réutilisabilité du code : 
L'API Composition permet de définir des fonctions de composition qui peuvent être réutilisées dans plusieurs composants, ce qui permet d'éviter la duplication de code et de maintenir une base de code plus propre et plus facile à gérer.

Meilleure compatibilité avec les outils modernes : 
L'API Composition est mieux adaptée aux outils modernes tels que TypeScript et les linters, car elle permet de définir des types pour les propriétés et les fonctions de composition, ce qui facilite la détection des erreurs de code et améliore la qualité du code.

Amélioration de la lisibilité : 
L'API Composition permet de définir la logique d'un composant de manière plus sous la forme de fonctions de composition plutôt que de propriétés et de méthodes imbriquées, ce qui facilite la lecture et la compréhension du code.

En somme, l'API Composition est une approche plus moderne et plus efficace pour structurer les composants Vue, offrant une meilleure séparation des préoccupations, une meilleure réutilisabilité du code, une meilleure compatibilité avec les outils modernes et une amélioration de la lisibilité du code.

## Conception détaillée

L'API Composition sera intégrée à Vue comme une fonctionnalité native, et pourra être accessible via le module `@vue/composition-api`.

Les fonctions de composition seront utilisées pour définir la logique de l'état et du comportement du composant. Les hooks de composition seront utilisés pour la gestion du cycle de vie du composant.

Un exemple simple d'utilisation de l'API Composition :

```js
import { reactive, computed } from '@vue/composition-api';

export default {
  setup() {
    const state = reactive({
      count: 0,
    });

    const increment = () => {
      state.count++;
    };

    const doubleCount = computed(() => state.count * 2);

    return {
      state,
      increment,
      doubleCount,
    };
  },
};
```

## Désavantages

L'API Composition peut augmenter la complexité les développeurs, qui devront apprendre une nouvelle manière de structurer leurs composants. 

L'ensemble des composants existants devront également être migrés vers l'API Composition, ce qui peut être une tâche fastidieuse et source d'erreurs.

## Alternatives

Une alternative serait de ne pas ajouter l'API Composition et de continuer à utiliser la syntaxe de classes pour structurer les composants.

## Stratégie d'adoption

Les développeurs des projets existants pourront adopter l'API Composition en important le module @vue/composition-api et en utilisant les fonctions de composition dans leurs composants. Pour les nouveaux projets, l'API Composition sera activée par défaut.

Il est également possible d'utiliser le projet vue-class-component pour les projets qui souhaitent continuer à utiliser la syntaxe de classes. Cependant, nous recommandons aux développeurs de migrer vers l'API Composition pour bénéficier de ses avantages.

[API Composition]: https://vuejs.org/guide/extras/composition-api-faq.html
[Vue Class Component]: https://class-component.vuejs.org/
