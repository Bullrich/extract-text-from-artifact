# Extract text from artifact

Action to simplify [the example from the example in GitHub with `workflow_run` event](https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows#using-data-from-the-triggering-workflow).

Needs to be called by the `workflow_run` event.


## Installation

```yaml
name: Use the data

on:
  workflow_run:
    workflows: [PR-Triggered-Event]
    types:
      - completed

jobs:
  download:
    runs-on: ubuntu-latest
    steps:
      - name: Extract content of artifact
        id: number
        uses: Bullrich/extract-text-from-artifact@main
        with:
          artifact-name: pr_number
      - run: echo "The PR that triggered the workflow is \#$NUMBER"
        env:
          NUMBER: ${{ steps.number.outputs.content }}
```
