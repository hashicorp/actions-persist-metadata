# Persist Metadata Action

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
