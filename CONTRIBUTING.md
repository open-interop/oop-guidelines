# Contributing

When contributing to this repository, please first discuss the change you wish to make via issue, email, or any other method with the owners of this repository before making a change.

Please note we have a code of conduct, please follow it in all your interactions with the project.

## Pull request process

1. Ensure any install or build dependencies are removed before the end of the layer when doing a build
2. Update the README.md with details of changes to the interface, this includes new environment variables, exposed ports, useful file locations and container parameters
3. Community pull requests should only be against `develop` and follow our **Git workflow** guidelines as defined below
4. You may merge the Pull Request in once you have the sign-off of two other developers, or if you do not have permission to do that, you may request the second reviewer to merge it for you

## Style Guide

All pull requests MUST adhere to the [Conventional Commits specification](https://conventionalcommits.org/)

## Git workflow

- There should be two protected branches in the repository `main` and `develop`.

- `main` is the main branch where the source code of HEAD always reflects a production-ready state.

- `develop` is the main branch where the source code of HEAD always reflects a state with the latest delivered development changes for the next release.

- Any automated nightly builds are built from `develop`.

### Branching

There are three different types of 'supporting' branches that you should use.

#### Feature branches

- May branch from: `develop`

- Must merge back into: ` develop`

- Branch naming convention:
    
    - Branch names should start with `feature/` to support git search and auto-completion.
    
    - e.g. `feature/branch-name`
    
    - Do not name your branch based on the following patterns `main`, `develop`, `release-*`, `release/*`, `hotfix/*`, or `hotfix-*`
    
    - Branch names should never start with numbers.

- Check in your feature branches so that code reviews can be undertaken when merging back into `develop`. Use the Github pull request pattern.

#### Release branches

- May branch from: `develop`

- Must merge back into: ` develop` and `main`

- Branch naming convention:
    
    - Branch names should start with `release/` to support git search and auto-completion.
    
    - e.g. `release/branch-name`
    
    - Do not name your branch based on the following patterns `main`, `develop`, `feature-*`, `feature/*`, `hotfix/*`, or `hotfix-*`
    
    - Branch names should never start with numbers.

- Release branches should be used to prepare the codebase for release by updating release metadata e.g. version numbers

- You should only be writing bug fixes in release branches, not features

- Version numbers should only be incremented/assigned at the time of branching the release branch. Not in `develop`.

- When merging `release` into `main` you should create a tag on main with the release version.

- Release branches should be merged back into `develop` after being merged into `main`. There will be conflicts...

- Remove `release/` branches when you're done with them.

#### Hotfix branches

- May branch from: `main`

- Must merge back into: ` develop` and `main`

- Branch naming convention:

    - Branch names should start with `hotfix/` to support git search and auto-completion.
    
    - e.g. `hotfix/branch-name`
    
    - Do not name your branch based on the following patterns `main`, `develop`, `feature-*`, `feature/*`, `release/*`, or `release-*`
    
    - Branch names should never start with numbers.
    
- Only for critical production bugs.

- Branch from a tag off of `main`. Once complete, merge back into `main` and tag the release. Then merge back into `develop`.

- **Except** if a `release/` branch already exists. Merge the hotfix into the `release/` branch and **not** `develop`.

- Remove `hotfix/` branches when you're done with them.

See the [Git branching model diagram](https://nvie.com/files/Git-branching-model.pdf) by Vincent Driessen that supports the above described workflow.

### Tagging

- When a branch is merged into `main` a tag with the version number should be created against `main`. Use SemVer.

### Merging

- **Do not rewrite published history.** The repository's history is valuable in its own right and it is very important to be able to tell what actually happened. Altering published history is a common source of problems for anyone working on the project.

- However, there are cases where rewriting history is legitimate. These are when:
  
    - You are the only one working on a branch and it is not one of the protected branches.
    
    - You want to tidy up your branch (e.g. squash commits) and/or rebase it onto the `develop` in order to merge it later.
    
    Never rewrite the history of the "main" branch or any other special branches (ie. used by production or CI servers).

- Keep the history clean and simple. Just before you merge your branch:

  - Make sure it conforms to the style guide and perform any needed actions if it doesn't (squash/reorder commits, reword messages etc.)
  
  - Rebase it onto the branch it's going to be merged to:
    
    ```
    [my-branch] $ git fetch
    [my-branch] $ git rebase origin/develop
    # then merge
    ```
    
    This results in a branch that can be applied directly to the end of the `main` branch and results in a very simple history.

### Misc

- *Be consistent*. This is related to the workflow but also expands to things like commit messages, branch names and tags. Having a consistent style throughout the repository makes it easy to understand what is going on by looking at the log, a commit message etc.

