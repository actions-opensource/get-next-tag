# get-next-tag

# Example

```yml
name: Create Tag And Release
on:
  push:
    branches:
      - master
    paths-ignore:
      - 'docs/**'
      - '*.md'
      - 'LICENSE'
jobs:
  createTagAndRelease:
    permissions: write-all
    runs-on: ubuntu-latest
    name: Create Tag And Release
    outputs:
      tagName: ${{ steps.setTag.outputs.tagName }}
    steps:
      - name: checkout
        uses: actions/checkout@v3
        
      - name: Set Tag Name
        id: setTag
        uses: actions-opensource/get-next-tag@v1

      - name: Echo Version
        run: |
          echo "${{ env.newTagName }}"
          echo "${{ steps.setTag.outputs.tagName }}"
```
