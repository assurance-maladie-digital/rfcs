- Date de début : 30/08/2022
- Version majeure cible : Design System v3
- PR d'implémentation : N/A

## Résumé

Création d'un nouveau dépôt GitHub `starter-kit-vue` pour héberger le Starter Kit Vue.

## Motivation

[Vue CLI][Vue CLI] fournissait un système de presets que nous utilisions avec le dépôt [Vue CLI Preset][Vue CLI Preset].<br>
Ce preset appelait le plugin [Vue CLI Plugin Vue Dash][Vue Dash], qui utilisait l'API mis à disposition par Vue CLI pour générer un nouveau projet.

Vue CLI est passé en mode maintenance uniquement, et la façon recommandée de créer un nouveau projet Vue est d'utiliser [create-vue][create-vue], qui est un outil permettant de créer des projets [Vite][Vite] préconfigurés.

Vite met également à disposition un outil de création de projets, nommé [create-vite][create-vite], mais il ne fournit pas non plus de système équivalent à celui utilisé avec Vue CLI, et l'équipe recommande d'utiliser un outil comme [degit][degit] (qui permet de cloner un dépôt Git sans son historique) afin de créer des templates personnalisés.

[Nuxt][Nuxt] fournit également un [ensemble de templates][nuxt-starter] par leur outil en ligne de commande `nuxi`, et permet d'utiliser un template personnalisé hébergé dans un dépôt GitHub en utilisant l'option `--template`.

## Conception détaillée

Création d'un nouveau dépôt `starter-kit-vue` sur GitHub qui héberge directement le template pour un nouveau projet.<br>
Cela permettra de configurer une CI pour exécuter la qualité, les tests et le build du template pour chacun des commits afin garantir le bon fonctionnement du Starter Kit.

Suppression du système d'options. Les fichiers du template ne seront plus parsés par EJS et seront plus simples à comprendre, et les contributeurs bénéficieront des mêmes fonctionnalités que sur un projet classique car leur environnement de développement sera le même.

Ajout d'une check-list dans le fichier Readme pour documenter les actions que l'utilisateur devra effectuer après la création de son projet pour « nettoyer » le template par défaut.

Le dépôt [Vue CLI Preset][Vue CLI Preset] sera archivé.

## Désavantages

En utilisant un dépôt qui héberge directement le template, on pert le fait de proposer différentes options lors de la création d'un nouveau projet. De ce fait, le Starter Kit sera moins flexible, mais cela permet de réduire le coût de la maintenance, le nombre de tests à effectuer pour s'assurer du bon fonctionnement du Starter Kit et permet d'assurer une meilleure cohérence des applications ainsi que de réduire l'effort cognitif nécessaire pour choisir les différentes options.

La suppression des options oblige également l'utilisateur qui crée un nouveau projet à modifier manuellement le titre et la description de son projet aux différents endroits où ils sont définis. Cependant, cela devrait améliorer les applications car actuellement, ces valeurs sont générées automatiquement et les utilisateurs ne les modifient pas, bien qu'elles ne soient pas forcément adaptées à leur projet.

Puisque le contenu du dépôt sera exactement le même que celui des nouveaux projets, l'utilisateur devra supprimer manuellement la configuration permettant d'exécuter les tests sur la CI, ainsi que modifier le titre de l'application et mettre à jour le Readme.

La procédure à suivre pour « nettoyer » le projet devra être documentée dans une section spécifique du fichier Readme du template, ainsi que dans la documentation associée au Starter Kit.

## Alternatives

Il serait possible de créer notre propre outil en ligne de commande, comme nous l'avions fait avec la [première version de Vue Dash][Vue Dash v1], mais cela implique beaucoup de maintenance et d'efforts, notamment pour supporter les différents systèmes d'exploitation, difficultés qui nous avaient amenés à arrêter la maintenance de cet outil.

Il serait également possible d'utiliser un package comme template en utilisant les commandes [`yarn create`][yarn-create] et [`npm init`][npm-init], ce qui permettrait d'héberger le template dans un package du monorepo comme c'est le cas actuellement. Cette solution implique de publier le Starter Kit régulièrement sur npm et nécessite que l'utilisateur mette à jour le package, là où un repo dédié permet de toujours avoir la dernière version.

## Stratégie d'adoption

Ce changement ne concerne que la création de nouveaux projets et n'impacte donc pas les projets existants.

[Vue CLI]: https://cli.vuejs.org/
[Vue CLI Preset]: https://github.com/assurance-maladie-digital/vue-cli-preset
[Vue Dash]: https://github.com/assurance-maladie-digital/design-system/tree/dev/packages/vue-cli-plugin-vue-dash
[Vue Dash v1]: https://github.com/assurance-maladie-digital/vue-dash
[create-vue]: https://github.com/vuejs/create-vue
[Vite]: https://github.com/vitejs/vite
[create-vite]: https://github.com/vitejs/vite/tree/main/packages/create-vite
[degit]: https://github.com/Rich-Harris/degit
[Nuxt]: https://github.com/nuxt/nuxt.js
[nuxt-starter]: https://github.com/nuxt/starter
[yarn-create]: https://classic.yarnpkg.com/lang/en/docs/cli/create/
[npm-init]: https://docs.npmjs.com/cli/init/
[Create React App]: https://github.com/facebook/create-react-app
