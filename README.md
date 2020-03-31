# nextrelease-test 🐠

Test for [nextrelease.io](https://nextrelease.io) changelog management.

This repository is a dry run with multiple branches, PRs and tags to see if nextrelease can serve our needs.

## master

This branch is the production environment and should always be deployable. Release branches will sync new staging commits to this branch.

## staging

This branch is the working branch. New commits can only be added via PRs. On arbitrary intervals a release is branched from staging to update master.

## release-vX.Y.Z

Branches with this naming convention are used to branch a ready state of staging, bump the version number, create a tag and then merge into master.
