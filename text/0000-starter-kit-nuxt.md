- Date de début : 06/10/2022
- Version majeure cible : Design System v3
- PR d'implémentation : N/A

## Résumé

Utilisation de [Nuxt][Nuxt] pour le Starter Kit Vue.

## Motivation

Les applications front construites avec le Starter Kit actuel sont des [Single Page Applications (SPA)][SPA], c'est-à-dire que le rendu de l'application s'effectue côté client, dans le navigateur.
Cela signifie que l'utilisateur doit attendre le téléchargement, le parsing puis l'exécution du code avant de voir et de pouvoir interagir avec l'application.

Nuxt permet d'améliorer les performances de nos applications en effectuant le [rendu côté serveur][SSR], et d'envoyer ainsi une application déjà compilée au navigateur.
De plus, lorsque l'application est téléchargée dans le navigateur, les ressources côté client sont également téléchargées, ce qui permet de rendre l'application interactive à la manière d'une SPA et d'éviter ainsi le rechargement lors de la navigation entre les pages.

Le fait d'envoyer au navigateur une version précompilée de l'application permet également d'améliorer [l'optimisation pour les moteurs de recherche (SEO)][SEO] car les moteurs de recherche n'auront pas à effectuer ce rendu pour indexer les résultats.

## Conception détaillée

Nuxt met également un certain nombre d'outils à disposition afin de simplifier et d'améliorer l'expérience développeur.

<!-- Nuxt Content
File System Routing
useState ou Pinia ?
gestion des erreurs ++
useCookie
$fetch avec ohmyfetch ou axios ?
nuxi
Suspense
Nitro Engine -->

C'est l'essentiel de la RFC. Expliquez la conception avec suffisamment de détails pour qu'une personne familière avec le sujet puisse comprendre. Entrez dans les détails et les cas particuliers, et n'hésitez pas à inclure des exemples d'utilisation de la fonctionnalité. Toute nouvelle terminologie doit être définie dans cette section.

## Désavantages

Le fait d'exécuter le code de l'application côté serveur impose certaines contraintes telles que le fait de gérer le code qui ne fonctionne que dans le navigateur dans des hooks de cycle de vie spécifiques.

Si on considère l'utilisation complète du rendu côté serveur, cela nécessite la gestion d'un serveur afin de répondre aux requêtes, et donc de gérer le déploiement, la charge et la sécurité de celui-ci.

## Alternatives

Il serait possible d'utiliser le module natif [`vue/server-renderer`][Vue SSR] afin de faire le rendu des applications côté serveur, mais cela requiert beaucoup de configuration manuelle, qui est simplifiée avec [l'utilisation de Nuxt][Vue SSR Nuxt], et on ne bénéficierait pas des fonctionnalités supplémentaires apportées par Nuxt.

## Stratégie d'adoption

Ce changement ne concerne que la création de nouveaux projets et n'impacte donc pas les projets existants.

[Nuxt]: https://v3.nuxtjs.org/
[SPA]: https://developer.mozilla.org/fr/docs/Glossary/SPA
[SSR]: https://web.dev/rendering-on-the-web/#server-rendering
[SEO]: https://developer.mozilla.org/fr/docs/Glossary/SEO
[Vue SSR]: https://vuejs.org/guide/scaling-up/ssr.html#rendering-an-app
[Vue SSR Nuxt]: https://vuejs.org/guide/scaling-up/ssr.html#nuxt
