# Contributing to Documentation

Contributions to the PX4 User Guide are very welcome; from simple fixes to spelling and grammar, through to the creation of whole new sections.

This topic explains how to make and test changes. Towards the end there is a basic style guide.

### [#](broken-reference) Quick Changes in Github <a href="#quick-changes-in-github" id="quick-changes-in-github"></a>

Simple changes to _existing content_ can be made by clicking the **Edit this page on GitHub** link that appears at the bottom of every page (this opens the page on Github for editing).

To edit an existing page:

1. Open the page.
2. Click the **Edit this page on GitHub** link below the page content.
3. Make the desired change.
4. Below the Github page editor you'll be prompted to create a separate branch and then guided to submit a _pull request_.

The documentation team will review the request and either merge it or work with you to update it.

### [#](broken-reference) Changes using Git (New Pages and Images) <a href="#changes-using-git-new-pages-and-images" id="changes-using-git-new-pages-and-images"></a>

More substantial changes, including adding new pages or adding/modifying images, aren't as easy to make (or properly test) on Github. For these kinds of changes we suggest using the same approach as for _code_:

1. Use the _git_ toolchain to get the documentation source code onto your local computer.
2. Modify the documentation as needed (add, change, delete).
3. _Test_ that it builds properly using Vuepress.
4. Create a branch for your changes and create a pull request (PR) to pull it back into the documentation.

The following explain how to get the source code, build locally (to test), and modify the code.

#### [#](broken-reference) Get/Push Documentation Source Code <a href="#get-push-documentation-source-code" id="get-push-documentation-source-code"></a>

To get the library(s) sources onto your local computer you will need to use the git toolchain. The instructions below explain how to get git and use it on your local computer.

