# RFCs du Digital de l'Assurance Maladie

Propositions de modifications pour nos projets publics.

[Liste des RFCs actives](https://github.com/assurance-maladie-digital/rfcs/tree/main/text)

## Qu'est-ce qu'une RFC ?

Une RFC est un document qui fait partie d'une série numérotée décrivant les modifications sur nos projets publics de manière cohérente et contrôlée.

## Quand suivre ce processus

La plupart des modifications, comme les corrections de bugs, les améliorations de la documentation et les fonctionnalités simples peuvent suivre le système de Pull Request classique.

Cependant, certains changements sont « substantiels », et doivent être soumis à un processus de conception et doivent faire consensus entre l'équipe principale et la communauté.

## Processus

1. Forker le dépôt <https://github.com/assurance-maladie-digital/rfcs>
2. Copier le fichier `0000-template.md` dans `text/0000-my-feature.md` (ne pas assigner de numéro pour le moment)
3. Compléter le template de la RFC
4. Soumettre une Pull Request
5. Retravailler la RFC en intégrant les différents commentaires afin d'arriver à consensus
6. Revue de l'équipe principale
7. Période finale de commentaires de 3 jours ouvrés, indiquée par un commentaire sur la Pull Request
8. Acceptation ou refus de la RFC :
   - Une RFC peut être rejetée par l'équipe une fois que les discussions publiques ont été résolues et que des commentaires ont été faits résumant la raison du rejet. Un membre de l'équipe doit ensuite fermer la Pull Request associée.
   - Une RFC peut être acceptée à la fin de sa période finale de commentaires. Un membre de l'équipe acceptera la Pull Request associée, auquel cas la RFC deviendra « active ».

## Cycle de vie d'une RFC

Une fois qu'une RFC devient active, les auteurs peuvent commencer à planifier la modification. Une RFC active ne signifie pas toujours l'implémentation de la modification, mais cela signifie que l'équipe l'a acceptée en principe et est favorable à cette modification.

De plus, le fait qu'une RFC soit acceptée et « active » n'implique rien sur la priorité qui est attribuée à son implémentation, y compris sur le fait que quelqu'un travaille dessus.

Les modifications des RFCs actives peuvent être effectuées dans les Pull Requests de suivi. Nous nous efforçons de présenter chaque RFC dans un état final, mais en raison de la nature du processus, des modifications peuvent être nécessaires lors de l'implémentation. Dans ce cas, les modifications seront apportées aux RFCs.

## Implémentation d'une RFC

L'auteur d'une RFC n'est pas obligé de l'implémenter. Cependant, l'auteur de la RFC, comme tout autre personne, peut publier une implémentation pour examen après l'acceptation de la RFC.

Lors de l'implémentation d'une RFC, les auteurs doivent publier le lien de celle-ci sur le RFC.

Si vous souhaitez travailler sur l'implémentation d'une RFC « active », mais que vous ne savez pas si quelqu'un travaille déjà dessus, n'hésitez pas à laisser un commentaire sur la Pull Request de la RFC.

## Revue des RFCs

Les membres de l'équipe principale essayeront de passer en revue régulièrement les propositions de RFC. Si un membre de l'équipe principale pense qu'une RFC est prête à être acceptée et à passer au statut « active », il peut approuver la Pull Request.

## Inspiration

Notre processus RFC est inspiré des processus RFC de [Vue][Vue RFC], [React][React RFC], [Rust][Rust RFC] et [Ember][Ember RFC].

[Vue RFC]: https://github.com/vuejs/rfcs
[React RFC]: https://github.com/reactjs/rfcs
[Rust RFC]: https://github.com/rust-lang/rfcs
[Ember RFC]: https://github.com/emberjs/rfcs
