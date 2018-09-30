# Lyflow
Lyflow est un workflow git adapté aux Chaînes d'Intégration/Chaînes de Déploiement, à la méthodoligie agile et l'automatisation cloud.

## Principes de base

### Trois branches principales

1. **master**, qui contient les "releases" stables du software.
2. **develop**, qui contient les dernières fonctionnalitées. Elle dispose souvent de versions du software qui ne sont pas encore terminées ou prêtes à être envoyé sur master. En termes agile elle contient **le dernier deliverable**
3. **unstable**, cette branche contient les dernières fonctionnalitées mais contrairement à la **branche develop** ces fonctionnalités peuvent avoir créé des conflits avec d'autres fonctionnalitées et sont en attente d'un correctif. Dans de rare cas certains changements peuvent être appliqués directement sur cette branche lorsque la création d'une branche "feature" est considéré comme de l'overkill. En termes agile cette branche contient les **user stories du sprint en cours.**

### Branches éphémères

1. **Les branches feature**, nommées ```feature/[nom de la feature]``` (example: ```feature/logo-animations```) sont des branches utilisées pour ajouter des fonctionnalitées au projet. Elle sont créées à partir de la dernière **branche unstable** et sont fusionnées (merge squash) à la **branche unstable** une fois terminées. Ces branches peuvent être supprimées une fois finies mais seulement une fois que la **branche unstable** a été fusionné à la **branche develop**, souvent à la fin d'un cycle.

![feature](https://raw.githubusercontent.com/lymeo/lyflow/master/feature.png)

2. **Les branches integration**, nommées ```integration/[nom du cycle]``` sont utilisées pour intégrer un groupe de fonctionnalitées dans le software. Elles sont créées à partir de la dernière **branche unstable** et sont fusionnées (merge squash) à la **branche unstable** une fois terminées. Dans les **branches integration**  des changements mineurs et des ajustements finaux sont faits pour, qu'une fois fusionnée, la **branche unstable** est prête, à terme, à être fusionnée (ou plutôt "rebase") avec la **branche develop**. Cette branche est supprimée apès la fusion (le "rebase").

![integration](https://raw.githubusercontent.com/lymeo/lyflow/master/integration.png)

3. **les branches release**, nommées ```release/[nom de la release]``` sont des branches utilisées pour grouper un ensemble de fonctionnalités en une "release". Cette branche est issue de la **branche develop** dans laquelle elle est fusionnée (merge squash) une fois terminée, après quoi elle sera supprimée.

![release](https://raw.githubusercontent.com/lymeo/lyflow/master/release.png)

### Illustration

![Full illustration](https://raw.githubusercontent.com/lymeo/lyflow/master/full.png)

## Cas d'usage

### ~~Petits projets~~
Ce workflow n'est pas adapté aux petits projets tout comme une gestion de conformitée "full scrum management" ne l'est pas.

### Scrum et deliverables
> Les méthodes "Scrum" et "agile", même étant citées plusieurs fois dans cette documentation, ne sont pas requises. 

La **branche unstable** est parfaitement adaptée à la gestion de "user stories" en cours. Une fois le sprint terminé toutes ces "user stories" sont ajoutées à la **branche develop** via "rebase". En utilisant "rebase" on s'assure un historique propre sur la **branche develop** contenant les différentes "user stories" menants au dernier "deliverable". Le dernier "deliverable" est toujours disponible sur la **branche develop** et la dernière "release" sur la  **branche master**.

### CI/CD

Les CI/CD sont géniales et mérites un workflow adapté. La **branche unstable** agit en tant que buffer et permet le déploiement continu de la **branche develop**. Déployer de manière continue la **branche develop** vous permet d'avoir une démo, ou une version "develop" déployable, sur laquelle vous avez un meilleur contrôle. Ajoutez à cela une séparation propre et vous avez la possibilitée de faire du testing et de automatisation sur la **branche unstable**. Par example vous pouvez tester continuellement la **branche unstable** et faire des rapports aux developpers.

## Crédits

Ce workflow a été créé et implementé par Lymeo une entreprise informatique française. Les contributeurs principaux étants **Cortney Knorr** et **Antoine Murcia**.


