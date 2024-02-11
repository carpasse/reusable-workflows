# reusable-workflows
 Collection of reusable workflows for my GitHub actions

## 🔗 Useful links

- [Reusing workflows](https://docs.github.com/en/actions/using-workflows/reusing-workflows) in GitHub Docs
- [How to start using reusable workflows with GitHub Actions](https://github.blog/2022-02-10-using-reusable-workflows-github-actions/)
  
## 📁 Workflows

### [publishToNPM.yml](.github/workflows/publishToNPM.yml)
This workflow is used to build the source code and publish it to [NPM public registry](https://www.npmjs.com/). It sets up node 20 and runs the build command and the license-check command with the `--if-present` flag. It uses the [semantic-release](https://www.npmjs.com/package/semantic-release) to do the release.

#### 📝 Usage

```yaml
name: Publish to NPM
on:
  push:
    branches: ['master', 'beta', 'alpha']
jobs:
  release:
    uses: carpasse/reusable-workflows/.github/workflows/publishToNPM.yml@v1
    secrets:
      NPM_TOKEN: ${{ secrets.NPM_TOKEN }}
```

### [runTests.yml](.github/workflows/runTests.yml)
This workflow is used to run the tests of the codebase. On Node versions 18, 20 and 21.

#### 📝 Usage

```yaml
name: Run tests
on: [pull_request]
jobs:
  validation:
    uses: carpasse/reusable-workflows/.github/workflows/runTests.yml@v1
```

### [validateCodebase.yml](.github/workflows/validateCodebase.yml)
This workflow is used to build and lint the codebase. It sets up node 20 and runs the linting and build commands (with the `--if-present` flag).

#### 📝 Usage

```yaml
name: Validate Codebase
on: [pull_request]
jobs:
  validation:
    uses: carpasse/reusable-workflows/.github/workflows/validateCodebase.yml@v1
```

### [validateCommits.yml](.github/workflows/validateCommits.yml)
This workflow is used to validate the commit messages. It uses the [wagoid/commitlint-github-action@5](https://github.com/wagoid/commitlint-github-action/tree/v5/) action.

#### 📝 Usage

```yaml
name: Validate commit messages
on: [pull_request]
jobs:
  commitlint:
    uses: carpasse/reusable-workflows/.github/workflows/validateCommits.yml@v1
```

## 📄 License

This repository is licensed under the [MIT License](LICENSE)

## 🙏 Credits
This repository is inspired by [inigomarquinez](https://github.com/inigomarquinez)'s [reusable-workflows](https://github.com/inigomarquinez/reusable-workflows) repository.
