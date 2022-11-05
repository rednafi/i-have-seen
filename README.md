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
      # Markdown syntax is allowed.
      message: |
        Simple comment **works**.
         This is another ~line~.

      where: "issues"
```

Whenever an issue is created, action-bot will add a comment like this:

![issue-comment]

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
    # Markdown syntax is allowed.
    with:
      message: |
        Simple comment **works**.
         This is another ~line~.

      where: "pull_request"
```

Upon the creation of a pull request, a comment will appear as follows:

![pr-comment]

### Add both issue & pull request comments

This can be seen in action [here][example].
```yml
name: CI

on:
  issues:
    types:
      - opened
  pull_request:
    types:
      - opened

jobs:
  add-issue-comment:
    uses: ./
    with:
      message: |
        Simple comment **works**.
         This is another ~line~.

      where: "issues"

  add-pr-comment:
    uses: ./
    with:
      message: |
        Simple comment **works**.
         This is another ~line~.

      where: "pull_request"
```


[issue-comment]: https://user-images.githubusercontent.com/30027932/200104205-62ab9ada-13b7-4a04-94e5-2a1913b1e569.png
[pr-comment]: https://user-images.githubusercontent.com/30027932/200104282-9a574966-6e08-487e-b5f2-3b4c7607e0a6.png
[example]: /.github/workflows/test.yml
