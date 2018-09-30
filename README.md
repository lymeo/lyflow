# Lyflow
Lyflow is a gitlab workflow adapted to CI/CD, agile and cloud automation.

## Basic principles

### Three main branches

1. **master**, contains the software's stable releases.
2. **develop**, this branch contains the latest features. It often contains versions of the software that are not yet finished or ready to be released and in agile terms contains the **latest deliverable**
3. **unstable**, this branch contains the latest features but unlike the **develop branch** these features might have broken others and are just generaly waiting for all functional conflicts and adjustements to be added. In extremely rare ocasions changes can be made on this branch directly when feature branches are deemed to be overkill. In agile terms this branch contains the ongoing sprint's user stories.

### Ephemeral branches

1. **feature branches**, named ```feature/[feature name]``` (example: ```feature/logo-animations```) are branches used to add features to the project. They are created from the latest **unstable branch** and are merged (squashed) back into the **unstable branch** when finished. These branches can be deleted when finished but only once the **unstable branch** has been merged into the **develop branch**, often at the end of a cycle.

![feature](https://raw.githubusercontent.com/lymeo/lyflow/master/feature.png)

2. **integration branches**, named ```integration/[cycle name]``` are used to integrate a group of features into the software. They are created from the latest **unstable branch** and are merged (squashed) back into the **unstable branch** when finished. On the **integration branches** minor changes and final adjustements are made so that, once merged, the **unstable branch** is ready to be, in turn, merged (actually rebased) onto the **develop branch**. This branch is deleted after the merge (well the rebase).

![integration](https://raw.githubusercontent.com/lymeo/lyflow/master/integration.png)

3. **release branches**, named ```release/[release name]``` are branches used to package features into a release and prepare them for the release. This branch stems from the **develop branch** where it is squashed back into when finished. It is deleted after being merged.

![release](https://raw.githubusercontent.com/lymeo/lyflow/master/release.png)

### Illustration

![Full illustration](https://raw.githubusercontent.com/lymeo/lyflow/master/full.png)

## Use cases

### ~~Small projects~~
This workflow is not adapted to small projects in the same sense full scrum compliant management is not.

### Scrum and deliverables
> Scrum and agile even though being referenced multiple times in this documentation is not a requirement. 

The **unstable branch** is perfectly adapted to manage the ongoing user stories. Once the sprint is finished all those user stories are added to the **develop branch** using rebase. By rebasing we insure a clean history, on the **developement branch**, containing all the different user stories leading up to the latest deliverable. The latest deliverable is alway's available on the **develop branch** and the latest release on the **master branch**.

### CI/CD

CI/CD is awesome and deserves an adapted workflow. The **unstable branch** acts as a buffer and enables the continuous deployment of the **develop branch**. Continuously deploying the **develop branch** enables you to have a demo, or develop version to be deployed, that you have better control other. Adding to this clean seperation is the possibility to do testing and automation on the **unstable branch**, for example: continuously testing the **unstable branch** and reporting to the developper.

## Credits

This workflow was created and implemented at Lymeo a French IT company. The main contributors being **Cortney Knorr** and **Antoine Murcia**.


