# [mdtmpl](https://github.com/FalcoSuessgott/mdtmpl) action
Github Action running [mdtmpl](https://github.com/FalcoSuessgott/mdtmpl)

# Usage

```yaml
name: mdtmpl

on:
  push:
    branches:
      - 'main'
      - 'master'

# required to commit the specified output file back to the branch
permissions:
    contents: write

jobs:
  mdtmpl:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4
      - uses: FalcoSuessgott/mdtmpl-action@v1
        with:
          # specify the template file (default: README.md.tmpl)
          template-file: README.md.tmpl
          # specify the output file (default: README.md)
          output-file:  README.md

        # this step commits the output-file back to the repo. Check: https://github.com/stefanzweifel/git-auto-commit-action
      - uses: stefanzweifel/git-auto-commit-action@v4
        with:
          commit_message: "docs(vars): update README generated with mdtmpl"
```