1. Download git for your computer from [https://git-scm.com/downloads (opens new window)](https://git-scm.com/downloads)
2. [Sign up (opens new window)](https://github.com/join) for Github if you haven't already
3. Create a copy (Fork) of the [PX4 User Guide repo (opens new window)](https://github.com/PX4/PX4-user\_guide) on Github ([instructions here (opens new window)](https://docs.github.com/en/get-started/quickstart/fork-a-repo)).
4.  Clone (copy) your forked repository to your local computer:

    For example, to clone the PX4 userguide fork for a user with Github account "john\_citizen":
5. Navigate to your local repository:
6.  Add a _remote_ called "upstream" to point to the PX4 version of the library:

    TIP

    A "remote" is a handle to a particular repository. The remote named _origin_ is created by default when you clone the repository, and points to _your fork_ of the guide. Above you create a new remote _upstream_ that points to the PX4 project version of the documents.
7.  Create a branch for your changes:

    This creates a local branch on your computer named `your_feature_branch_name`.
8. Make changes to the documentation as needed (general guidance on this in following sections)
9.  Once you are satisfied with your changes, you can add them to your local branch using a "commit":

    For a good commit message, please refer to [Contributing](.gitbook/assets/contribute) section.
10. Push your local branch (including commits added to it) to your forked repository on Github.
11. Go to your forked repository on Github in a web browser, e.g.: `https://github.com/<your git name>/PX4-user_guide.git`. There you should see the message that a new branch has been pushed to your forked repository.
12. Create a pull request (PR):
    * On the right hand side of the "new branch message" (see one step before), you should see a green button saying "Compare & Create Pull Request". Press it.
    * A pull request template will be created. It will list your commits and you can (must) add a meaningful title (in case of a one commit PR, it's usually the commit message) and message (explain what you did for what reason. Check [other pull requests (opens new window)](https://github.com/PX4/PX4-user\_guide/pulls) for comparison)
13. You're done! Maintainers for the PX4 User Guide will now have a look at your contribution and decide if they want to integrate it. Check if they have questions on your changes every once in a while.

#### [#](broken-reference) Building the Library Locally <a href="#building-the-library-locally" id="building-the-library-locally"></a>

Build the library locally to test that any changes you have made have rendered properly:

1. Install the [Vuepress prerequiresites (opens new window)](https://vuepress.vuejs.org/guide/getting-started.html#prerequisites):
   *   [Nodejs 10+ (opens new window)](https://nodejs.org/en)

       Note

       For recent nodejs versions (after v16.15.0) you need to enable the node legacy OpenSSL provider. On Ubuntu you can do this by running the terminal command:
   * [Yarn classic (opens new window)](https://classic.yarnpkg.com/en/docs/install)
2. Navigate to your local repository:
3. Install dependencies (including Vuepress):
4. Preview and serve the library:
   * Now you can browse the guide on http://localhost:8080/px4\_user\_guide/
   * Stop serving using **CTRL+C** in the terminal prompt.
5. Build the library using:

TIP

Use `yarn docs:dev` to preview changes _as you make them_ (documents are updated and served very quickly). Before submitting a PR you should also build it using `docs:build`, as this can highlight issues that are not visible when using `docs:dev`.

#### [#](broken-reference) Source Code Structure <a href="#source-code-structure" id="source-code-structure"></a>

The guide uses the [Vuepress (opens new window)](https://vuepress.vuejs.org/) toolchain. The PX4 User Guide has some minor differences, mostly related to configuration and setup.

In overview:

* Pages are written in separate files using markdown.
  * The syntax is almost the same as that used by the Github wiki.
  * Vuepress also supports some [markdown extensions (opens new window)](https://vuepress.vuejs.org/guide/markdown.html). We try and avoid using these, except for [tips, warning, etc. (opens new window)](https://vuepress.vuejs.org/guide/markdown.html#custom-containers).
* This is a [multilingual (opens new window)](https://vuepress.vuejs.org/guide/i18n.html#default-theme-i18n-config) book:
  * Pages for each language are stored in the folder named for the associated language code (e.g. "zh" for Chinese, "ko" for Korean).
  * Only edit the ENGLISH (**/en**) version of files. We use [Crowdin](broken-reference) to manage the translations.
* All pages must be in an appropriately named sub-folder of **/en** (e.g. this page is in folder **en/contribute/**).
  * This makes linking easier because other pages and images are always as the same relative levels
* The _structure_ of the book is defined in **SUMMARY.md**
  * If you add a new page to the guide you must also add an entry to this file!
* Images must be stored in a sub folder of **/assets**. This is two folders down from content folders, so if you add an image you will reference it like:
* A file named **package.json** defines any dependencies of the build.
* A web hook is used to track whenever files are merged into the master branch on this repository, causing the book to rebuild.

#### [#](broken-reference) Adding New Pages <a href="#adding-new-pages" id="adding-new-pages"></a>

When you add a new page you must also add it to **en/SUMMARY.md**!

### [#](broken-reference) Style Guide <a href="#style-guide" id="style-guide"></a>

1. Files/file names
   * Put new files in an appropriate sub-folder of **/en/**. Do not further nest folders.
   * Use descriptive names. In particular, image filenames should describe what they contain.
   * Use lower case filenames and separate words using underscores "\_"
2. Images
   * Use the smallest size and lowest resolution that makes the image still useful (this reduces download cost for users with poor bandwidth).
   * New images should be created in a sub-folder of **/assets/** by default (so they can be shared between translations).
3. Content:
   * Use "style" (bold, emphasis, etc) consistently.
     * **Bold** for button presses and menu definitions.
     * _Emphasis_ for tool names.
     * Otherwise use as little as possible.
   * Headings and page titles should use "First Letter Capitalisation"
   * The page title should be a first level heading (#). All other headings should be h2 (##) or lower.
   * Don't add any style to headings.
   * Don't translate the _first part_ of a note, tip or warning declaration (e.g. `::: tip`) as this precise text is required to render the note properly.

### [#](broken-reference) Where Do I Add Changes? <a href="#where-do-i-add-changes" id="where-do-i-add-changes"></a>

Add new documentation in-line with the existing structure!

Some of the main categories are:

* Development: content related to:
  * Evolving the platform (new modes, modules, flight modes, hardware, software and hardware architecture and porting).
  * "Experimental" work that requires developer expertise to reproduce.
* Flying: content related to flying a standard vehicle (flight modes, arming, taking off, landing)
* Basic configuration: Configuration that every vehicle will need to do
* Advanced configuration: Configuration that is specific to a vehicle type, or some segment of users.
* Peripherals: Documentation on different hardware that can be used.
  * This also includes setup and configuration information for hardware that isn't covered in Basic configuration.
* Basic Assembly: Assembly of an autopilot and its main peripherals
* Airframe Builds: Examples of how to build a whole system.

### [#](broken-reference) Translations <a href="#translations" id="translations"></a>

For information about translation see: [Translation](broken-reference).

### [#](broken-reference) Licence <a href="#licence" id="licence"></a>

All PX4/Dronecode documentation is free to use and modify under terms of the permissive [CC BY 4.0 (opens new window)](https://creativecommons.org/licenses/by/4.0/) licence.

Last Updated: 9/13/2023, 2:00:12 AM
