# workflows
Reusable CI/CD pipelines for wasco-dev Rust WebAssembly component repositories.

## CI
The CI pipeline runs quality checks on a Rust WebAssembly component. To use the general CI pipeline, add this file to your repository.

**File:** `.github/workflows/ci.yml`
```yaml
on:
  pull_request:
  repository_dispatch:
      types: ["workflows-updated"]
  push:
    branches: ["main"]

jobs:
  ci:
    uses: wasco-dev/workflows/.github/workflows/ci.yml@main
```

## CD
The CD pipeline pushes your Rust WebAssembly component to GitHub Container Registry and an Azure Registry. To use the general CD pipeline, add this file to your repository.

**File:** `.github/workflows/cd.yml`
```yaml
on:
  workflow_dispatch:
  push:
    branches: ["main"]

jobs:
  cd:
    uses: wasco-dev/workflows/.github/workflows/cd.yml@main
    permissions:
      contents: read
      packages: write
      attestations: write
      id-token: write
    secrets: inherit
```

## Actions
### Install wkg
You can install [wkg](https://github.com/bytecodealliance/wasm-pkg-tools) into your own pipeline jobs by using:
```yaml
- uses: wasco-dev/workflows/.github/actions/install-wkg@main
```
By default this uses version `0.15.0` of wkg from `https://github.com/bytecodealliance/wasm-pkg-tools/releases/download/v0.15.0/wkg-x86_64-unknown-linux-gnu`, this version can be changed like so:
```yaml
- uses: wasco-dev/workflows/.github/actions/install-wkg@main
  with:
    version: "0.16.0"
```
