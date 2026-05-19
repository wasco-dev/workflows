# workflows
Reusable CI/CD pipelines for wasco-dev Rust WebAssembly component repositories.

## CI
The CI pipeline runs quality checks on a Rust WebAssembly component. To use the general CI pipeline, add this file to your repository.

**File:** `.github/workflows/ci.yml`
```yaml
on:
  pull_request:
  push:
    branches: ["main"]

jobs:
  ci:
    uses: wasco-dev/workflows/.github/workflows/ci.yml@main
```

## CD
The CD pipeline updates the GitHub of a Rust WebAssembly component. To use the general CD pipeline, add this file to your repository.

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
