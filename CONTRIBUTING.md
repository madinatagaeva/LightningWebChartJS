# Contributing to Lightning Web Components

We want to encourage the developer community to contribute to Lightning Web Components. This guide has instructions to install, build, test and contribute to the framework.

- [Requirements](#requirements)
- [Installation](#installation)
- [Building LWC](#building-lwc)
- [Testing](#testing)
- [Git Workflow](#git-workflow)
-  madina

Before you start, familiarize yourself with [Lightning Web Components](https://lwc.dev/guide/introduction).

## Requirements

- [Node](https://nodejs.org/) >= 10
- [NPM](https://www.npmjs.com// >= 6.14

## Installation

### 1) Download the repository

```bash
git clone git@github.com:SalesforceLabs/LightningWebChartJS.git
```

### 2) Install Dependencies

```bash
npm install
```

## Testing

### Unit Testing lwcc

When developing lwcc, utilize [sfdx-lwc-jest](https://github.com/salesforce/sfdx-lwc-jest/) unit testing to provide test coverage for new functionality. To run the jest tests use the following command from the root directory:

```bash
npm run test:unit
```

Additionally, the testing can be started in 'watch' mode which allows for automatic test re-runs on save:

```bash
npm run test:unit:watch
```

To execute a particular test, use the following command:

```bash
npm run test:unit <path_to_test>
```

### Apex Testing lwcc

The apex tests are run the following command from the root directory:

```bash
npm run test:apex
```

Additionally, to have the related code coverage, use the following command:

```bash
npm run test:apex:coverage
```

## Editor Configurations

Configuring your editor to use our lint and code style rules will make the code review process delightful!

### Code formatting

[Prettier](https://prettier.io/) is a code formatter used to ensure consistent formatting across your code base. To use Prettier with Visual Studio Code, install [this extension](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) from the Visual Studio Code Marketplace. The [.prettierignore](/.prettierignore) and [.prettierrc](/.prettierrc) files are provided as part of this repository to control the behavior of the Prettier formatter.

### Code linting

[ESLint](https://eslint.org/) is a popular JavaScript linting tool used to identify stylistic errors and erroneous constructs. To use ESLint with Visual Studio Code, install [this extension](https://marketplace.visualstudio.com/items?itemName=salesforce.salesforcedx-vscode-lwc) from the Visual Studio Code Marketplace. The [.eslintignore](/.eslintignore) file is provided as part of this repository to exclude specific files from the linting process in the context of Lightning Web Components development.

## Git Workflow

The process of submitting a pull request is fairly straightforward and
generally follows the same pattern each time:

1. [Fork the LWC repo](#fork-the-lwc-repo)
1. [Create a feature branch](#create-a-feature-branch)
1. [Make your changes](#make-your-changes)
1. [Rebase](#rebase)
1. [Check your submission](#check-your-submission)
1. [Create a pull request](#create-a-pull-request)
1. [Update the pull request](#update-the-pull-request)

### Fork the LWC repo

[Fork][fork-a-repo] the [SalesforceLabs/LightningWebChartJS](https://github.com/SalesforceLabs/LightningWebChartJS) repo. Clone your fork in your local workspace and [configure][configuring-a-remote-for-a-fork] your remote repository settings.

```bash
git clone git@github.com:<YOUR-USERNAME>/LightningWebChartJS.git
cd lwcc
git remote add upstream git@github.com:SalesforceLabs/LightningWebChartJS.git
```

### Create a feature branch

```bash
git checkout master
git pull origin master
git checkout -b feature/<name-of-the-feature>
```

### Make your changes

Modify the files, build, test, lint and eventually commit your code using the following command:

```bash
git add <path/to/file/to/commit>
git commit ...
git push origin feature/<name-of-the-feature>
```

Commit your changes using a descriptive commit message

The above commands will commit the files into your feature branch. You can keep
pushing new changes into the same branch until you are ready to create a pull
request.

### Rebase

Sometimes your feature branch will get stale with respect to the master branch,
and it will require a rebase. The following steps can help:

```bash
git checkout master
git pull upstream master
git checkout feature/<name-of-the-feature>
git rebase upstream/master
```

_note: If no conflicts arise, these commands will ensure that your changes are applied on top of the master branch. Any conflicts will have to be manually resolved._

### Check your submission

#### Lint your changes

```bash
npm run lint
```

The above command may display lint issues that are unrelated to your changes.
The recommended way to avoid lint issues is to [configure your
editor][eslint-integrations] to warn you in real time as you edit the file.

Fixing all existing lint issues is a tedious task so please pitch in by fixing
the ones related to the files you make changes to!

#### Run tests

Test your change by running the unit tests and integration tests. Instructions [here](#testing).

### Create a pull request

If you've never created a pull request before, follow [these
instructions][creating-a-pull-request]. Pull request samples can be found [here](https://github.com/salesforce/lwc/pulls)

### Update the pull request

```sh
git fetch origin
git rebase origin/${base_branch}

# If there were no merge conflicts in the rebase
git push origin ${feature_branch}

# If there was a merge conflict that was resolved
git push origin ${feature_branch} --force
```

_note: If more changes are needed as part of the pull request, just keep committing and pushing your feature branch as described above and the pull request will automatically update._

CI validates prettifying, linting and tests

[fork-a-repo]: https://help.github.com/en/articles/fork-a-repo
[configuring-a-remote-for-a-fork]: https://help.github.com/en/articles/configuring-a-remote-for-a-fork
[setup-github-ssh]: https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/
[creating-a-pull-request]: https://help.github.com/articles/creating-a-pull-request/
[eslint-integrations]: http://eslint.org/docs/user-guide/integrations
