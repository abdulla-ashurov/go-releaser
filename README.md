# go-releaser

## GITHUB WORKFLOWS FILE

```yml
name: Release
"on":
  push:
    branches:
      - main

permissions:
    contents: write
    packages: write

jobs:
  release:
    name: release
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          cache: npm
          node-version: 18
      - run: npm ci
      - run: npx semantic-release
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          NPM_TOKEN: ${{ secrets.NPM_TOKEN }}
```
