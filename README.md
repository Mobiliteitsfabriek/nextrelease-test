# 🏗 Release management playground

This repository is a playground with multiple branches, PRs and tags to test out the release flow. You can play around by creating PRs to staging and publishing release drafts.

## 🌊 Release flow

### Adding changes

1. Create a new branch from staging.
1. Make changes.
1. Push your branch and create a PR into staging.
1. Optionally add a label: `dependency` and `bug` labels will be placed in their own category in the release notes.
1. Merge your branch into staging. A [GitHub action](.github/workflow/release-drafter.yml) will kick off.
1. Rinse and repeat as you like. See how the release draft keeps udating in https://github.com/reisbalans/nextrelease-test/releases.

### Updating the version

1. Once you feel it is time for a new release, create a new branch from staging to bump the version.
1. Run `yarn bump:minor` in the project root. (or `yarn bump:patch`, `yarn bump:major` for other semver updates).
1. Commit, push and merge the changes.
1. Go to https://github.com/reisbalans/nextrelease-test/releases.
1. Check that the draft release looks in order. The version numbers should match your bump changes.
1. Click 'Edit', then 'Publish release'. A [GitHub action](.github/workflow/release-master-pr.yml) will kick off.
1. Wait a little for the action to finish, then check the PR to master that was created.

Note that it is assumed a release is always merged into master. Should a release PR be closed without merging, the next one will not include all changes but just those from the latest release. (For example when a patch is requested on reviewing the release PR). In this case you should manually add a link to the other included release(s) in the PR body.

## 🎋 Branches

### master

This branch is the production environment and should always be deployable.

### staging

This branch is the working branch. New commits can only be added via PRs. On arbitrary intervals a release is branched from staging.

### master-release-vX.Y.Z

A branch with this naming pattern is automatically generated when a release draft is published. It is branched from that release tag and set to be merged into master.

## ⚙️ Configuration

The current setup uses the following tools:

- [semver](https://semver.org/)
- [Release Drafter](https://github.com/release-drafter/release-drafter)
- [GitHub Actions](https://help.github.com/en/actions)
- [GitHub Releases](https://help.github.com/en/github/administering-a-repository/managing-releases-in-a-repository)
- [Yarn version](https://classic.yarnpkg.com/en/docs/cli/version/)
