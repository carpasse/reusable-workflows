# reusable-workflows
 Collection of reusable workflows for my GitHub actions

## 🔗 Useful links

- [Reusing workflows](https://docs.github.com/en/actions/using-workflows/reusing-workflows) in GitHub Docs
- [How to start using reusable workflows with GitHub Actions](https://github.blog/2022-02-10-using-reusable-workflows-github-actions/)
  
## 📁 Workflows

### [release.yml](.github/workflows/release.yml)
This workflow is used to create a release and publish it to [NPM public registry](https://www.npmjs.com/). It uses the [semantic-release](https://www.npmjs.com/package/semantic-release)

#### 📝 Usage

```yaml
name: Release
on:
  push:
    branches: ['main', 'beta', 'alpha']
jobs:
  release:
    uses: carpasse/reusable-workflows/.github/workflows/release.yml@v1
    secrets:
      NPM_TOKEN: ${{ secrets.NPM_TOKEN }}
```

### [validation.yml](.github/workflows/validation.yml)
This workflow is used to validate the codebase. It runs `npm ci`, `npm build` (if present), `npm run lint:ci`, and `npm run test`. On Node versions 18, 20 and 21.

#### 📝 Usage

```yaml
name: Validation
on: [pull_request]
jobs:
  validation:
    uses: carpasse/reusable-workflows/.github/workflows/validation.yml@v1
```

### [commitlint.yml](.github/workflows/commitlint.yml)
This workflow is used to validate the commit messages. It runs setups node 20 and runs commitlint on all the messages of the Pull Request.

#### 📝 Usage

```yaml
name: Lint Commit Messages
on: [pull_request]
jobs:
  commitlint:
    uses: carpasse/reusable-workflows/.github/workflows/lintCommitMessages.yml@v1
```

## 📄 License

This repository is licensed under the [MIT License](LICENSE)

## 🙏 Credits
This repository is inspired by [inigomarquinez](https://github.com/inigomarquinez)'s [reusable-workflows](https://github.com/inigomarquinez/reusable-workflows) repository.
