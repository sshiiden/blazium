# Contributors guidelines

This document summarizes the most important points for people interested in
contributing to Blazium, especially via bug reports or pull requests.

The [Blazium Discord](https://chat.blazium.app) has additional information about contributing.

## Table of contents

- [Reporting bugs](#reporting-bugs)
- [Proposing features or improvements](#proposing-features-or-improvements)
- [Contributing pull requests](#contributing-pull-requests)
- [Contributing to Blazium translations](#contributing-to-blazium-translations)
- [Communicating with developers](#communicating-with-developers)

## Reporting bugs

Report bugs [here](https://github.com/godotengine/godot/issues/new?assignees=&labels=&template=bug_report.yml).
Please follow the instructions in the template when you do.

Notably, please include a Minimal Reproduction Project (MRP), which is a small
Godot project which reproduces the issue, with no unnecessary files included.
Be sure to not include the `.godot` folder in the archive to save space.

Make sure that the bug you are experiencing is reproducible in the latest Godot
releases. You can find an overview of all Godot releases [on the website](https://godotengine.org/download/archive/)
to confirm whether your current version is the latest one. It's worth testing
against both the latest stable release and the latest dev snapshot for the next
Godot release.

If you run into a bug which wasn't present in an earlier Godot version (what we
call a _regression_), please mention it and clarify which versions you tested
(both the one(s) working and the one(s) exhibiting the bug).

## Proposing features or improvements

**The main issue tracker is for bug reports and does not accept feature proposals.**

Instead, head to the [Blazium Discord](https://chat.blazium.app) and leave a suggestion in the appropriate chat.

## Contributing pull requests

If you want to add new engine features, please make sure that:

- This functionality is desired, which means that it solves a common use case
  that several users will need in their real-life projects.
- You talked to other developers on how to implement it best. See also
  [Proposing features or improvements](#proposing-features-or-improvements).
- Even if it doesn't get merged, your PR is useful for future work by another
  developer.

Similar rules can be applied when contributing bug fixes - it's always best to
discuss the implementation in the bug report first if you are not 100% about
what would be the best fix.

Visit the [Blazium Discord](https://chat.blazium.app) for information and guides related to contribution and pull requests.

### Be mindful of your commits

Try to make simple PRs that handle one specific topic. Just like for reporting
issues, it's better to open 3 different PRs that each address a different issue
than one big PR with three commits. This makes it easier to review, approve, and
merge the changes independently.

When updating your fork with upstream changes, please use ``git pull --rebase``
to avoid creating "merge commits". Those commits unnecessarily pollute the git
history when coming from PRs.

Also try to make commits that bring the engine from one stable state to another
stable state, i.e. if your first commit has a bug that you fixed in the second
commit, try to merge them together before making your pull request. This
includes fixing build issues or typos, adding documentation, etc.

This [Git style guide](https://github.com/agis-/git-style-guide) also has some
good practices to have in mind.

### Format your commit messages with readability in mind

The way you format your commit messages is quite important to ensure that the
commit history and changelog will be easy to read and understand. A Git commit
message is formatted as a short title (first line) and an extended description
(everything after the first line and an empty separation line).

The short title is the most important part, as it is what will appear in the
changelog or in the GitHub interface unless you click the "expand" button.
Try to keep that first line under 72 characters, but you can go slightly above
if necessary to keep the sentence clear.

It should be written in English, starting with a capital letter, and usually
with a verb in imperative form. A typical bugfix would start with "Fix", while
the addition of a new feature would start with "Add". A prefix can be added to
specify the engine area affected by the commit. Some examples:

- Add C# iOS support
- Show doc tooltips when hovering properties in the theme editor
- Fix GLES3 instanced rendering color and custom data defaults
- Core: Fix `Object::has_method()` for script static methods

If your commit fixes a reported issue, please include it in the _description_
of the PR (not in the title, or the commit message) using one of the
[GitHub closing keywords](https://docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue)
such as "Fixes #1234". This will cause the issue to be closed automatically if
the PR is merged. Adding it to the commit message is easier, but adds a lot of
unnecessary updates in the issue distracting from the thread.

Here's an example of a well-formatted commit message (note how the extended
description is also manually wrapped at 80 chars for readability):

```text
Prevent French fries carbonization by fixing heat regulation

When using the French fries frying module, Blazium would not regulate the heat
and thus bring the oil bath to supercritical liquid conditions, thus causing
unwanted side effects in the physics engine.

By fixing the regulation system via an added binding to the internal feature,
this commit now ensures that Blazium will not go past the ebullition temperature
of cooking oil under normal atmospheric conditions.
```

**Note:** When using the GitHub online editor or its drag-and-drop
feature, *please* edit the commit title to something meaningful. Commits named
"Update my_file.cpp" won't be accepted.

### Document your changes

If your pull request adds methods, properties or signals that are exposed to
scripting APIs, you **must** update the class reference to document those.
This is to ensure the documentation coverage doesn't decrease as contributions
are merged.

[Update documentation XML files](https://docs.blazium.app/contributing/documentation/updating_the_class_reference.html)
Follow the style guide described in the
[Documentation writing guidelines](https://docs.blazium.app/contributing/documentation/docs_writing_guidelines.html).

If your pull request modifies parts of the code in a non-obvious way, make sure
to add comments in the code as well. This helps other people understand the
change without having to dive into the Git history.

### Write unit tests

When fixing a bug or contributing a new feature, we recommend including unit
tests in the same commit as the rest of the pull request. Unit tests are pieces
of code that compare the output to a predetermined *expected result* to detect
regressions. Tests are compiled and run on GitHub Actions for every commit and
pull request.

Pull requests that include tests are more likely to be merged, since we can have
greater confidence in them not being the target of regressions in the future.

For bugs, the unit tests should cover the functionality that was previously
broken. If done well, this ensures regressions won't appear in the future
again. For new features, the unit tests should cover the newly added
functionality, testing both the "success" and "expected failure" cases if
applicable.

Feel free to contribute standalone pull requests to add new tests or improve
existing tests as well.

See [Unit testing](https://docs.blazium.app/contributing/development/core_and_modules/unit_testing.html)
for information on writing tests in Blazium's C++ codebase.

## Contributing to Blazium translations

In the future you can contribute to Blazium translations, a link will be provide in the future for this.

Please refer to Blazium's [editor and documentation localization guidelines](https://docs.blazium.app/contributing/documentation/editor_and_docs_localization.html)

## Communicating with developers

The Blazium Engine community is largely centralized on the [Blazium Discord](https://chat.blazium.app) at this time, feel free to drop by!

To communicate with developers (e.g. to discuss a feature you want to implement
or a bug you want to fix), the following channels can be used:

- [Blazium Discord](https://chat.blazium.app): General community chat and development can all be found here.
- [Bug tracker](https://github.com/Blazium-Engine/blazium-engine/issues): If there is an
  existing issue about a topic you want to discuss, you can participate directly.
  If not, you can open a new issue. Please mind the guidelines outlined above
  for bug reporting.
- Feature Proposals should be made on the [Blazium Discord](https://chat.blazium.app) for now.
- [Blazium](https://github.com/blazium-engine/) on [X (Twitter)](https://x.com/BlaziumEngine)

Thanks for your interest in contributing!

—The Blazium development community
