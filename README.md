# Persist Metadata Action
[![Heimdall](https://heimdall.hashicorp.services/api/v1/assets/actions-persist-metadata/badge.svg?key=822b0e2cf3c960db813d2c5a2d6dbfde76d040feb756cc7cb98e049c449a32f5)](https://heimdall.hashicorp.services/site/assets/actions-persist-metadata) [![CI](https://github.com/hashicorp/actions-persist-metadata/actions/workflows/lint.yml/badge.svg)](https://github.com/hashicorp/actions-persist-metadata/actions/workflows/lint.yml)

Persists metadata provided by Common Release Tooling

_This is intended for internal HashiCorp use only_

## Usage

Add the following to your workflow in the `jobs` stanza:

```
on:
  repository_dispatch:
    types: "persist-metadata"

jobs:
  persist-metadata:
    runs-on: ubuntu-latest
    steps:
      - name: Persist metadata
        uses: hashicorp/actions-persist-metadata@v1
```

### In reusuable workflows

If your workflow is shared between Common Release Tooling workflows and other product specific
workflows using [reusable
workflows](https://docs.github.com/en/actions/using-workflows/reusing-workflows) you can add a
conditional to skip the job when it is not required.

```
on: workflow_call

jobs:
  persist-metadata:
    # Common-release-tooling uses `repository_dispatch` to run workflows
    if: github.event_name == 'repository_dispatch'
    runs-on: ubuntu-latest
    steps:
      - name: Persist metadata
        uses: hashicorp/actions-persist-metadata@v1

```
