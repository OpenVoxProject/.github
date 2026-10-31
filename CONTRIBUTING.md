# Contribution guidelines

## Table of contents

* [Contributing](#contributing)
* [Writing proper commits - short version](#writing-proper-commits---short-version)
* [Writing proper commits - long version](#writing-proper-commits---long-version)
  * [Make separate commits for logically separate changes](#make-separate-commits-for-logically-separate-changes)
  * [Developer Certificate of Origin](#developer-certificate-of-origin)
  * [Signing commits](#signing-commits)
  * [AI-assisted contributions](#ai-assisted-contributions)
  * [Sending your patches](#sending-your-patches)
  * [Rebasing your pull request](#rebasing-your-pull-request)
  * [Update the related GitHub issue](#update-the-related-github-issue)
* [Testing](#testing)

These guidelines apply to every OpenVoxProject repository that doesn't have its own `CONTRIBUTING.md`.
The projects have grown over time based on a range of contributions from people using them.
If you follow these contributing guidelines your patch will likely make it into a release a little more quickly.

## Contributing

Please note that this project is released with a Contributor Code of Conduct.
By participating in this project you agree to abide by the [Contributor Code of Conduct](https://voxpupuli.org/coc/).

* Fork the repo.
* Create a separate branch for your change.
* We only take pull requests with passing tests, and documentation. [GitHub Actions](https://docs.github.com/en/actions) run the tests for us. You can also run them locally, as explained in [Testing](#testing).
* For Puppet code: check out [the docs](https://voxpupuli.org/docs/reviewing_pr/) we use to review a module and the [Puppet language style guide](https://docs.openvoxproject.org/openvox/latest/style_guide.html). They provide some guidance for new code that might help you before you submit a pull request.
* Add a test for your change. Only refactoring and documentation changes require no new tests. If you are adding functionality or fixing a bug, please add a test.
* Squash your commits down into logical components. You don't have to squash everything into a single commit.
* Add a `Signed-off-by` line to every commit and sign every commit with a GPG, SSH, or S/MIME key. See [Developer Certificate of Origin](#developer-certificate-of-origin) and [Signing commits](#signing-commits).
* Rebase onto the repository's current default branch, push the branch to your fork, and submit a pull request.

Please be prepared to repeat some of these steps as our contributors review your code.

If this is a Puppet Module: Also consider sending in your profile code that calls this component module as an acceptance test or provide it via an issue. This helps reviewers a lot to test your use case and prevents future regressions!

## Writing proper commits - short version

* Make commits of logical units.
* Check for unnecessary whitespace with `git diff --check` before committing.
* Commit using Unix line endings (check the settings around "crlf" in git-config(1)).
* Do not check in commented out code or unneeded files.
* The first line of the commit message should be a short description (50 characters is the soft limit, excluding ticket number(s)), and should skip the full stop.
* The body should provide a meaningful commit message, which:
  * uses the imperative, present tense: `change`, not `changed` or `changes`.
  * includes motivation for the change, and contrasts its implementation with the previous behavior.
  * Make sure that you have tests for the bug you are fixing, or feature you are adding.
  * Make sure the test suite passes after your commit.
  * When introducing a new feature, make sure it is properly documented in the README.md
  * A detailed explanation is also available at [cbea.ms/git-commit](https://cbea.ms/git-commit/)
* Include a valid `Signed-off-by` annotation as a [Developer Certificate of Origin](https://en.wikipedia.org/wiki/Developer_Certificate_of_Origin). See the [OpenVox Project DCO](https://github.com/OpenVoxProject/.github/blob/main/DCO.md)
* Sign the commit. See [Signing commits](#signing-commits).
* If an AI tool created a significant part of the commit, add an attribution trailer. See [AI-assisted contributions](#ai-assisted-contributions).

## Writing proper commits - long version

### Make separate commits for logically separate changes

Please break your commits down into logically consistent units which include new or changed tests relevant to the rest of the change.
The goal of doing this is to make the diff easier to read for whoever is reviewing your code.
In general, the easier your diff is to read, the more likely someone will be happy to review it and get it into the code base.

If you are going to refactor a piece of code, please do so as a separate commit from your feature or bug fix changes.

We also really appreciate changes that include tests to make sure the bug is not re-introduced, and that the feature is not accidentally broken.

Describe the technical detail of the change(s). If your description starts to get too long, that is a good sign that you probably need to split up your commit into more finely grained pieces.

Commits which plainly describe the things which help reviewers check the patch and future developers understand the code are much more likely to be merged in with a minimum of bike-shedding or requested changes.
Ideally, the commit message would include information, and be in a form suitable for inclusion in the release notes for the release that includes them.

Please also check that you are not introducing any trailing whitespace or other "whitespace errors".
You can do this by running `git diff --check` on your changes before you commit.

### Developer Certificate of Origin

We require a `Signed-off-by` annotation on all commits contributed to the OpenVoxProject codebase, as a [Developer Certificate of Origin](https://en.wikipedia.org/wiki/Developer_Certificate_of_Origin). See the [OpenVox Project DCO](https://github.com/OpenVoxProject/.github/blob/main/DCO.md).

If you have properly configured `user.name` and `user.email` in your `Git` configuration, `Git` includes a `-s` or `--signoff` command line option to append this line automatically to your commit message:

```sh
git commit --signoff -m 'Commit message'
```

If you already committed your changes, and you have only one commit on your branch, you can use `git commit --amend --signoff` to add a sign-off to the latest commit.
If you have more than one commit on your branch, you can instead use `git rebase` to add a sign-off to existing commits. For example, if your branch is based on the `main` branch of the `upstream` remote:

```sh
git rebase --signoff upstream/main
```

If you've already pushed commits without the proper signoff to a branch and are attempting to remediate this, then just force-push them after adding the proper annotations.

```sh
git push --force-with-lease origin <branchname>
```

### Signing commits

OpenVoxProject repositories require a verified signature on every commit, so a pull request that contains an unsigned commit can't be merged.
GitHub accepts GPG, SSH, and S/MIME signatures.
See GitHub's documentation on [signing commits](https://docs.github.com/en/authentication/managing-commit-signature-verification/signing-commits) to create a key and add it to your account.

To sign every commit automatically, configure Git once:

```sh
git config --global user.signingkey <key-id>
git config --global commit.gpgsign true
```

For an SSH key, also run `git config --global gpg.format ssh` and set `user.signingkey` to the path of your public key.

Amending or rebasing creates new commits, and those need signatures too.
With `commit.gpgsign` set, Git signs them automatically. Otherwise, pass `-S` to `git commit --amend` or `git rebase`.

### AI-assisted contributions

Read the [AI Usage Policy](https://github.com/OpenVoxProject/.github/blob/main/AI_POLICY.md) before you use AI tools on a contribution.
You are responsible for every line you submit.
If an AI tool created a significant part of a commit, add an attribution trailer to the commit message, such as `Co-authored-by:`, `Generated-by:`, or `Assisted-by:`, and mention the AI use in the pull request description.
AI tools must not add `Signed-off-by` lines, because only a human can certify the Developer Certificate of Origin.

### Sending your patches

To submit your changes via a GitHub pull request, we _highly_ recommend that you have them on a topic branch, instead of directly on your default HEAD branch (usually `main` or `master`).
It makes things much easier to keep track of, especially if you decide to work on another thing before your first change is merged in.
Maintainers have the option to rebase the source branch of a pull request, and you don't want that to happen in your HEAD branch.

GitHub has some pretty good [general documentation](https://docs.github.com/) on using their site.
They also have documentation on [creating pull requests](https://docs.github.com/en/pull-requests/how-tos/create-pull-requests/creating-a-pull-request).

After you push your topic branch to your fork, GitHub shows a **Compare & pull request** button on the repository page. Click it to open a pull request against the OpenVoxProject repository.

When you have addressed a review comment, reply in its thread saying what you changed. Leave resolving the thread to the reviewer who opened it; maintainers may resolve stale threads when they merge.

### Rebasing your pull request

If your branch conflicts with the repository's default branch, or you need a change that landed there after you created your branch, rebase your branch instead of merging the default branch into it.
Maintainers don't squash pull requests when they merge them, so the commits on your branch become part of the project history as they are.

```sh
git fetch upstream
git rebase upstream/main
```

Here `upstream` is the remote that points at the OpenVoxProject repository. Replace `main` with the repository's default branch if it's different.
Git stops at each commit that conflicts. Fix the conflicting files, then run `git add <file>` and `git rebase --continue`.
GitHub's guide to [resolving merge conflicts after a Git rebase](https://docs.github.com/en/get-started/using-git/resolving-merge-conflicts-after-a-git-rebase) covers this in more detail.

When the rebase finishes, update your pull request:

```sh
git push --force-with-lease origin <branchname>
```

`--force-with-lease` refuses to overwrite your branch if it has commits you haven't fetched, such as a suggestion a reviewer committed from the GitHub UI.

### Update the related GitHub issue

If there is a GitHub issue associated with your change, reference it in the pull request description, for example `Fixes #123`.
GitHub links the two, and closes the issue when the pull request is merged.

## Testing

Most repositories run their tests in GitHub Actions.
You can always check `.github/workflows/` to see what the CI does, and many repositories explain how to run the tests locally in their README.

* **Puppet modules:** see [How to run the test suite](https://voxpupuli.org/docs/how_to_run_tests/).
* **Ruby projects:** most use [rspec](https://rspec.info/). Run `bundle install`, then list the available rake tasks with `bundle exec rake --tasks`. Usually there's a task named `test` or `spec`. Our goal is that running `bundle exec rake` always executes the whole test matrix. If this isn't yet the case for a project you're working on, please open an issue in that repository.
* **Clojure projects:** openvox-server and openvoxdb use [Leiningen](https://leiningen.org/) (`lein test`). Some of their tests need extra services, such as a PostgreSQL database, so check the README or the CI workflow first.
