- Date de début : 21/07/2023
- Version majeure cible : v3
- PR d'implémentation : 

## Résumé

Utilisation de [Vitest][Vitest] pour le Starter Kit Vue.

## Exemple simple

```js
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

La nouvelle structure du projet étant basée sur Vite, Vitest semble être un choix naturel pour les tests unitaires.

## Conception détaillée

Les utilisateurs devront [installer vitest][pnpm add -D vitest] avant de créer un nouveau projet.
NB : un plugin existe éalement pour Nuxt : [nuxt-vitest][nuxt-vitest]

Si un utilisateur souhaite migrer un projet existant, il devra supprimer le répertoire `node_modules` de son projet ainsi que le fichier `yarn.lock`, puis exécuter la commande `pnpm install` et commiter le résultat.

## Désavantages

L'utilisation de Vitest pourrait nécessiter la réécriture des tests existants et une certaine formation pour les développeurs qui ne sont pas familiers avec la bibliothèque mais cela devrait être minime car Vitest est très proche de Jest.

## Alternatives

D'autres frameworks de tests unitaires Cypress pourraient être utilisés à la place de Vitest. 

Vitest et Cypress sont tous deux d'excellentes options pour les tests unitaires dans les projets JavaScript, mais ils ont des cas d'utilisation et des compromis différents.

Vitest est un framework de test unitaire conçu spécifiquement pour tester des unités individuelles de code, telles que des fonctions ou des composants. Il est léger, rapide et facile à configurer, ce qui en fait un bon choix pour les développeurs qui veulent écrire et exécuter des tests rapidement. Vitest est également conçu pour fonctionner avec Vite, un serveur de développement rapide qui utilise le rechargement instantané de modules (HMR) pour accélérer le processus de développement.

Cypress, en revanche, est un framework de test de bout en bout conçu pour tester l'ensemble de l'application, de l'interface utilisateur au backend. Il est plus lourd et nécessite plus de configuration, mais il peut fournir une vue plus complète du comportement et des interactions de l'application. Cypress est également conçu pour fonctionner avec un serveur de test dédié, ce qui peut le rendre moins adapté au développement et aux tests rapides.

En résumé, Vitest est un bon choix pour les développeurs qui veulent se concentrer sur les tests unitaires et le développement rapide, tandis que Cypress est un bon choix pour les développeurs qui veulent tester l'ensemble de l'application et avoir une couverture de test plus complète. En fin de compte, le choix entre Vitest et Cypress dépendra des besoins et des objectifs spécifiques du projet.

## Stratégie d'adoption

Ce changement ne concerne que la création de nouveaux projets et n'impacte donc pas les projets existants qui pourront rester sur [JEST] ou faire le choix de la migration.

[Vitest]: https://vitest.dev/
[nuxt-vitest]: https://nuxt.com/modules/vitest
[JEST]: https://jestjs.io/
