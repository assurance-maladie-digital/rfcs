- Date de début : 21/07/2023
- Version majeure cible : v3
- PR d'implémentation : 

## Résumé

Utilisation de [Vitest][Vitest] pour le Starter Kit Vue.

## Exemple simple

```
import { describe, it, expect } from 'vitest';
import { mount } from '@vue/test-utils';

import MyTest from '../MyTest.vue';

describe('MyTest', async () => {
	it('is a Vue instance', () => {
		const wrapper = mount(MyTest);
		expect(wrapper).toMatchSnapshot();
	});
});
```

## Motivation

Les applications front construites avec le Starter Kit actuel utilisent [JEST][JEST] pour les tests unitaires. Ce choix a été fait lors de la création de la v2 du Starter Kit dans le but d'avoir un outil de test simple à utiliser et à configurer pour les développeurs.

Vitest est une option intéressante car elle permet d'exécuter les tests unitaires plus rapidement et améliore votre expérience de développement grâce au mode de surveillance par défaut utilisant le rechargement instantané de modules (HMR) de Vite. Vitest offre également une compatibilité avec la plupart des API et des bibliothèques d'écosystème Jest, donc dans la plupart des projets, il devrait être possible de remplacer Jest par Vitest sans difficulté.

## Conception détaillée

Les utilisateurs devront [installer vitest][pnpm add -D vitest] avant de créer un nouveau projet.
NB : un plugin existe éalement pour Nuxt : [nuxt-vitest][nuxt-vitest]

Si un utilisateur souhaite migrer un projet existant, il devra supprimer le répertoire `node_modules` de son projet ainsi que le fichier `yarn.lock`, puis exécuter la commande `pnpm install` et commiter le résultat.

## Désavantages

L'utilisation de Vitest pourrait nécessiter une certaine formation pour les développeurs qui ne sont pas familiers avec la bibliothèque mais cela devrait être minime car Vitest est très proche de Jest.

## Alternatives

D'autres frameworks de tests unitaires Cypress pourraient être utilisés à la place de Vitest. Cependant, Vitest est plus rapide et plus léger que Cypress et permet de tester des composants Vue.js.

## Stratégie d'adoption

Ce changement ne concerne que la création de nouveaux projets et n'impacte donc pas les projets existants qui pourront rester sur [JEST] ou faire le choix de la migration.

[Vitest]: https://vitest.dev/
[nuxt-vitest]: https://nuxt.com/modules/vitest
[JEST]: https://jestjs.io/
