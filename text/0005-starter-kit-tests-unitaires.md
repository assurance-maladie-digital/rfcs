- Date de début : 21/07/2023
- Version majeure cible : v3
- PR d'implémentation : N/A

## Résumé

Utilisation de [Vitest][Vitest] (tests unitaires) pour le Starter Kit Vue.

## Exemple simple

```js
import { describe, it, expect } from "vitest";
import { mount } from "@vue/test-utils";

import MyTest from "../MyTest.vue";

describe("MyTest", async () => {
  it("is a Vue instance", () => {
    const wrapper = mount(MyTest);
    expect(wrapper).toMatchSnapshot();
  });
});
```

## Motivation

Les applications front construites avec le Starter Kit actuel utilisent [JEST][JEST] pour les tests unitaires. Ce choix a été fait lors de la création de la v2 du Starter Kit dans le but d'avoir un outil de test simple à utiliser et à configurer pour les développeurs.

Vitest est une option intéressante car elle permet d'exécuter les tests unitaires plus rapidement et améliore l'expérience de développement grâce au mode de surveillance par défaut utilisant le rechargement instantané de modules (HMR) de Vite. Vitest offre également une compatibilité avec la plupart des API et des bibliothèques d'écosystème Jest, donc dans la plupart des projets, il devrait être possible de remplacer Jest par Vitest sans difficulté.

La nouvelle structure du projet étant basée sur Vite, Vitest semble être un choix naturel pour les tests unitaires. Cependant, l'utilisation d'un outil de tests d'intégration (Playwrite, Cypress...) en plus de Vitest peut permettre de couvrir un plus large spectre de tests.

## Conception détaillée

Vitest sera utilisé par défaut sur les nouveaux projets pour mettre en place des tests unitaires.

Pour les projets existants, les utilisateurs devront [installer vitest][yarn add -D vitest].
NB : un plugin existe également pour Nuxt : [nuxt-vitest][nuxt-vitest]

Pour utiliser Vitest, les utilisateurs peuvent utiliser la syntaxe et les fonctions Jest existantes, car Vitest offre une compatibilité avec la plupart des API et des bibliothèques d'écosystème Jest. Un guide de migration est disponible [ici][migration-guide].

Il est possible d'utiliser Jest avec Vite : [vite-jest][vite-jest], mais avoir deux pipelines différents à configurer et à maintenir peut être une source de confusion pour les développeurs.

## Désavantages

L'utilisation de Vitest pourrait nécessiter la réécriture des tests existants et une certaine formation pour les développeurs qui ne sont pas familiers avec cette bibliothèque mais cela devrait être minime car la syntaxe est très proche de Jest.

## Alternatives

D'autres alternatives existent comme [Jasmine][Jasmine], [Mocha][Mocha] mais elles ne semblent pas être aussi intéressantes que Vitest.

## Stratégie d'adoption

Ce changement concerne la création de nouveaux projets et les projets existants pourront rester sur JEST ou faire le choix de la migration vers Vitest en fonction de leurs besoins spécifiques.

[Vitest]: https://vitest.dev/
[nuxt-vitest]: https://nuxt.com/modules/vitest
[JEST]: https://jestjs.io/
[migration-guide]: https://vitest.dev/guide/migration.html
[vite-jest]: https://github.com/sodatea/vite-jest
[Jasmine]: https://jasmine.github.io/
[Mocha]: https://mochajs.org/
