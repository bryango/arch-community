# Arch `community` package forks

This repo hosts forked branches of the Arch `community` repo. Branches:

- user mods are applied on `packages/*/trunk`, tracking upstream changes
- backup and alternatives are renamed `forks/*`

## strategy

- **PKGBUILD:** cloned to a local machine. There will be two remotes:
  - `origin`: tracking the fork here, and
  - `upstream`: tracking the upstream repo

  The merge from upstream is performed locally, so is the package build. Sometimes the upstream can be pulled and merged directly on the web interface, starting from the diff, e.g.
  
  > https://github.com/bryango/arch-community/compare/packages/texstudio...archlinux:svntogit-community:packages/texstudio

- **source:** kept on github, if possible. The src repo can be heavy and thus a burden to maintain locally. Most of the time the upstream can be pulled and merged directly on the web interface, starting from the diff, e.g.

  > https://github.com/bryango/texstudio/compare/master...texstudio-org:texstudio:4.5.1

  It may be possible to create a pull request and merge directly from this link. If not, see below for a detailed forking procedure. 

## texstudio

**p13n features:**

- stop re-calculating text width after rebuilds: [09a6ed](https://github.com/bryango/texstudio/commit/09a6ed5ef0fec6353b4dd8fa7eb30a12138fe928)

To sync from the upstream repo, let us consider the upstream `4.5.1` as an example:

- prepare a new `bryango` branch tracking the upstream release tree, e.g. `4.5.1-upstream`; more specifically,

  - find the release commit and checkout the corresponding tree;
  - view the files tree under this repo, i.e. change url to `bryango/...`;
  - create a new branch `4.5.1-upstream` tracking this tree in our own repo.
  
Essentially, we've fetched a copy of the upstream `4.5.1` tree in our own repo.

- merge `4.5.1-upstream` into `master` via a pull request
- tag `master` with `4.5.1` by [creating a new release](https://github.com/bryango/texstudio/releases)
- finally, update the PKGBUILD [here](https://github.com/bryango/arch-community/tree/packages/texstudio/trunk) accordingly
