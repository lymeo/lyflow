# Lyflow
Lyflow is a git workflow adapted to CI/CD, agile and cloud automation.

![Full illustration](https://raw.githubusercontent.com/lymeo/lyflow/master/full.png)

## Basic principles

### Three main branches

1. **master**, contains the software's stable releases.
2. **develop**, this branch contains the latest features. It often contains versions of the software that are not yet finished or ready to be released and in agile terms contains the **latest deliverable**.
3. **unstable**, this branch contains the latest features but unlike the **develop branch** these features might have caused malfunctions in other features and are just generaly waiting for all functional conflicts and adjustements to be added. In extremely rare ocasions changes can be made on this branch directly when feature branches are deemed to be overkill. In agile terms this branch contains the ongoing sprint's user stories.

### Ephemeral branches

1. **feature branches**, named ```feature/[feature name]``` (example: ```feature/logo-animations```) are branches used to add features to the project. They are created from the latest **unstable branch** and are merged (squashed) back into the **unstable branch** when finished. These branches can be deleted when finished but only once the **unstable branch** has been merged into the **develop branch**, often at the end of a cycle.

![feature](https://raw.githubusercontent.com/lymeo/lyflow/master/feature.png)

2. **integration branches**, named ```integration/[cycle name]``` are used to integrate a group of features into the software. They are created from the latest **unstable branch** and are merged (squashed) back into the **unstable branch** when finished. On the **integration branches** minor changes and final adjustments are made so that, once merged, the **unstable branch** is ready to be, in turn, merged (actually rebased) onto the **develop branch**. This branch is deleted after the merge (actually the rebase).

![integration](https://raw.githubusercontent.com/lymeo/lyflow/master/integration.png)

3. **release branches**, named ```release/[release name]``` are branches used to package features into a release and prepare them for the release. This branch stems from the **develop branch** into which it is squashed back when finished. This release branch is deleted after being merged into the **unstable branch** to avoid later conflicts between **develop and unstable**.

![release](https://raw.githubusercontent.com/lymeo/lyflow/master/release.png)

### Overview

![Full illustration](https://raw.githubusercontent.com/lymeo/lyflow/master/full.png)

### Hotfix branches

In a similar way to the Gitflow workflow, Lyflow allows Hotfix branches but recommends implementation only when necessary on the **develop and master branch**. 

## Use cases

### ~~Small projects~~
This workflow is not adapted to small projects in the same way full Scrum compliant management is not.

### Scrum and deliverables
> Scrum and agile even though being referenced multiple times in this documentation are not a requirement. 

The **unstable branch** is perfectly adapted to manage the ongoing user stories. Once the sprint is finished all those user stories are added to the **develop branch** using rebase. By rebasing we insure a clean history, on the **develop branch**, containing all the different user stories leading up to the latest deliverable. The latest deliverable is always available on the **develop branch** and the latest release on the **master branch**.

### CI/CD

CI/CD has revolutionised releasing software to end users and deserves an adapted workflow. The **unstable branch** acts as a buffer and enables the continuous deployment of the **develop branch**. Continuously deploying the **develop branch** enables teams to have a deployable demo, or develop version, all the while maintaining better control during the process. Adding to this clean separation is the possibility for testing and automation on the **unstable branch**, for example, continuously testing the **unstable branch** and reporting to the team.

## Credits

This workflow was created and implemented by Lymeo, a French IT company. The main contributors being **Cortney Knorr** and **Antoine Murcia**.


