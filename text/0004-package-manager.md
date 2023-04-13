- Date de début : 28/03/2023
- Version majeure cible : v3
- PR d'implémentation : N/A

## Résumé

Utilisation de [pnpm] comme gestionnaire de paquets à la place de [Yarn].

## Motivation

Actuellement nous utilisons [Yarn Classic], qui est en mode maintenance depuis janvier 2020. Yarn 2 a introduit un nouveau mode de fonctionnement appelé Plug'n'Play, qui change complètement la philosophie de Yarn, au point que celui-ci est considéré comme un gestionnaire de paquets différent, avec également un [système de configuration différent][yarn config].

En parallèle, [pnpm] a commencé à gagner en popularité et à un mode de fonctionnement qui reste proche de celui de [npm].

De plus, pnpm est plus performant et plus efficace au niveau de l'espace disque que [Yarn] comme le montre leur [benchmark][pnpm benchmark]. Il intègre également le support des monorepos comme le Design System via les [workspaces][pnpm workspaces].

## Conception détaillée

Les utilisateurs devront [installer pnpm][pnpm install] avant de créer un nouveau projet.

Si un utilisateur souhaite migrer un projet existant, il devra supprimer le répertoire `node_modules` de son projet ainsi que le fichier `yarn.lock`, puis exécuter la commande `pnpm install` et commiter le résultat.

Pour le Design System, l'installation des dépendances avec du cache passe de ~150s avec Yarn classique à ~50s avec pnpm.
Il sera également possible d'utiliser le [hook `devPreinstall`](https://pnpm.io/fr/scripts#pnpmdevpreinstall) afin de simplifier la configuration de l'environnement de développement à l'installation du projet.

## Désavantages

Le fait de modifier le gestionnaire de paquets utilisé nécessitera que les utilisateurs installent et se familiarisent avec un nouvel outil, même si pnpm a une interface en ligne de commande quasiment identique à celle de Yarn.

Les workflows de déploiement devront également être adaptés, mais l'arrivée de la v3 du Design System devrait coïncider avec l'arrivée de la nouvelle plateforme, et les modifications à faire sur la version actuelle de celle-ci consistent principalement en des modifications de commandes.

## Alternatives

Il serait possible d'utiliser [npm], qui a l'avantage d'être intégré directement lors de l'installation de [node.js], cependant on ne bénéficierait pas des améliorations de performances et d'efficacité de pnpm, et l'interface en ligne de commande est différente de celle utilisée actuellement.

## Stratégie d'adoption

Ce changement ne concerne que la création de nouveaux projets et n'impacte donc pas les projets existants qui pourront rester sur [Yarn Classic] ou faire le choix de la migration.

[pnpm]: https://pnpm.io/fr/
[pnpm benchmark]: https://pnpm.io/benchmarks
[pnpm workspaces]: https://pnpm.io/fr/workspaces
[pnpm install]: https://pnpm.io/fr/installation
[Yarn Classic]: https://classic.yarnpkg.com/lang/en/
[Yarn]: https://yarnpkg.com/
[yarn config]: https://yarnpkg.com/configuration/yarnrc
[npm]: https://docs.npmjs.com/
[node.js]: https://nodejs.org/fr
