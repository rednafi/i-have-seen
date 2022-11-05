# i-have-seen

Workflow to automatically add a comment when an issue or a pull request is opened.

## Usage

### Add an issue comment

```yml
name: CI

on:
  issues:
    types:
      - opened

jobs:
  add-issue-comment:
    uses: rednafi/i-have-seen/.github/workflows/seen.yml@v1
    with:
      message: |
        Simple comment **works**.
         This is another ~line~.

      where: "issues"
```

Whenever an issue is created, action-bot will add a comment like this:

![issue-comment][issue-comment]


### Add a pull request comment

```yml
name: CI

on:
  pull_request:
    types:
      - opened

jobs:
  add-pr-comment:
    uses: rednafi/i-have-seen/.github/workflows/seen.yml@v1
    with:
      message: |
        Simple comment **works**.
         This is another ~line~.

      where: "pull_request"
```

Upon the creation of a pull request, a comment will appear as follows:




[issue-comment]: https://user-images.githubusercontent.com/30027932/200104205-62ab9ada-13b7-4a04-94e5-2a1913b1e569.png
