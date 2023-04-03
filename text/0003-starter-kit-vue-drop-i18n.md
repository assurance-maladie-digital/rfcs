- Date de début : 22/03/2023
- Version majeure cible : v3
- PR d'implémentation : N/A

## Résumé

Suppression de [Vue i18n][Vue i18n] dans le Starter Kit Vue.

## Motivation

Les applications front construites avec le Starter Kit actuel utilisent [Vue i18n][Vue i18n] pour extraire les textes des composants. Ce choix a été fait lors de la création de la v2 du Starter Kit dans le but de simplifier la modification des textes ainsi que la lecture du template.

Après plus de 3 ans depuis la création du Starter Kit et l'utilisation de ce système dans un certain nombre de projets, il est apparu que le coup de la maintenance est supérieure à ce qui avait été prévu, et que l'utilisation de [Vue i18n][Vue i18n] rend plus complexe l'écriture et la modification des templates, sans réellement simplifier la modification des textes, voir même en la complexifiant lorsque les textes doivent être formatés.

De plus, seul un très faible pourcentage des applications construites avec le Starter Kit utilisent le système de traduction pour gérer plusieurs langues, ce qui implique d'ajouter du poids inutile à la plupart des applications.

À noter également que dans le cas de pages de texte longues comme les Conditions Générales d'Utilisation, les textes sont déjà intégrés dans le template de composants de "contenu" afin de simplifier leur édition.

## Conception détaillée

Les textes seront maintenant écrits directement dans les templates, sans passer par des fichiers traductions et Vue i18n et la structure de dossiers suivante ne sera plus présente :

```
translations/
├── components/
│   ├── layout/
│   └── index.ts
├── views/
│   ├── about.ts
│   ├── home.ts
│   ├── index.ts
│   ├── maintenance.ts
│   └── notFound.ts
├── common.ts
└── index.ts
```

## Désavantages

Le fait de modifier le fonctionnement de la gestion des textes et la structure de l'application peut demander un certain temps d'adaptation, mais la nouvelle version du Starter Kit est une version majeure qui comprends déjà des changements importants qu demanderons une adaptation.

## Alternatives

Il serait possible d'utiliser un CMS pour gérer les textes, mais cela nécessite un ajout d'offre et une décision collective.

Puisque l'utilisation de Nuxt a été actée dans la RFC [Starter Kit Nuxt][Starter Kit Nuxt], il est possible d'utiliser [Nuxt Content][Nuxt Content] en complément pour rédiger les pages de textes longues comme les Conditions Générales d'Utilisation puisque ce module permet de gérer du contenu à la façon d'un CMS en Markdown.

## Stratégie d'adoption

Ce changement ne concerne que la création de nouveaux projets et n'impacte donc pas les projets existants.

[Vue i18n]: https://kazupon.github.io/vue-i18n/
[Starter Kit Nuxt]: 0002-starter-kit-nuxt.md
[Nuxt Content]: https://content.nuxtjs.org/
