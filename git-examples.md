# GIT Examples

### [#](broken-reference) Contributing Code to PX4 <a href="#contributing-code-to-px4" id="contributing-code-to-px4"></a>

Adding a feature to PX4 follows a defined workflow. In order to share your contributions on PX4, you can follow this example.

* [Sign up (opens new window)](https://github.com/join) for github if you haven't already
* Fork the PX4-Autopilot repo (see [here (opens new window)](https://docs.github.com/en/get-started/quickstart/fork-a-repo))
* Clone your forked repository to your local computer
* Go into the new directory, initialize and update the submodules, and add the original upstream PX4-Autopilot
* You should have now two remote repositories: One repository is called `upstream` that points to PX4/PX4-Autopilot, and one repository `origin` that points to your forked copy of the PX4 repository.
* This can be checked with the following command:
* Make the changes that you want to add to the current main.
*   Create a new branch with a meaningful name that represents your feature

    you can use the command `git branch` to make sure you're on the right branch.
*   Add your changes that you want to be part of the commit by adding the respective files

    If you prefer having a GUI to add your files see [Gitk (opens new window)](https://git-scm.com/book/en/v2/Git-in-Other-Environments-Graphical-Interfaces) or [`git add -p` (opens new window)](http://nuclearsquid.com/writings/git-add/).
*   Commit the added files with a meaningful message explaining your changes

    For a good commit message, please refer to [Contributing](.gitbook/assets/contribute) section.
*   Some time might have passed and the [upstream main (opens new window)](https://github.com/PX4/PX4-Autopilot.git) has changed. PX4 prefers a linear commit history and uses [git rebase (opens new window)](https://git-scm.com/book/en/v2/Git-Branching-Rebasing). To include the newest changes from upstream in your local branch, switch to your main branch

    Then pull the newest commits from upstream main

    Now your local main is up to date. Switch back to your feature branch and rebase on your updated main
* Now you can push your local commits to your forked repository
*   You can verify that the push was successful by going to your forked repository in your browser: `https://github.com/<your git name>/PX4-Autopilot.git`

    There you should see the message that a new branch has been pushed to your forked repository.
* Now it's time to create a pull request (PR). On the right hand side of the "new branch message" (see one step before), you should see a green button saying "Compare & Create Pull Request". Then it should list your changes and you can (must) add a meaningful title (in case of a one commit PR, it's usually the commit message) and message (explain what you did for what reason. Check [other pull requests (opens new window)](https://github.com/PX4/PX4-Autopilot/pulls) for comparison)
* You're done! Responsible members of PX4 will now have a look at your contribution and decide if they want to integrate it. Check if they have questions on your changes every once in a while.

### [#](broken-reference) Changing Source Trees <a href="#changing-source-trees" id="changing-source-trees"></a>

We recommend using PX4 `make` commands to switch between source code branches. This saves you having to remember the commands to update submodules and clean up build artifacts (build files that are not removed will result in "untracked files" errors after the switch).

To switch between branches:

1. Clean up the current branch, de-initializing submodule and removing all build artifacts:
2. Switch to a new branch or tag (here we first fetch the fictional branch "PR\_test\_branch" from the `upstream` remote):
3. Get the submodules for the new branch:

### [#](broken-reference) Get a Specific Release <a href="#get-a-specific-release" id="get-a-specific-release"></a>

Specific PX4 point releases are made as tags of the [release branches](broken-reference), and are named using the format `v<release>`. These are [listed on Github here (opens new window)](https://github.com/PX4/PX4-Autopilot/releases?q=release\&expanded=true) (or you can query all tags using `git tag -l`).

To get the source code for a _specific older release_ (tag):

1.  Clone the PX4-Autopilot repo and navigate into _PX4-Autopilot_ directory:

    Note

    You can reuse an existing repo rather than cloning a new one. In this case clean the build environment (see [changing source trees](broken-reference)):
2. Checkout code for particular tag (e.g. for tag v1.13.0-beta2)
3. Update submodules:

### [#](broken-reference) Get a Release Branch <a href="#get-a-release-branch" id="get-a-release-branch"></a>

Releases branches are branched of `main`, and used to backport necessary changes from main into a release. The branches are named using the format `release/<release_number>` (e.g. `release/v1.13`). The are [listed here (opens new window)](https://github.com/PX4/PX4-Autopilot/branches/all?query=release).

To get a release branch:

*   Clone the PX4-Autopilot repo and navigate into _PX4-Autopilot_ directory:

    Note

    You can reuse an existing repo rather than cloning a new one. In this case clean the build environment (see [changing source trees](broken-reference)):
* Fetch the desired release branch. For example, assuming you want the source for PX4 v1.13:
* Checkout the code for the branch
* Update submodules:

### [#](broken-reference) Update Submodule <a href="#update-submodule" id="update-submodule"></a>

There are several ways to update a submodule. Either you clone the repository or you go in the submodule directory and follow the same procedure as in [Contributing code to PX4](broken-reference).

### [#](broken-reference) Do a PR for a submodule update <a href="#do-a-pr-for-a-submodule-update" id="do-a-pr-for-a-submodule-update"></a>

This is required after you have done a PR for a submodule X repository and the bug-fix / feature-add is in the current main of submodule X. Since the Firmware still points to a commit before your update, a submodule pull request is required such that the submodule used by the Firmware points to the newest commit.

* Make a new branch that describes the fix / feature for the submodule update:
* Go to submodule subdirectory
* PX4 submodule might not necessarily point to the newest commit. Therefore, first checkout main and pull the newest upstream code.
* Go back to Firmware directory, and as usual add, commit and push the changes.

### [#](broken-reference) Checkout pull requests <a href="#checkout-pull-requests" id="checkout-pull-requests"></a>

You can test someone's pull request (changes are not yet merged) even if the branch to merge only exists on the fork from that person. Do the following:

`PR ID` is the number right next to the PR's title (without the #) and the `<branch name>` can also be found right below the `PR ID`, e.g. `<the other persons git name>:<branch name>`. After that you can see the newly created branch locally with

Then switch to that branch

### [#](broken-reference) Common pitfalls <a href="#common-pitfalls" id="common-pitfalls"></a>

#### [#](broken-reference) Force push to forked repository <a href="#force-push-to-forked-repository" id="force-push-to-forked-repository"></a>

After having done the first PR, people from the PX4 community will review your changes. In most cases this means that you have to fix your local branch according to the review. After changing the files locally, the feature branch needs to be rebased again with the most recent upstream/main. However, after the rebase, it is no longer possible to push the feature branch to your forked repository directly, but instead you need to use a force push:

#### [#](broken-reference) Rebase merge conflicts <a href="#rebase-merge-conflicts" id="rebase-merge-conflicts"></a>

If a conflict occurs during a `git rebase`, please refer to [this guide (opens new window)](https://docs.github.com/en/get-started/using-git/resolving-merge-conflicts-after-a-git-rebase).

#### [#](broken-reference) Pull merge conflicts <a href="#pull-merge-conflicts" id="pull-merge-conflicts"></a>

If a conflict occurs during a `git pull`, please refer to [this guide (opens new window)](https://help.github.com/articles/resolving-a-merge-conflict-using-the-command-line/#competing-line-change-merge-conflicts).

#### [#](broken-reference) Build error due to git tags out of date <a href="#build-error-due-to-git-tags-out-of-date" id="build-error-due-to-git-tags-out-of-date"></a>

The build error `Error: PX4 version too low, expected at least vx.x.x` occurs if git tags are out of date.

This can be solved by fetching the upstream repository tags:
