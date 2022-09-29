# Persist Metadata Action

Persists metadata provided by Common Release Tooling

_This is intended for internal HashiCorp use only_

## Usage

Add the following to your workflow in the `jobs` stanza:

```
jobs:
  persist-metadata:
    runs-on: ubuntu-latest
    steps:
      - name: Persist metadata
        uses: hashicorp/actions-persist-metadata@v1
```
