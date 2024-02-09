- Date de début : 09/02/2024 

- Version majeure cible : SK v2-bridge 

- PR d'implémentation : N/A 

 

 

## Résumé 

 

 

Les projets VueJs actuels sont basés sur la syntaxe de class offerte par la libraire `vue-class-component`. Cependant, cette librairie n'est plus maintenue et une stratégie de migration est nécessaire pour accompagner la migration des projets vers Vue3. 

 

 

## Motivation 

 

 

L'objectif est de Faire le choix entre les deux meilleures stratégies de migrations disponibles, Toutes deux recommandés par la documentation de vue-class-component : 

- Migrer les composants vers la librairie [vue-facing-decorator](https://github.com/facing-dev/vue-facing-decorator) pour conserver des composants sous forme de class. 

- Utiliser l'outils de migration [vue-class-migrator](https://github.com/getyourguide/vue-class-migrator) et passer sur une syntaxe optionAPI native. 

 

 

## Conception détaillée 

 

La documentation de migration vers `vue-facing-decorator` a été rédiger sur cette PR : https://github.com/assurance-maladie-digital/starter-kit-vue-bridge/pull/30. 

La documentation de migration via `vue-class-migrator` a été rédiger sur cette PR : https://github.com/assurance-maladie-digital/starter-kit-vue-bridge/pull/33. 

 

 

### Migration vers `vue-facing-decorator` 

 

 

Migrer vers `vue-facing-decorator` permettrait de continuer d'utiliser une syntaxe sous forme de class similaire a celle de `vue-class-component`. La déclaration des variables, des méthodes et des computeds sont identiques à la manière dont `vue-class-component` et ne nécessiteraient pas de travail de migration. La manière de déclarer les classes, les props, les références vers les éléments du dom, les watchers et les models changes et devrons être manuellement adapté à la syntaxe de `vue-facing-decorator`. 

Voir la documentation de [vue-class-component](https://class-component.vuejs.org/), de [vue-facing-decorator](https://facing-dev.github.io/vue-facing-decorator/#/) et la [PR](https://github.com/assurance-maladie-digital/starter-kit-vue-bridge/pull/30) sur la documentation de la procédure de migration. 

 

 

### Migration via `vue-class-migrator` 

 

Migrer vers l'optionApi via `vue-class-migrator` permettrait d'adopter la syntaxe native de VueJs et de ne plus dépendre de librairies tierces pour la syntaxe des composants. 

L'utilisation de `vue-class-migrator` permettrait d'automatiser une grande partie du travail de changement de syntaxe. Le test d'exécution de ce script effectué sur différents projets a montré des résultats satisfaisants à l'exception de la migration des props déclarés en tant que mixins dans les composants en utilisant le helper 'mixin' de `vue-class-componant`. De plus les composants utilisant des décorateurs personnalisés ne seront pas reconnus par `vue-class-migrator` et causeront l'échec de la migration du composant. Cela à été le cas lors des tests pour les composants Views utilisant un décorateur `@Meta`, il faut alors retirer les décorateurs pour effectuer la migration automatisée. 

 

Voir la documentation de [vue-class-migrator](https://github.com/ThomasKientz/vue-class-migrator/blob/main/README.MD) et la [PR](https://github.com/getyourguide/vue-class-migrator) sur la documentation de la procédure de migration. 

 

 

 

## Désavantages 

 

 

Nous n'avons pas effectué à ce jour de test de migration complet sur un projet. Nous n'avons donc pas retour d'expérience exhaustif sur les deux stratégies de migration. 

 

 

## Stratégie d'adoption 

 

 

Après l'adoption de l'une des deux stratégies de migration, la documentation de migration et les dépendances du StarterKit de migration devrons être mise à jour pour accompagner les équipes dans la migration de leurs projets. 

 

 