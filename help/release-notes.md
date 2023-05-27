April 2023 (version 1.78)
=========================

Show release notes after an update

**Update 1.78.1**: The update addresses this security [issue](https://github.com/microsoft/vscode/issues?q=is%3Aissue+milestone%3A%22April+2023+Recovery+1%22+is%3Aclosed "https://github.com/microsoft/vscode/issues?q=is%3Aissue+milestone%3A%22April+2023+Recovery+1%22+is%3Aclosed").

**Update 1.78.2**: The update addresses these [issues](https://github.com/microsoft/vscode/issues?q=is%3Aissue+milestone%3A%22April+2023+Recovery+2%22+is%3Aclosed "https://github.com/microsoft/vscode/issues?q=is%3Aissue+milestone%3A%22April+2023+Recovery+2%22+is%3Aclosed").

* * *

Welcome to the April 2023 release of Visual Studio Code. There are many updates in this version that we hope you'll like, some of the key highlights include:

*   **[Accessibility improvements](#accessibility "#accessibility")** - Better screen reader support, new audio cues.
*   **[New color themes](#new-default-color-themes "#new-default-color-themes")** - "Modern" light and dark color theme defaults.
*   **[Profile templates](#profile-templates "#profile-templates")** - Built-in templates for Python, Java, Data Science, and more.
*   **[Drag and drop selector](#drop-selector "#drop-selector")** - Choose how you'd like item links placed into the editor.
*   **[Standalone color picker](#standalone-color-picker "#standalone-color-picker")** - Color picker UI to insert or modify color formats.
*   **[Quick Fixes for Source Control input](#source-control "#source-control")** - Fix spelling and other errors right in the input box.
*   **[Markdown drag and drop videos](#drag-and-drop-videos-into-markdown-files "#drag-and-drop-videos-into-markdown-files")** - Easily add video tags in Markdown files.
*   **[Notebooks insert images as attachments](#drop-image-files-into-notebooks-to-create-attachments "#drop-image-files-into-notebooks-to-create-attachments")** - Choose between an image link, path, or attachment.
*   **[Git LFS and VS Code for the Web](#commit-files-to-git-large-file-storage "#commit-files-to-git-large-file-storage")** - Use vscode.dev for repos with Git Large File Storage.
*   **[VS Code Day 2023](#vs-code-day "#vs-code-day")** - Catch up on the sessions in the YouTube playlist.

> If you'd like to read these release notes online, go to [Updates](https://code.visualstudio.com/updates "https://code.visualstudio.com/updates") on [code.visualstudio.com](https://code.visualstudio.com "https://code.visualstudio.com").

**Insiders:** Want to try new features as soon as possible? You can download the nightly [Insiders](https://code.visualstudio.com/insiders "https://code.visualstudio.com/insiders") build and try the latest updates as soon as they are available.

Accessibility
-------------

### Aria verbosity settings

Screen reader users can exclude hints from a feature's `aria-label` to decrease redundancy via the `"accessibility.verbosity.diff-editor"` and `"accessibility.verbosity.terminal"` settings.

### Improved and aligned Quick Pick experience

Previously, users of accessibility mode experienced different behavior when working with the Command Palette and other Quick Picks. In accessibility mode, the first item of the Quick Pick wasn't selected in order to be fully accessible. This iteration, we've introduced new behavior that allows you to have the best of both worlds: an accessible **and** fast Quick Pick workflow allowing you to hit `Enter` right away.

> **Note**: One tradeoff with this approach is that if an item in the Quick Pick is selected, you are not able to hear ARIA changes to the Quick Pick input box, due to an ARIA limitation. To hear these changes, you can press `unassigned` until no item of the list is selected.

### Terminal

#### Terminal accessible buffer improvements

*   Jump between commands using `Ctrl+DownArrow` and `Ctrl+UpArrow`.
*   Use **Set Selection Anchor**, **Select from Anchor to Cursor**, and page navigation via `Shift+PageUp` and `Shift+PageDown`.
*   Preview the position when using **Terminal: Navigate Accessible Buffer** (`Ctrl+Shift+O`) before accepting a command to go to a new location.
*   Engage with the output while dynamic updates occur.

#### Terminal Accessibility Help menu

The terminal's **Accessibility Help** menu can now be navigated using arrow keys.

Sorry, your browser doesn't support HTML 5 video.

### Diff editor audio cue improvements

VS Code now caches audio cues so they only have to be loaded once, yielding better responsiveness, and have improved the tones used for the diff editor.

### Go to Line/Column announcement

When **Go to Line/Column...** (`Ctrl+G`) is invoked, the screen reader now reads the associated line content.

Workbench
---------

### New default Color Themes

New 'Dark Modern' and 'Light Modern' themes replace 'Dark+' and 'Light+' as the new default dark and light color themes.

![Dark Modern and Light Modern color themes](images/1_78/dark-light-modern-themes.png)

### Profile templates

[Profiles](https://code.visualstudio.com/docs/editor/profiles "https://code.visualstudio.com/docs/editor/profiles") let you quickly switch your editor extensions, settings, and UI layout depending on your current project or task. To help you get started with profiles, we are shipping [Profile Templates](https://code.visualstudio.com/docs/editor/profiles#_profile-templates "https://code.visualstudio.com/docs/editor/profiles#_profile-templates"), which are curated profiles for different programming languages and scenarios. You can use a profile template as is or use it as a starting point to customize further for you own workflows.

You select a profile template through the **Profiles** > **Create Profile...** dropdown:

![Create Profile dropdown with profile templates](images/1_78/profile-template-dropdown.png)

Once you select a profile template, you can review the settings, extensions, and other data, and remove individual items if you don't want to include them in your new Profile.

![Profiles view showing the contents of the Data Science profile template](images/1_78/data-science-project-template.png)

After you create the new profile based on a template, changes made to settings, extensions, or UI are persisted to your profile.

### Glyph margin decoration rendering improvements

This month, we've improved the rendering of decorations that appear in the editor margin. Debugging-related decorations such as breakpoints and stack frame pointers will always render next to the editor line numbers. Additional decorations render to the left of any debugging-related decorations. This allows you to view your breakpoints even if there are other decorations on the same line, such as test decorations or bookmarks. Note that clicks are not yet scoped to individual decorations.

![bookmarks displayed next to breakpoint and stack frame pointer decorations](images/1_78/glyph-decorations.png)

### Copy images from the image preview

You can now copy images from the built-in image preview using `Ctrl+C` or by right-clicking in the preview and selecting **Copy**. The copied image data can be pasted back into VS Code or into other applications.

Editor
------

### Drop selector

VS Code lets you drop files and content into text editors by holding `Shift` before dropping. In this update, we've added UI that lets you change how this content is inserted into the file. After you drop an image into a Markdown file for example, this control lets you switch between inserting a Markdown image, a workspace relative path to the image, and the full path to the image:

The drop selector control appears whenever you drop content and there is more than one possible way it could be inserted. You can open the control by clicking on it or using `Ctrl+.`. The drop selector goes away as soon as you start typing or move the cursor outside of the inserted text. You can also fully disable the drop selector control using `"editor.dropIntoEditor.showDropSelector": "never"`.

VS Code includes a few built-in ways to drop common content formats. Extensions can also add their own drop options using the `DocumentDropEditProvider` API.

### Standalone color picker

It is now possible to launch a standalone color picker in order to insert and replace colors. To open the color picker, select **Show or Focus Standalone Color Picker** from the Command Palette.

![Standalone color picker control adjusted to blue color](images/1_78/standalone-color-picker.png)

When no colors or color formats are provided by extensions, the color-picker falls back to CSS-formatted colors. It is also now possible to visualize inline color decorators for CSS-formatted colors in all file types. To display these decorators, enable the **Editor: Default Color Decorators** (`editor.defaultColorDecorators`) setting.

### New snippet variable for timezone offset

A new snippet variable, `CURRENT_TIMEZONE_OFFSET`, is now available. This variable returns the current timezone offset in the format `+HHMM` or `-HHMM` (for example `-0700`). This complements other time-related snippet variables such as `CURRENT_YEAR`, `CURRENT_MONTH`, `CURRENT_DAY_NAME`, etc.

### Diff algorithm improvements

We continued improving the new diff algorithm in VS Code and deprecated the old algorithm. While the old algorithm is still the default for the diff editor, we will slowly change the default to the new algorithm and measure its performance.

You can override the default by setting `diffEditor.diffAlgorithm` to `advanced` (new diff algorithm) or `legacy` (default).

The new algorithm produces better diffs in many cases, but might be slower for some documents.

Here are some examples (legacy vs. advanced):

*   Improved line insertion diffs by considering indentation:
    
    ![JSON file diff result using legacy algorithm](images/1_78/diff-example1-legacy.png)
    
    ![JSON file diff result using advanced algorithm](images/1_78/diff-example1-advanced.png)
    
*   Improved word insertion diffs by considering space and separator characters:
    
    ![TypeScript imports word insertion diff using legacy algorithm](images/1_78/diff-example2-legacy.png)
    
    ![TypeScript imports word insertion diff using advanced algorithm](images/1_78/diff-example2-advanced.png)
    
*   More natural diffs by minimizing not just the length of the diff, but also the number of chunks:
    
    ![TypeScript added line diff using legacy algorithm](images/1_78/diff-example3-legacy.png)
    
    ![TypeScript added line diff using advanced algorithm](images/1_78/diff-example3-advanced.png)
    
*   Less noise by extending character level diffs to entire words if a part of the word changed significantly:
    
    ![TypeScript code change diff using legacy algorithm](images/1_78/diff-example4-legacy.png)
    
    ![TypeScript code change diff using legacy algorithm](images/1_78/diff-example4-advanced.png)
    

Diffing source code and even just evaluating the quality of a diff are hard problems and there is still room for improvement. If you encounter a diff where you think the algorithm could do better, try out our [diff playground](https://microsoft.github.io/monaco-editor/playground.html#XQAAAAJHAwAAAAAAAABBqQkHQ5NjdMjwa-jY7SIQ9S7DNlzs5W-mwj0fe1ZCDRFc9ws9XQE0SJE1jc2VKxhaLFIw9vEWSxW3yscw4B1FRgmSatbNyrNa50VLHWwDOn0YI7IfU0xJ0CGYU1vRtgnKPmZzQcQ1L9J7fCG48SpY2EIkpDE0S8hEos9yyee90RGD-wBeHe7sW88RInZzrk_ZW3jyJzSW_Xvd-X5Sb5qqa6C8CKmDej_-_rDHLSJRRYNrE9HyxNbsCq1E93qQGHETd9ab7kMGiL8C5K8AOGxTe69PiKFFKajiC0j4Vmv_8EEfs-kOqhfKi5-X4HhOM4OwOJEjvadYmtKTyTolnK5yDmgxV1Etg5Hj5Qzi10tewXOIWFf08DQcNm2YhOo-glAabugpGHC9BTZaUBH07kPrbyZjbuiKTPyoABP5oLEiuPLZjj7zFa4LAZCoHZ4WZLUhEbnWGkhiQE2tpW9j_GN7Ig "https://microsoft.github.io/monaco-editor/playground.html#XQAAAAJHAwAAAAAAAABBqQkHQ5NjdMjwa-jY7SIQ9S7DNlzs5W-mwj0fe1ZCDRFc9ws9XQE0SJE1jc2VKxhaLFIw9vEWSxW3yscw4B1FRgmSatbNyrNa50VLHWwDOn0YI7IfU0xJ0CGYU1vRtgnKPmZzQcQ1L9J7fCG48SpY2EIkpDE0S8hEos9yyee90RGD-wBeHe7sW88RInZzrk_ZW3jyJzSW_Xvd-X5Sb5qqa6C8CKmDej_-_rDHLSJRRYNrE9HyxNbsCq1E93qQGHETd9ab7kMGiL8C5K8AOGxTe69PiKFFKajiC0j4Vmv_8EEfs-kOqhfKi5-X4HhOM4OwOJEjvadYmtKTyTolnK5yDmgxV1Etg5Hj5Qzi10tewXOIWFf08DQcNm2YhOo-glAabugpGHC9BTZaUBH07kPrbyZjbuiKTPyoABP5oLEiuPLZjj7zFa4LAZCoHZ4WZLUhEbnWGkhiQE2tpW9j_GN7Ig") and share your feedback and ideas in our issue tracker!

### Inline completion improvements

This iteration we rewrote the inline completion feature and fixed [a lot of bugs](https://github.com/microsoft/vscode/issues?q=is%3Aclosed+is%3Aissue+milestone%3A%22April+2023%22+label%3Ainline-completions "https://github.com/microsoft/vscode/issues?q=is%3Aclosed+is%3Aissue+milestone%3A%22April+2023%22+label%3Ainline-completions").

Most notably, **Accept Word** now works across lines and there is a new command **Accept Line**. To support this feature, accepting the next word/line does not ask the extension again, as inline completion provider extensions would often report entirely different suggestions when asking for inline completions of the next line.

Extensions
----------

### Improved extension recommendations notification

The extension recommendations notification now shows the publisher of the recommended extension. This helps you make a more informed decision before installing the extension. The following images show the new notification when there are recommendations for both a single extension and multiple extensions.

![Extension recommendations notification with a single recommendation](images/1_78/extension-recommendations-notification-single.png) ![Extension recommendations notification with multiple recommendations](images/1_78/extension-recommendations-notification-multiple.png)

### Informing about installed deprecated extensions

If you have an extension installed that has been deprecated, you will now receive a notification informing you about it and suggesting alternatives. This is shown only once per deprecated extension.

![Notification about deprecated extension](images/1_78/deprecated-extension-notification.png)

Source Control
--------------

### Quick Fixes in the Source Control input

Code Actions and Quick Fixes are now supported in the Source Control message box:

The [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker "https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker") extension, for example, adds spelling fixes to the Source Control input. Extensions can contribute additional fixes and Code Actions.

### GitHub repository rulesets

VS Code already lets you define branch protection using the `git.branchProtection` setting. This milestone we added a new experimental feature that uses the recently announced [GitHub repository rulesets](https://docs.github.com/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets "https://docs.github.com/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets") to determine whether a branch is protected. If you are using GitHub repository rulesets, you can enable this feature using the `github.branchProtection` setting.

Notebooks
---------

### Drop image files into notebooks to create attachments

You can now drag and drop image files into notebook Markdown cells to create attachments. When you drop the image, use [the new drop selector control](#drop-selector "#drop-selector") to select **Insert Image as Attachment**:

![Using the drop selector in a notebook Markdown cell](images/1_78/notebook-drop.png)

This adds the image to the notebook as an attachment instead of simply adding a link to the image:

![An image file added as an attachment](images/1_78/notebook-drop-attachment.png)

### Toggle notebook output scrolling

You can now toggle individual cells to display output in a scrollable region either by command **Notebook: Toggle Scroll Cell Output** (`Ctrl+K Y`) or the link in the truncation message.

### Find control improvements

The notebook Find control now searches keywords on what's visually presented by default. Users can change the search scope (Markdown source, Markdown preview, code source, and code outputs) through setting `notebook.find.scope`. Additionally, when replacing matches, the Markdown cell is converted to an editable cell so you can make the replacement. When you're done, the cell is converted back to Markdown, and the preview is restored.

Languages
---------

### Drag and drop videos into Markdown files

Want to insert a video into your Markdown? Just drag it into the editor and then hold `Shift` to drop it into the file:

This inserts a `<video>` tag pointing to the video file. You can drag videos from VS Code's Explorer or from your local operating system.

### Strict nulls for JavaScript script blocks in HTML

You can now use the `js/ts.implicitProjectConfig.strictNullChecks` setting to enable strict nulls for JavaScript in HTML script blocks:

![Strict nulls in a script block](images/1_78/html-strict-null.png)

With strict nulls enabled, hovers and other IntelliSense features show when a type can be nullable. For example, notice how `el` now has a type of `HTMLElement | null`. This is because `document.getElementById` returns null if it can't find an element with that ID.

Testing
-------

[Continuous run](https://code.visualstudio.com/updates/v1_75#_continuous-test-runs "https://code.visualstudio.com/updates/v1_75#_continuous-test-runs") can now be turned on for individual tests. This requires a test extension that supports continuous run and has adopted the `supportsContinuousRun` API finalized last iteration.

![Continuous run button highlighted on an individual test](images/1_78/testing-continous-run.png)

VS Code for the Web
-------------------

### Commit files to Git Large File Storage

Git Large File Storage (LFS) allows you to efficiently store large files in Git repositories. [github.dev](https://github.dev "https://github.dev") and [vscode.dev](https://vscode.dev "https://vscode.dev") now support committing files to Git LFS in repositories hosted on GitHub, enabling easy updates from your browser without needing to install the LFS extension for Git locally.

LFS commit support in github.dev and vscode.dev works out of the box when your repository already has a `.gitattributes` file in the root of your repository that specifies which file types should be stored with Git LFS. To set up your repository for Git LFS for the first time, consult the [Git LFS](https://git-lfs.com "https://git-lfs.com") documentation.

Remote Development
------------------

The [Remote Development extensions](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack "https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack"), allow you to use a [Dev Container](https://code.visualstudio.com/docs/devcontainers/containers "https://code.visualstudio.com/docs/devcontainers/containers"), remote machine via SSH or [Remote Tunnels](https://code.visualstudio.com/docs/remote/tunnels "https://code.visualstudio.com/docs/remote/tunnels"), or the [Windows Subsystem for Linux](https://learn.microsoft.com/windows/wsl "https://learn.microsoft.com/windows/wsl") (WSL) as a full-featured development environment.

You can learn about new extension features and bug fixes in the [Remote Development release notes](https://github.com/microsoft/vscode-docs/blob/main/remote-release-notes/v1_78.md "https://github.com/microsoft/vscode-docs/blob/main/remote-release-notes/v1_78.md").

And check out the [Develop Anywhere with VS Code](https://www.youtube.com/watch?v=c0L85sFHF2I&list=PLj6YeMhvp2S7hWnmPEcxsSPEB0FLHqi0j&index=11 "https://www.youtube.com/watch?v=c0L85sFHF2I&list=PLj6YeMhvp2S7hWnmPEcxsSPEB0FLHqi0j&index=11") VS Code Day session.

Contributions to extensions
---------------------------

### Python

#### Jupyter extension no longer installed by default

The [Jupyter](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter "https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter") extension is no longer automatically installed alongside the [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python "https://marketplace.visualstudio.com/items?itemName=ms-python.python") extension by default. This change was made in response to [feedback](https://github.com/microsoft/vscode-python/issues/18073 "https://github.com/microsoft/vscode-python/issues/18073") from [Dev Container](https://code.visualstudio.com/docs/devcontainers/containers "https://code.visualstudio.com/docs/devcontainers/containers") users who wanted a faster container creation process without the Jupyter extension installed by default.

If you have Dev Container definitions that only list the Python extension and wish to continue using the Jupyter notebooks features in your containers, you can add the Jupyter extension ID to your `devcontainer.json` file:

      "customizations": {    "vscode": {      "extensions": ["ms-python.vscode-pylance", "ms-python.python", "ms-toolsai.jupyter"]    }  }
    

Alternatively, you can create a [Profile](https://code.visualstudio.com/docs/editor/profiles "https://code.visualstudio.com/docs/editor/profiles") that includes the Python and Jupyter extensions, as well as any other of your favorite extensions.

#### Create environment command with microvenv

When the **Python: Create environment** command is invoked using a Python distribution that doesn't have the `venv` package installed, the Python extension now uses [microvenv](https://github.com/brettcannon/microvenv "https://github.com/brettcannon/microvenv") as a fallback. This can be a hurdle for Python environments that are preinstalled on Unix-based systems.

Microvenv is a lightweight Python module that offers a minimalist approach to creating virtual environments for your Python projects. It is not equipped with traditional activation scripts like virtual environments, but it provides a good alternative for creating an isolated environment when the `venv` module is not available in your Python distribution.

The **Create Environment** command will also install `pip` into the environments created via `microvenv`.

#### Formatter extension recommendations

In previous releases, we announced new extensions for the [Black Formatter](https://marketplace.visualstudio.com/items?itemName=ms-python.black-formatter "https://marketplace.visualstudio.com/items?itemName=ms-python.black-formatter") and [autopep8](https://marketplace.visualstudio.com/items?itemName=ms-python.autopep8 "https://marketplace.visualstudio.com/items?itemName=ms-python.autopep8") that work in tandem with the Python extension through the [Language Server Protocol](https://microsoft.github.io/language-server-protocol "https://microsoft.github.io/language-server-protocol") (LSP) to provide formatting for Python files. In this release, we display a notification if you are still using the Python extension's built-in formatting features, prompting you to install these new extensions.

#### Run Python actions are now in submenus

In order to streamline the Python commands available when right-clicking on the editor, the **Run Python File in Terminal** and **Run Selection/Line in Python Terminal** commands are now submenu items under the **Run Python** entry.

![Run Python option on context menu with "Run file in terminal" and "Run selection/line" options in the submenu](images/1_78/run-python-submenu.png)

#### Automatic conversion of f-strings

There's a new `"python.analysis.autoFormatStrings"` setting that enables automatic conversion of f-strings when using [Pylance](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance "https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance"). Once enabled, Pylance will automatically insert an `f` at the beginning of a string when you insert `{` within quotes:

The default value for this setting is currently disabled, but will be enabled in an upcoming release pending positive feedback. If you have any comments or suggestions regarding this feature, feel free to share them on the [Pylance GitHub repository](https://github.com/microsoft/pylance-release "https://github.com/microsoft/pylance-release").

#### Code navigation enabled on strings that contain paths

There's another new experimental setting called `"python.analysis.gotoDefinitionInStringLiteral"` that enables **Go to Definition** from module-like string literals. This can be helpful if you're working on web applications, such as Django apps, and want to navigate to modules or paths defined in string literals:

This new setting, like the `autoFormatStrings` setting mentioned earlier, is currently disabled by default. However, we plan to enable this behavior in a future release based on feedback. Eventually, we plan to remove this setting entirely.

### Jupyter

#### Restart commands

The [Jupyter](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter "https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter") extension now includes two new commands, enabling the user to restart the kernel and run cells directly. The commands are **Restart Kernel and Run All Cells** and **Restart Kernel and Run Up To Selected Cell**, and can be accessed via the command IDs `jupyter.restartkernelandrunallcells` and `jupyter.restartkernelandrunuptoselectedcell` respectively.

#### Reconnect to busy remote Jupyter kernels

In previous releases, when connecting to a remote Jupyter kernel session, the Jupyter extension would wait for the kernel to be idle before connecting. This could take a long time if the kernel was busy running a long-running computation. In this release, the Jupyter extension connects to the kernel immediately, even if it is busy. This allows you to interrupt the kernel while it is busy.

#### Platform-specific Jupyter extensions

The Jupyter extension now ships [platform-specific extensions](https://code.visualstudio.com/api/working-with-extensions/publishing-extension#platformspecific-extensions "https://code.visualstudio.com/api/working-with-extensions/publishing-extension#platformspecific-extensions"), with each VSIX built for a specific platform (Windows 64 bit, Windows 32 bit, Linux x64, Alpine x64, macOS Intel, macOS Apple Silicon, etc.). The download size of the Jupyter extension for individual platforms is smaller, resulting in faster download times and less disk space usage.

### GitHub Pull Requests and Issues

There has been more progress on the [GitHub Pull Requests and Issues](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github "https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github") extension, which allows you to work on, create, and manage pull requests and issues. Highlights include:

*   You can add team reviewers to a pull request.
*   All of the places where you can **Checkout default branch** now respect the `git.pullBeforeCheckout` setting.
*   GitHub's file level commenting is supported.

Review the [changelog for the 0.64.0](https://github.com/microsoft/vscode-pull-request-github/blob/main/CHANGELOG.md#0640 "https://github.com/microsoft/vscode-pull-request-github/blob/main/CHANGELOG.md#0640") release of the extension to learn about the other highlights.

### GitHub Copilot

> **Note**: To get access to the new chat-based GitHub Copilot features, you'll need to sign up for the [GitHub Copilot chat waitlist](https://github.com/github-copilot/chat_waitlist_signup/join "https://github.com/github-copilot/chat_waitlist_signup/join"). These features are only available in VS Code [Insiders](https://code.visualstudio.com/insiders "https://code.visualstudio.com/insiders") with the [GitHub Copilot Nightly](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot-nightly "https://marketplace.visualstudio.com/items?itemName=GitHub.copilot-nightly") extension.

#### Chat editors

Our first iteration on GitHub Copilot Chat enabled chat sessions in the sidebar. Now, we support opening the same chat view as an editor. This lets you customize the position of your chat session to be anywhere you want within your window layout.

You can open a chat editor by running the command **Interactive Session: Open Editor** and then move it between editor groups just as you would with any other editor.

![A chat view as an editor](images/1_78/chat-editor.png)

#### Additional codeblock commands

There are two new commands in the codeblock toolbar, **Insert into New File** and **Run in Terminal**. These are next to the existing commands **Copy** and **Insert at Cursor**, and give you extra options for quickly taking action on the code suggestions that are returned from Copilot.

![The codeblock toolbar showing the two new codeblock commands](images/1_78/chat-codeblock-commands.png)

#### Code Actions and inline chat

Editor chat sessions are now integrated with the Quick Fixes. Select the light bulb for a squiggle and there are options to fix or explain using Copilot.

In addition to Code Actions, inline chat is now also available from the editor context menu.

#### Inline chat modes

There is now a setting to change the different modes of inline chat: `interactiveEditor.editMode`.

The options are:

*   `live` - Apply AI suggested changes directly to the editor (default).
*   `livePreview` - Apply changes but renders them in an embedded diff editor.
*   `preview` - Show changes in a disconnected, embedded diff editor.

#### Similar commands in the Command Palette

With the power of Copilot, the Command Palette is now able to show similar command results. To enable this, you must have an active Copilot subscription, be in the private preview of the chat view, and apply the setting:

    "workbench.commandPalette.experimental.useSemanticSimilarity": true
    

Here are some examples:

*   "turn on autosave" being interpreted as **Toggle Auto Save**
    
    ![query "turn on autosave" is correctly resolved to Toggle Auto Save](images/1_78/command-palette-similar-results.png)
    
*   "add function" includes additional results at the bottom with contributions from extensions
    
    ![query "add function" including Azure Functions Create Function command](images/1_78/command-palette-similar-results-2.png)
    
*   Lastly, if your results yield no results, you can **Ask GitHub Copilot**, which puts what's in your filter box in a new chat for Copilot to handle.
    
    ![Ask GitHub Copilot "no results" option in the Command Palette](images/1_78/ask-copilot.png)
    

We will be iterating in this space so stay tuned!

Preview Features
----------------

### TypeScript 5.1 Support

This update includes support for the upcoming TypeScript 5.1 release. Read the [TypeScript 5.1 Beta blog post](https://devblogs.microsoft.com/typescript/announcing-typescript-5-1-beta "https://devblogs.microsoft.com/typescript/announcing-typescript-5-1-beta") and [TypeScript 5.1 iteration plan](https://github.com/microsoft/TypeScript/issues/53031 "https://github.com/microsoft/TypeScript/issues/53031") for more details on what the TypeScript team is currently working on. Some editor tooling highlights:

*   Linked editing support for JSX tags.
*   Snippet completions for `@param` JSDoc tags.

To start using the TypeScript 5.1 nightly builds, install the [TypeScript Nightly](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-typescript-next "https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-typescript-next") extension.

### Rename matching JSX tags using F2

When you trigger rename on a JSX tag, VS Code now renames just the matching tag instead of trying to update all references to the tag:

This requires TypeScript 5.1+ and matches how rename works in HTML.

You can disable this behavior using `javascript.preferences.renameMatchingJsxTags` and `typescript.preferences.renameMatchingJsxTags`.

Extension authoring
-------------------

### Workspace edits can now create files directly from DataTransferFile

One of the primary uses of the [drop into editor API](https://github.com/microsoft/vscode-extension-samples/tree/main/drop-on-document "https://github.com/microsoft/vscode-extension-samples/tree/main/drop-on-document") is writing dropped files/content into the workspace. However in previous VS Code releases, this could be fairly slow for large files. This is because the file contents end up being copied between processes twice: first from the renderer to the extension host to read the file contents, and then back from the extension host to the renderer to write the file.

    class CreateFileDropProvider implements vscode.DocumentDropEditProvider {    async provideDocumentDropEdits(_document: vscode.TextDocument, _position: vscode.Position, dataTransfer: vscode.DataTransfer, _token: vscode.CancellationToken): Promise<vscode.DocumentDropEdit | undefined> {        const pngFile = dataTransfer.get('image/png')?.asFile();        if (!pngFile) {            return;        }        // Read file        // This results in the entire file contents being copied over to the extension host.        const contents = await pngFile.data();        // Now create a workspace edit that writes the file into the workspace        // This results in the same file contents from above being copied back again.        const additionalEdit = new vscode.WorkspaceEdit();        const path = vscode.Uri.joinPath(vscode.workspace.workspaceFolders![0].uri, 'image.png');        additionalEdit.createFile(path, { contents });        const edit = new vscode.DocumentDropEdit(path.fsPath);        edit.additionalEdit = additionalEdit;        return edit;    }}
    

Now you can avoid those extra copies though by passing a `DataTransferFile` directly to `WorkspaceEdit.createFile`:

    additionalEdit.createFile(path, { contents: pngFile });
    

This should significantly improve performance, especially when working with larger files.

### Resolve Code Action commands in resolveCodeAction

A `CodeActionProvider` can now lazily resolve the command of `CodeAction` in `resolveCodeAction`. Previously only the edits for the Code Action could be lazily resolved.

If the command is expensive to compute, this allows a `CodeActionProvider` to defer this work until the Code Action is going to be applied.

### editor/lineNumber/context menu

We have finalized the `editor/lineNumber/context` menu. This allows extension authors to contribute actions to a context menu anchored to the editor line number and glyph margin. Actions contributed to this menu receive the line number in command arguments and can reference the `editorLineNumber` context key in their when clauses.

### Authentication API improvements

#### Authentication session preference is now workspace aware

For authentication providers that support being signed into multiple accounts at once (like Microsoft), the user is prompted to select an account to use when `vscode.authentication.getSession` with `createIfNone: true` is called.

**Previous behavior:**

This preference is remembered until `vscode.authentication.getSession` is called with the `ClearSessionPreference` flag.

**New behavior:**

This preference is remembered per-workspace until `vscode.authentication.getSession` is called in that workspace with the `ClearSessionPreference` flag.

This behavior was introduced to allow extensions to use different accounts for different workspaces and allow those preferences to be remembered.

> **Note**: The preference is extension specific. So if one extension calls `vscode.authentication.getSession`, it will not affect the session preference for another extension calling `vscode.authentication.getSession`.

#### Microsoft Sovereign Cloud support in desktop

This iteration, we introduced a new Authentication Provider into the core product: `Microsoft Sovereign Cloud`. This provider is for authenticating users to [Microsoft Cloud for Sovereignty](https://www.microsoft.com/en-us/industry/sovereignty/cloud "https://www.microsoft.com/en-us/industry/sovereignty/cloud") like Azure US Government, Azure China, etc. Under the hood, it works identically to the `Microsoft` auth provider, only with different URLs. If you want to use this auth provider, you can guide the user through setting the `microsoft-sovereign-cloud.endpoint` value, which has a couple of defaults but also supports custom Sovereign Cloud URLs as well.

Keep in mind that most users do not have a Sovereign Cloud account. Our recommendation is that if you want to support Sovereign Clouds, you should make it possible for users to sign in via Sovereign Clouds, but not include it as part of the mainline workflow so as not to confuse users.

Proposed APIs
-------------

Every milestone comes with new proposed APIs and extension authors can try them out. As always, we want your feedback. Here are the steps to try out a proposed API:

1.  [Find a proposal that you want to try](https://github.com/microsoft/vscode/tree/main/src/vscode-dts "https://github.com/microsoft/vscode/tree/main/src/vscode-dts") and add its name to `package.json#enabledApiProposals`.
2.  Use the latest [vscode-dts](https://www.npmjs.com/package/vscode-dts "https://www.npmjs.com/package/vscode-dts") and run `vscode-dts dev`. It will download the corresponding `d.ts` files into your workspace.
3.  You can now program against the proposal.

You cannot publish an extension that uses a proposed API. There may be breaking changes in the next release and we never want to break existing extensions.

### Format multiple ranges

The `DocumentRangeFormattingEditProvider` API has an optional proposed function to support formatting multiple ranges at once. By adopting this API, providers improve the format modified ranges flow because only a single request to a language service is needed.

### Document drop metadata

This new proposal enriches the existing [drop into editor](https://github.com/microsoft/vscode-extension-samples/tree/main/drop-on-document "https://github.com/microsoft/vscode-extension-samples/tree/main/drop-on-document") API to support the [new drop selector](#drop-selector "#drop-selector"). Providers can use it to provide a better drop into editor experience.

The first part of this proposal adds a `label` property to `DocumentDropEdit`. This human readable label describes the edit and is shown in the drop selector UI:

![Labels shown in the drop selector](images/1_78/notebook-drop.png)

The second part adds an extra `metadata` argument to `registerDocumentDropEditProvider`. This metadata argument identifies the provider and tells VS Code the types of content it applies to:

    vscode.languages.registerDocumentDropEditProvider('markdown', new InsertBase64ImageProvider(), {    // Unique id that identities this provider    id: 'insertBase64Image',    // Array of mime types, such as `image/png` or `text/plain`, that this provider supports.    // You can also use wildcards, such as `image/*` which matches any image content that is dropped.    dropMimeTypes: ["image/*"]})
    

The `dropMimeTypes` array can help improve performance as your provider is only called for relevant dropped content.

Engineering
-----------

### Electron 22 update

In this milestone, we have finished our [experiment](https://code.visualstudio.com/updates/v1_77#_exploring-custom-memory-allocator-for-the-extension-host "https://code.visualstudio.com/updates/v1_77#_exploring-custom-memory-allocator-for-the-extension-host") with using a custom allocator for extension host and are ready to bundle Electron 22 into VS Code Desktop. We want to thank everyone involved with self-hosting on [Insiders builds](https://code.visualstudio.com/insiders "https://code.visualstudio.com/insiders") and provided early feedback. This update comes with Chromium `108.0.5359.215` and Node.js `16.17.1`.

VS Code Day
-----------

You can catch up on all the highlights from VS Code Day with the [VS Code Day 2023](https://www.youtube.com/playlist?list=PLj6YeMhvp2S7hWnmPEcxsSPEB0FLHqi0j "https://www.youtube.com/playlist?list=PLj6YeMhvp2S7hWnmPEcxsSPEB0FLHqi0j") YouTube playlist. There you will find sessions on topics such as [GitHub Copilot](https://www.youtube.com/watch?v=9ZQ4yMl7rHw&list=PLj6YeMhvp2S7hWnmPEcxsSPEB0FLHqi0j&index=3 "https://www.youtube.com/watch?v=9ZQ4yMl7rHw&list=PLj6YeMhvp2S7hWnmPEcxsSPEB0FLHqi0j&index=3"), [Data Science](https://www.youtube.com/watch?v=3JvIS2lvkqQ&list=PLj6YeMhvp2S7hWnmPEcxsSPEB0FLHqi0j&index=8 "https://www.youtube.com/watch?v=3JvIS2lvkqQ&list=PLj6YeMhvp2S7hWnmPEcxsSPEB0FLHqi0j&index=8"), and [TypeScript](https://www.youtube.com/watch?v=HalycM9tSNM&list=PLj6YeMhvp2S7hWnmPEcxsSPEB0FLHqi0j&index=4 "https://www.youtube.com/watch?v=HalycM9tSNM&list=PLj6YeMhvp2S7hWnmPEcxsSPEB0FLHqi0j&index=4"), as well as the [Keynote](https://www.youtube.com/watch?v=sBzLV8GJSJ4&list=PLj6YeMhvp2S7hWnmPEcxsSPEB0FLHqi0j&index=2 "https://www.youtube.com/watch?v=sBzLV8GJSJ4&list=PLj6YeMhvp2S7hWnmPEcxsSPEB0FLHqi0j&index=2") by Erich Gamma and Kai Maetzel, where they explain how the team builds and ships VS Code.

Thank you
---------

Last but certainly not least, a big _**Thank You**_ to the contributors of VS Code.

### Issue tracking

Contributions to our issue tracking:

*   [@gjsjohnmurray (John Murray)](https://github.com/gjsjohnmurray "https://github.com/gjsjohnmurray")
*   [@IllusionMH (Andrii Dieiev)](https://github.com/IllusionMH "https://github.com/IllusionMH")
*   [@starball5 (starball)](https://github.com/starball5 "https://github.com/starball5")
*   [@tamuratak (Takashi Tamura)](https://github.com/tamuratak "https://github.com/tamuratak")
*   [@Kathund (Kath)](https://github.com/Kathund "https://github.com/Kathund")
*   [@ArturoDent (ArturoDent)](https://github.com/ArturoDent "https://github.com/ArturoDent")

### Pull requests

Contributions to `vscode`:

*   [@a-stewart (Anthony Stewart)](https://github.com/a-stewart "https://github.com/a-stewart"): Support copying non-pngs and wait for focus to avoid race conditions [PR #180322](https://github.com/microsoft/vscode/pull/180322 "https://github.com/microsoft/vscode/pull/180322")
*   [@andrewbranch (Andrew Branch)](https://github.com/andrewbranch "https://github.com/andrewbranch"): \[typescript-language-features\] Support replacing Go to Definition with Go to Source Definition by preference [PR #178840](https://github.com/microsoft/vscode/pull/178840 "https://github.com/microsoft/vscode/pull/178840")
*   [@c-claeys (Cristopher Claeys)](https://github.com/c-claeys "https://github.com/c-claeys"): Add support for multiRange formatting [PR #163190](https://github.com/microsoft/vscode/pull/163190 "https://github.com/microsoft/vscode/pull/163190")
*   [@donaldnevermore (Donald33 Wang)](https://github.com/donaldnevermore "https://github.com/donaldnevermore"): Support custom switch-case indentation [PR #179670](https://github.com/microsoft/vscode/pull/179670 "https://github.com/microsoft/vscode/pull/179670")
*   [@FlorentRevest (Florent Revest)](https://github.com/FlorentRevest "https://github.com/FlorentRevest"): debug session: use queue to make sure debugee status get processed in correct order [PR #180410](https://github.com/microsoft/vscode/pull/180410 "https://github.com/microsoft/vscode/pull/180410")
*   [@gjsjohnmurray (John Murray)](https://github.com/gjsjohnmurray "https://github.com/gjsjohnmurray"): Set a max-height on comments and add vertical scrolling (#174629) [PR #180044](https://github.com/microsoft/vscode/pull/180044 "https://github.com/microsoft/vscode/pull/180044")
*   [@hermannloose (Hermann Loose)](https://github.com/hermannloose "https://github.com/hermannloose"): Allow individual comments to be marked as draft [PR #173305](https://github.com/microsoft/vscode/pull/173305 "https://github.com/microsoft/vscode/pull/173305")
*   [@iliazeus (Ilia Pozdnyakov)](https://github.com/iliazeus "https://github.com/iliazeus"): Add support for F20-F24 keys in keyboard shortcuts [PR #179591](https://github.com/microsoft/vscode/pull/179591 "https://github.com/microsoft/vscode/pull/179591")
*   [@jeanp413 (Jean Pierre)](https://github.com/jeanp413 "https://github.com/jeanp413"): Fixes configured default shell not used when connecting to remote [PR #175844](https://github.com/microsoft/vscode/pull/175844 "https://github.com/microsoft/vscode/pull/175844")
*   [@jjaeggli (Jacob Jaeggli)](https://github.com/jjaeggli "https://github.com/jjaeggli"): Accessibility help dialog uses semantic markup for assistive technology [PR #179726](https://github.com/microsoft/vscode/pull/179726 "https://github.com/microsoft/vscode/pull/179726")
*   [@KapitanOczywisty](https://github.com/KapitanOczywisty "https://github.com/KapitanOczywisty"): Update PHP grammar from fork [PR #180100](https://github.com/microsoft/vscode/pull/180100 "https://github.com/microsoft/vscode/pull/180100")
*   [@LakshyAAAgrawal (Lakshya A Agrawal)](https://github.com/LakshyAAAgrawal "https://github.com/LakshyAAAgrawal"): Fix typo in vscode.d.ts [PR #177377](https://github.com/microsoft/vscode/pull/177377 "https://github.com/microsoft/vscode/pull/177377")
*   [@mahmoudsalah1993 (Mahmoud Salah)](https://github.com/mahmoudsalah1993 "https://github.com/mahmoudsalah1993"): Return the key correctly when having a single userDataProfileContentH… [PR #178517](https://github.com/microsoft/vscode/pull/178517 "https://github.com/microsoft/vscode/pull/178517")
*   [@Mai-Lapyst](https://github.com/Mai-Lapyst "https://github.com/Mai-Lapyst"): Fix accidently starting all onTaskType extensions when running any task; fixes #175821 [PR #178679](https://github.com/microsoft/vscode/pull/178679 "https://github.com/microsoft/vscode/pull/178679")
*   [@maxmmyron (Max)](https://github.com/maxmmyron "https://github.com/maxmmyron"): Fix: diff editor arrow click enables breakpoint [PR #179130](https://github.com/microsoft/vscode/pull/179130 "https://github.com/microsoft/vscode/pull/179130")
*   [@mblout (Michael Blout)](https://github.com/mblout "https://github.com/mblout"): Add debug API for call stack selection changes (63943) [PR #179132](https://github.com/microsoft/vscode/pull/179132 "https://github.com/microsoft/vscode/pull/179132")
*   [@MonadChains (MonadChains)](https://github.com/MonadChains "https://github.com/MonadChains"): Issue 151220/add current timezone offset variable [PR #170518](https://github.com/microsoft/vscode/pull/170518 "https://github.com/microsoft/vscode/pull/170518")
*   [@simon04 (Simon Legner)](https://github.com/simon04 "https://github.com/simon04"): terminalActions: "Open Last URL" [PR #173217](https://github.com/microsoft/vscode/pull/173217 "https://github.com/microsoft/vscode/pull/173217")
*   [@SimonSiefke (Simon Siefke)](https://github.com/SimonSiefke "https://github.com/SimonSiefke"): fix: printing of extension id in mainThreadExtensionService [PR #179553](https://github.com/microsoft/vscode/pull/179553 "https://github.com/microsoft/vscode/pull/179553")
*   [@spahnke (Sebastian Pahnke)](https://github.com/spahnke "https://github.com/spahnke"): \[Monaco\] Add `monaco.editor.registerEditorOpener` method to be able to intercept editor open operations [PR #177064](https://github.com/microsoft/vscode/pull/177064 "https://github.com/microsoft/vscode/pull/177064")
*   [@sumneko (最萌小汐)](https://github.com/sumneko "https://github.com/sumneko"): Update Lua grammar [PR #177798](https://github.com/microsoft/vscode/pull/177798 "https://github.com/microsoft/vscode/pull/177798")
*   [@tisilent (xie jialong 努力鸭)](https://github.com/tisilent "https://github.com/tisilent"): Fix #159471 [PR #177961](https://github.com/microsoft/vscode/pull/177961 "https://github.com/microsoft/vscode/pull/177961")
*   [@tomheaton (Tom Heaton)](https://github.com/tomheaton "https://github.com/tomheaton"): Fix `collapseAll` command when no folder is open [PR #180330](https://github.com/microsoft/vscode/pull/180330 "https://github.com/microsoft/vscode/pull/180330")
*   [@weartist (Han)](https://github.com/weartist "https://github.com/weartist")
    *   support to open both integrated terminal and external terminal with … [PR #168879](https://github.com/microsoft/vscode/pull/168879 "https://github.com/microsoft/vscode/pull/168879")
    *   Added support for breakpointWidget to automatically adapt to width wh… [PR #179551](https://github.com/microsoft/vscode/pull/179551 "https://github.com/microsoft/vscode/pull/179551")
    *   add confirmation before removing cell for #173481 [PR #179776](https://github.com/microsoft/vscode/pull/179776 "https://github.com/microsoft/vscode/pull/179776")
*   [@Wundero (Sam Riddle)](https://github.com/Wundero "https://github.com/Wundero"): Use defined variable instead of internal property [PR #178701](https://github.com/microsoft/vscode/pull/178701 "https://github.com/microsoft/vscode/pull/178701")
*   [@yiliang114 (易良)](https://github.com/yiliang114 "https://github.com/yiliang114")
    *   fix: close #176763, modify the conditions to load vscode-web-playground [PR #176771](https://github.com/microsoft/vscode/pull/176771 "https://github.com/microsoft/vscode/pull/176771")
    *   chore: rename wrong service name [PR #177954](https://github.com/microsoft/vscode/pull/177954 "https://github.com/microsoft/vscode/pull/177954")
    *   fix: typos [PR #179581](https://github.com/microsoft/vscode/pull/179581 "https://github.com/microsoft/vscode/pull/179581")
*   [@YinDongFang (dongfang)](https://github.com/YinDongFang "https://github.com/YinDongFang"): Fix 'Window' key is treated as 'unknown' in Firefox (#175739) [PR #175740](https://github.com/microsoft/vscode/pull/175740 "https://github.com/microsoft/vscode/pull/175740")

Contributions to `vscode-js-debug`:

*   [@markw65](https://github.com/markw65 "https://github.com/markw65"): Fix the race for the javascript terminal too [PR #1654](https://github.com/microsoft/vscode-js-debug/pull/1654 "https://github.com/microsoft/vscode-js-debug/pull/1654")

Contributions to `vscode-json-languageservice`:

*   [@zardoy (Vitaly)](https://github.com/zardoy "https://github.com/zardoy")
    *   \[completions\] Always show details such as `Default value` [PR #183](https://github.com/microsoft/vscode-json-languageservice/pull/183 "https://github.com/microsoft/vscode-json-languageservice/pull/183")
    *   \[completion\] Don't suggest duplicates when `uniqueItems: true` [PR #184](https://github.com/microsoft/vscode-json-languageservice/pull/184 "https://github.com/microsoft/vscode-json-languageservice/pull/184")

Contributions to `vscode-pull-request-github`:

*   [@Balastrong (Leonardo Montini)](https://github.com/Balastrong "https://github.com/Balastrong")
    *   Add x button to remove a label from a new PR [PR #4649](https://github.com/microsoft/vscode-pull-request-github/pull/4649 "https://github.com/microsoft/vscode-pull-request-github/pull/4649")
    *   Change file mode for execute husky hook on MacOS [PR #4695](https://github.com/microsoft/vscode-pull-request-github/pull/4695 "https://github.com/microsoft/vscode-pull-request-github/pull/4695")
*   [@eastwood (Clinton Ryan)](https://github.com/eastwood "https://github.com/eastwood"): Gracefully handle errors where the SSH configuration file is corrupt or malformed [PR #4644](https://github.com/microsoft/vscode-pull-request-github/pull/4644 "https://github.com/microsoft/vscode-pull-request-github/pull/4644")
*   [@kabel (Kevin Abel)](https://github.com/kabel "https://github.com/kabel")
    *   Fix status checks rendering [PR #4542](https://github.com/microsoft/vscode-pull-request-github/pull/4542 "https://github.com/microsoft/vscode-pull-request-github/pull/4542")
    *   Make the display of PR number in tree view configurable [PR #4576](https://github.com/microsoft/vscode-pull-request-github/pull/4576 "https://github.com/microsoft/vscode-pull-request-github/pull/4576")
    *   Centralize all configuration strings into `settingKeys.ts` [PR #4577](https://github.com/microsoft/vscode-pull-request-github/pull/4577 "https://github.com/microsoft/vscode-pull-request-github/pull/4577")
    *   Move `PullRequest` to a shared location for reviewing of types [PR #4578](https://github.com/microsoft/vscode-pull-request-github/pull/4578 "https://github.com/microsoft/vscode-pull-request-github/pull/4578")
*   [@ypresto (Yuya Tanaka)](https://github.com/ypresto "https://github.com/ypresto"): Fix wrong repo URL for nested repos in workspace (fix copy permalink) [PR #4711](https://github.com/microsoft/vscode-pull-request-github/pull/4711 "https://github.com/microsoft/vscode-pull-request-github/pull/4711")

Contributions to `monaco-editor`:

*   [@dneto0 (David Neto)](https://github.com/dneto0 "https://github.com/dneto0"): Add WebGPU Shading Language tokenizer, with tests [PR #3884](https://github.com/microsoft/monaco-editor/pull/3884 "https://github.com/microsoft/monaco-editor/pull/3884")
*   [@kisstkondoros (Tamas Kiss)](https://github.com/kisstkondoros "https://github.com/kisstkondoros"): Fix reference error in convert method of OutlineAdapter [PR #3924](https://github.com/microsoft/monaco-editor/pull/3924 "https://github.com/microsoft/monaco-editor/pull/3924")
*   [@tamayika](https://github.com/tamayika "https://github.com/tamayika"): Change moduleResolution to node16 and adopt TS 5.0 [PR #3860](https://github.com/microsoft/monaco-editor/pull/3860 "https://github.com/microsoft/monaco-editor/pull/3860")

Contributions to `devcontainers/cli`:

*   [@aaronlehmann (Aaron Lehmann)](https://github.com/aaronlehmann "https://github.com/aaronlehmann"): Add support for Docker credential helpers [PR #460](https://github.com/devcontainers/cli/pull/460 "https://github.com/devcontainers/cli/pull/460")

[](# "Scroll to top")

 const vscode = acquireVsCodeApi(); const container = document.createElement('p'); container.style.display = 'flex'; container.style.alignItems = 'center'; const input = document.createElement('input'); input.type = 'checkbox'; input.id = 'showReleaseNotes'; input.checked = true; container.appendChild(input); const label = document.createElement('label'); label.htmlFor = 'showReleaseNotes'; label.textContent = 'Show release notes after an update'; container.appendChild(label); const beforeElement = document.querySelector("body > h1")?.nextElementSibling; console.log(beforeElement); if (beforeElement) { document.body.insertBefore(container, beforeElement); } else { document.body.appendChild(container); } window.addEventListener('message', event => { if (event.data.type === 'showReleaseNotes') { input.checked = event.data.value; } }); input.addEventListener('change', event => { vscode.postMessage({ type: 'showReleaseNotes', value: input.checked }, '\*'); });