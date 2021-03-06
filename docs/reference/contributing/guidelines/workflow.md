## Workflow

All code changes and additions to Mbed OS are handled through GitHub. If you want to contribute, either by adding features or by fixing bugs, please follow the guidelines for [new features](#features) and [bugs](#reporting-bugs). In both cases, please follow the [code style guide and GitHub pull request guidelines](../reference/style.html).

### Mbed OS maintainers

The maintainers are a small group of Mbed OS engineers who are responsible for the Mbed OS codebase. Their primary role is to progress contributions, both internal and external, from the initial pull request state through to released code.

Responsibilities:

1. Ensure the relevant stakeholders review pull requests.
1. Guide contributors both technically and procedurally.
1. Run pull requests through the CI systems.
1. Put label version.
1. Merge pull requests into the requested branches.
1. Make periodic patch and feature releases.

The current maintainers are:

- [Anna Bridge](https://os.mbed.com/users/AnnaBridge).
- [Martin Kojtal](https://os.mbed.com/users/Kojto).
- [Shrikant Tudavekar](https://os.mbed.com/users/shrikant1213).
- [Nir Sonnenschein](https://os.mbed.com/users/nirs).
- [Cruz Monrreal](https://os.mbed.com/users/CM2).
- [Kevin Bracey](https://os.mbed.com/users/kjbracey).

### Contributions

Before contributing an enhancement (new feature, new port and so on), please [discuss it on the forums](https://os.mbed.com/forum/bugs-suggestions/) to avoid duplication of work, as we or others might be working on a related feature.

We can only accept contributions through GitHub if you create a pull request from forked versions of our repositories. This allows us to review the contributions in an easy-to-use and reliable way, under public scrutiny.

For security purposes, we require our GitHub contributors to use two-factor authentication on their GitHub accounts. Two-factor authentication adds a layer of security, which reduces the risk of your account being hacked. To enable two-factor authentication, please see [GitHub’s instructions](https://help.github.com/articles/configuring-two-factor-authentication/).

Please create separate pull requests for each concern; each pull request needs a clear unity of purpose. In particular, separate code formatting and style changes from functional changes. This makes each pull request’s true contribution clearer, so review is quicker and easier.

#### Reporting bugs

You can submit Mbed OS bugs [on the forums](https://os.mbed.com/forum/bugs-suggestions/) or directly [on GitHub](https://github.com/ARMmbed/mbed-os)

The bug report should be reproducible (fails for others) and specific (where and how it fails). We will close insufficient bug reports.

We copy issues reported on GitHub to our internal tracker and regularly triage them.

### Guidelines for GitHub pull requests

Pull requests on GitHub have to meet the following requirements to keep the code and commit history clean:

- Commits should always contain a proper description of their content. Start with a concise and sensible one-line description. Then, elaborate on reasoning of the choices made, descriptions for reviewers and other information that might otherwise be lost.
- You should always write commits to allow publication, so they can never contain confidential information, reference private documents, links to intranet locations or rude language.
- Each commit should be the minimum self-contained commit for a change. A commit should always result in a new state that is again in a compilable state. You should (if possible) split large changes into logical smaller commits that help reviewers follow the reasoning behind the full change.
- Commits and pull request titles should follow [Chris Beam’s seven rules of great commit messages](http://chris.beams.io/posts/git-commit#seven-rules):
	1. Separate the subject from the body with a blank line.
	1. Limit the subject line to 72 characters (note that this is a deviation from Beam's standard).
	1. Capitalize the subject line.
	1. Do not end the subject line with a period.
	1. Use the imperative mood in the subject line.
	1. Wrap the body at 72 characters.
	1. Use the body to explain _what_ and _why_ vs _how_.
- Because we use GitHub, special commit tags that other projects may use, such as “Reviewed-by”, or “Signed-off-by”, are redundant and should be omitted. GitHub tracks who reviewed what and when.
- Prefixing your commit message with a domain is acceptable, and we recommend doing so when it makes sense. However, prefixing one's domain with the name of the repo is not useful. For example, making a commit entitled "mbed-drivers: Fix doppelwidget frobulation" to the `mbed-drivers` repo is not acceptable because it is already understood that the commit applies to `mbed-drivers`. Renaming the commit to "doppelwidget: Fix frobulation" would be better, if we presume that "doppelwidget" is a meaningful domain for changes, because it communicates that the change applies to the doppelwidget area of `mbed-drivers`.
- All new features and enhancements require documentation, tests and user guides for us to accept them. Please link each pull request to all relevant documentation and test pull requests.
- Avoid merging commmits. (Always rebase when possible.)
- Comment in the pull request on every change (rebase or new commits). This helps reviewers to be up to date with changes
- Pull requests should fix a bug, add a feature or refactor.

#### Release versioning

You can find Mbed OS versioning at [How We Release Arm Mbed OS](../introduction/release-process.html).

### Pull request categories

#### Bug fixes

Every bug fix should contain a test to verify results prior to and after the pull request.

#### Changes and additions

Backward compatible changes (such as refactoring and enhancements) or new target additions can go into patch and feature releases. We only consider features and new functionality additions for feature releases.

#### Features

We initially implement new features on separate branches in the Mbed OS repository. Mbed OS maintainers create the new branches by following the naming convention: "feature-" prefix.

Each feature has a tech lead. This person is responsible for:

- Rebasing often to track master development.
- Reviewing any addition to the feature branch (approval required by the feature tech lead or another assigned person).

### Pull request types

We consider the following pull request types.

#### Fix

A bug fix is a backward-compatible internal change that fixes incorrect behavior.

Release: patch

#### Refactor

Refactors are intended for feature releases, if they are not fixing specific issues, because they can introduce new issues.

Release: feature

#### Target update

Updating target implementation (adding a new target or updating already supported target) is a change for a patch release.

Release: patch

#### Feature

New features target feature releases. A new feature can only be integrated if the feature supports most of the targets (if it requires new target HAL implementation).

We consider adding a new functionality to be a feature. It does not matter if it is C++, C or Python.

Release: feature

#### Documentation update

Documentation updates include changes to markdown files or Doxygen documentation (comment-only changes).

Release: patch

#### Test update

Test updates include updates to a new test unit or test case.

Release: patch

#### Breaking change

A breaking change is any change that results in breaking user space. It should have strong justification for us to consider it. Often, such changes can be backward compatible, for example, deprecating the old functionality and introducing the new replacement.

Release: major

### Pull request template

Below is a good example of a pull request:

```
Fix deep sleep locking bug

# Description

Fix problems that could leave deep sleep locked unintentionally, along with adding tests to verify this behavior is fixed.

Tested locally with two targets and all toolchains.

You can see test results [here](just an example).

# Pull request type

    [X] Fix
    [ ] Refactor
    [ ] Target update
    [ ] Functionality change
    [ ] Docs update
    [ ] Test update
    [ ] Breaking change

```

### GitHub pull requests workflow

Each pull request goes through the following workflow:

<span class="images">![](https://s3-us-west-2.amazonaws.com/mbed-os-docs-images/Workflow.png)<span>The workflow of merging a pull request</span></span>

### Pull request states

The Mbed OS maintainers add labels to a pull request that represent the pull request workflow states. The Mbed OS maintainers are responsible for moving pull requests through the workflow states.

Each state is time boxed. In most cases, this is sufficient time to move to another state. The pull request can be closed if no update is provided within the time frame.

If a pull request is idle for more than two weeks, it will be closed. The author or the maintainer can reopen it at any time.

#### Reviews

All pull requests must be reviewed. The Arm Mbed CI bot determines the most suitable person to review the pull request and tags that person accordingly.

Github dismisses a reviewer's status after any change to the pull request commit history (such as adding a new commit or rebasing). Smaller changes, such as documentation edits or rebases on top of latest master, only require additional review by maintainers. Their approval is sufficient because a team assigned as a reviewer already approved the pull request.

Label: `needs: review`
Time: 3 days for reviewers to leave feedback after the maintainers add the "needs: review" label.

#### The CI (Continuous Integration) testing

There are many [CI systems available](../contributing/guidelines/ci.html) for testing Mbed OS pull requests and braches. Which CI tests we run against a particular pull request depends on the effect that pull request has on the code base. Irrespective of which CI tests run, Mbed OS has an all green policy, meaning that all the CI jobs that are triggered must pass before we merge the pull request.

Label: `needs: CI`
Time: 1 day for CI to complete and report back results.

#### Work needed

A pull request in the work needed state requires additional work due to failed tests, or rework as a result of the review. If a pull request is in this state, then our maintainers request changes from the pull request author.

Label: `needs: work`
Time: 3 days for the pull request author to action the review comments.

#### Ready for integration

Maintainers merge pull requests during the internal gatekeeping meetings that occur three times a week. They can merge straightforward pull requests immediately.

Label: `Ready for merge`
Time: 2 days

#### Releases

When we merge a pull request that we will publish in a patch release, we tag the pull request with the specific patch release version. This is the release in which we first publish this pull request. For patch releases, we allow only bug fixes, new targets and enhancements to existing functionality. New features only go in feature releases.

The release tag has the following format:

*release-version: 5.f.p* - Where `f` is the feature release and `p` the patch release.

### Additional labels

We use many other labels to summarize the scope and effect of the changes.

- *needs: preceding PR* - This pull request cannot yet be merged because it has a dependency on another pull request that needs to merge first.
- *DO NOT MERGE* - This pull request contains changes that may be in a draft state and submitted purely for review, or may contain breaking changes that have not been considered.
- *devices: 'name'* - This pull request specifically affects the named device(s).
- *component: 'name'* - This pull request specifically affects the named component. Component names follow the structure of Mbed OS (`ble`, `storage`, `tls` and so on).
- *rollup PR* - This pull request is ready for CI testing, but will instead be brought into a rollup pull request to test multiple pull requests at once.

The following labels summarize the scope of the pull request.

- *scope: bug-fix*.
- *scope: feature*.
- *scope: new-target*

#### Rollup pull requests

When Mbed OS has many small, orthogonal pull requests waiting for CI testing to start, maintainers can bundle multiple pull requests into a single pull request referred to as a rollup pull request. Once this rollup pull request passes CI testing and merges, the bundled pull requests used to build the rollup pull request also automatically merge.

By the time the maintainers select a pull request to be integrated into a rollup pull request, it already has a release label and is waiting to start CI testing. Each bundled pull request gains a *rollup PR* label. Once the rollup pull request is generated, a comment is added to the bundled pull request, informing the bundled pull request's author.

If a rollup pull request fails CI testing, maintainers identify the problem bundled pull requests, update their statuses and provide additional guidance on what went wrong. Critically, if a bundled pull request is updated *while* it is already in a rollup pull request, and the rollup pull request passes CI and merges, the updated bundled pull request *does not* automatically merge.

##### How it works

Rollup pull requests use the same process as pull requests merging into master, except that pull requests are merged into a rebased temporary branch. All pull requests with the *rollup PR* label are cloned and merged into the temporary branch. If no merge conflicts arise, a pull request is opened with the temporary branch. Once the rollup pull request merges, all other pull requests that went into building the rollup pull request are also _marked_ as merged because their contents are now part of master.

Rollup pull requests are a solution to two types of problem: CI testing duration and semantic conflict problem. Rollup pull requests drastically lower the time to test many pull requests at once. Instead of putting many pull requests through CI, only one goes through testing. This lowers the load on the CI infrastructure and helps close pull requests sooner. The second, more subtle, problem that rollup pull requests solve is the case in which two pull requests pass testing on their own, but as soon as they join together, the way they interact with each other causes tests to fail. For more details, please see [this example](https://bors.tech/essay/2017/02/02/pitch).

A special case occurs when a bundled pull request is updated while its rollup pull request undergoes testing. When a pull request is bundled into a rollup pull request, its commits become a part of the rollup pull request at the time that the rollup pull request source branch is created. If you update the bundled pull requests, its commit history is no longer exactly mirrored in the rollup pull request. If this situation arises, the bundled pull request that was updated _is not_ automatically marked as merged because all changes of the updated bundled pull request were not present in the merged rollup pull request. Maintainers treat the updated, previously bundled pull request as if it were on its own all along.
