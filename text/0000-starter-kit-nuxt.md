- Date de début : 09/03/2023
- Version majeure cible : Design System v3
- PR d'implémentation : N/A

## Résumé

Utilisation de [Nuxt][Nuxt] pour le Starter Kit Vue.

## Motivation

Les applications front construites avec le Starter Kit actuel sont des [Single Page Applications (SPA)][SPA], c'est-à-dire que le rendu de l'application s'effectue côté client, dans le navigateur.
Cela signifie que l'utilisateur doit attendre le téléchargement, le parsing puis l'exécution du code avant de voir et de pouvoir interagir avec l'application.

Nuxt permet d'améliorer les performances de nos applications en effectuant le [rendu côté serveur][SSR], et d'envoyer ainsi une application déjà compilée au navigateur.
De plus, lorsque l'application est téléchargée dans le navigateur, les ressources côté client sont également téléchargées, ce qui permet de rendre l'application interactive à la manière d'une SPA et d'éviter ainsi le rechargement lors de la navigation entre les pages.

Le fait d'envoyer au navigateur une version pré-compilée de l'application permet également d'améliorer [l'optimisation pour les moteurs de recherche (SEO)][SEO] car les moteurs de recherche n'auront pas à effectuer ce rendu pour indexer les résultats.

## Conception détaillée

Nuxt met un certain nombre d'outils à disposition afin de simplifier et d'améliorer l'expérience développeur tels que [Nuxt Content][Nuxt Content], qui permet de gérer du contenu à la façon d'un CMS en Markdown, une [gestion des erreurs][Nuxt Error Handling] poussée, une [interface en ligne de commande][Nuxi] orientée expérience développeur, des composables tels que [useFetch][Nuxt useFetch] ou [useCookie][Nuxt useCookie], et encore d'autres outils grâce aux [modules communautaires][Nuxt Modules].

## Désavantages

Le fait d'exécuter le code de l'application côté serveur impose certaines contraintes telles que le fait de gérer le code qui ne fonctionne que dans le navigateur dans des hooks de cycle de vie spécifiques.

Si on considère l'utilisation complète du rendu côté serveur, cela nécessite la gestion d'un serveur afin de répondre aux requêtes, et donc de gérer le déploiement, la charge et la sécurité de celui-ci.

## Alternatives

Il serait possible d'utiliser [Astro][Astro] qui est meta-framework axé sur la performance, et dont les fonctionnalités sont similaires à Nuxt comme le rendu côté serveur, la gestion du contenu en Markdown ou la récupération de données côté serveur.<br>
Astro implémente l'architecture Component Islands, où uniquement certains composants d'une page sont interactifs et les ressources JavaScript ne sont chargées que pour ces composants, ce qui réduit considérablement la taille des applications.

Cependant, Astro a sa propre syntaxe de composants, différente de celle de Vue.js, ce qui peut être difficile à appréhender et à maintenir, en particulier pour les développeurs novices, là où Nuxt a pour philosophie principale de simplifier au maximum son utilisation en se concentrant sur l'expérience développeur.

Il serait également possible d'utiliser le module natif [`vue/server-renderer`][Vue SSR] afin de faire le rendu des applications côté serveur, mais cela requiert beaucoup de configuration manuelle, qui est simplifiée avec [l'utilisation de Nuxt][Vue SSR Nuxt], et on ne bénéficierait pas des fonctionnalités supplémentaires apportées par Nuxt.

## Stratégie d'adoption

Ce changement ne concerne que la création de nouveaux projets et n'impacte donc pas les projets existants.

[Nuxt]: https://v3.nuxtjs.org/
[SPA]: https://developer.mozilla.org/fr/docs/Glossary/SPA
[SSR]: https://web.dev/rendering-on-the-web/#server-rendering
[SEO]: https://developer.mozilla.org/fr/docs/Glossary/SEO
[Vue SSR]: https://vuejs.org/guide/scaling-up/ssr.html#rendering-an-app
[Vue SSR Nuxt]: https://vuejs.org/guide/scaling-up/ssr.html#nuxt
[Nuxt Content]: https://content.nuxtjs.org/
[Nuxt Modules]: https://nuxt.com/modules
[Nuxt Error Handling]: https://nuxt.com/docs/getting-started/error-handling
[Nuxi]: https://nuxt.com/docs/api/commands/add
[Nuxt useFetch]: https://nuxt.com/docs/api/composables/use-fetch
[Nuxt useCookie]: https://nuxt.com/docs/api/composables/use-cookie
[Astro]: https://astro.build/
