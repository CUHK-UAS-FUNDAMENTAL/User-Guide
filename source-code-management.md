# Source Code Management

### [#](broken-reference) Branching Model <a href="#branching-model" id="branching-model"></a>

The PX4 project uses a three-branch Git branching model:

* [main (opens new window)](https://github.com/PX4/PX4-Autopilot/tree/main) is by default unstable and sees rapid development.
* [beta (opens new window)](https://github.com/PX4/PX4-Autopilot/tree/beta) has been thoroughly tested. It's intended for flight testers.
* [stable (opens new window)](https://github.com/PX4/PX4-Autopilot/tree/stable) points to the last release.

We try to retain a [linear history through rebases (opens new window)](https://www.atlassian.com/git/tutorials/rewriting-history) and avoid the [Github flow (opens new window)](https://docs.github.com/en/get-started/quickstart/github-flow). However, due to the global team and fast moving development we might resort to merges at times.

To contribute new functionality, [sign up for Github (opens new window)](https://docs.github.com/en/get-started/signing-up-for-github/signing-up-for-a-new-github-account), then [fork (opens new window)](https://docs.github.com/en/get-started/quickstart/fork-a-repo) the repository, [create a new branch (opens new window)](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-and-deleting-branches-within-your-repository), add your [changes as commits](broken-reference), and finally [send a pull request](broken-reference). Changes will be merged when they pass our [continuous integration (opens new window)](https://en.wikipedia.org/wiki/Continuous\_integration) tests.

All code contributions have to be under the permissive [BSD 3-clause license (opens new window)](https://opensource.org/licenses/BSD-3-Clause) and all code must not impose any further constraints on the use.

### [#](broken-reference) Code Style <a href="#code-style" id="code-style"></a>

PX4 uses the [Google C++ style guide (opens new window)](https://google.github.io/styleguide/cppguide.html), with the following (minimal) modifications:

Note

Not all PX4 source code matches the style guide, but any _new code_ that you write should do so — in both new and existing files. If you update an existing file you are not required to make the whole file comply with the style guide, just the code you've modified.

#### [#](broken-reference) Tabs <a href="#tabs" id="tabs"></a>

* Tabs are used for indentation (equivalent to 8 spaces).
* Spaces are used for alignment.

#### [#](broken-reference) Line Length <a href="#line-length" id="line-length"></a>

* Maximum line length is 120 characters.

#### [#](broken-reference) File Extensions <a href="#file-extensions" id="file-extensions"></a>

* Source files use extension `*.cpp` instead of `*.cc`.

#### [#](broken-reference) Function and Method Names <a href="#function-and-method-names" id="function-and-method-names"></a>

* `lowerCamelCase()` is used for functions and methods to _visually_ distinguish them from `ClassConstructors()` and `ClassNames`.

#### [#](broken-reference) Class Privacy Keywords <a href="#class-privacy-keywords" id="class-privacy-keywords"></a>

* _zero_ spaces before `public:`, `private:`, or `protected:` keywords.

#### [#](broken-reference) Example Code Snippet <a href="#example-code-snippet" id="example-code-snippet"></a>

### [#](broken-reference) In-Source Documentation <a href="#in-source-documentation" id="in-source-documentation"></a>

PX4 developers are encouraged to create appropriate in-source documentation.

Note

Source-code documentation standards are not enforced, and the code is currently inconsistently documented. We'd like to do better!

Currently we have two types of source-based documentation:

* `PRINT_MODULE_*` methods are used for both module run time usage instructions and for the Modules & Commands Reference in this guide.
  * The API is documented [in the source code here (opens new window)](https://github.com/PX4/PX4-Autopilot/blob/v1.8.0/src/platforms/px4\_module.h#L381).
  * Good examples of usage include the Application/Module Template and the files linked from the modules reference.
*   We encourage other in-source documentation _where it adds value/is not redundant_.

    TIP

    Developers should name C++ entities (classes, functions, variables etc.) such that their purpose can be inferred - reducing the need for explicit documentation.

    * Do not add documentation that can trivially be inferred from C++ entity names.
    * ALWAYS specify units of variables, constants, and input/return parameters where they are defined.
    * Commonly you may want to add information about corner cases and error handling.
    * [Doxgyen (opens new window)](http://www.doxygen.nl/) tags should be used if documentation is needed: `@class`, `@file`, `@param`, `@return`, `@brief`, `@var`, `@see`, `@note`. A good example of usage is [src/modules/events/send\_event.h (opens new window)](https://github.com/PX4/PX4-Autopilot/blob/main/src/modules/events/send\_event.h).

Please avoid "magic numbers", for example, where does this number in the conditional come from? What about the multiplier on yaw stick input?

Instead, define the numbers as named constants with appropriate context in the header:

and update the source implementation.

### [#](broken-reference) Commits and Commit Messages <a href="#commits-and-commit-messages" id="commits-and-commit-messages"></a>

Please use descriptive, multi-paragraph commit messages for all non-trivial changes. Structure them well so they make sense in the one-line summary but also provide full detail.

**Use `git commit -s` to sign off on all of your commits.** This will add `signed-off-by:` with your name and email as the last line.

This commit guide is based on best practices for the Linux Kernel and other [projects maintained (opens new window)](https://github.com/torvalds/subsurface-for-dirk/blob/a48494d2fbed58c751e9b7e8fbff88582f9b2d02/README#L88-L115) by Linus Torvalds.

### [#](broken-reference) Pull Requests <a href="#pull-requests" id="pull-requests"></a>

Github [Pull Requests (PRs) (opens new window)](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) are the primary mechanism used to submit new functionality and bug fixes to PX4.

They include the new set of [commits](broken-reference) in your branch (relative the main branch), and a description of the changes.

The description should include:

* An overview of what the changes deliver; enough to understand the broad purpose of the code
* Links to related issues or supporting information.
* Information about what testing of the PR funcitonality has been done, with links to flight logs.
* Where possible, the results from general Test Flights both before and after the change.

Last Updated: 8/30/2023, 7:21:34 AM
