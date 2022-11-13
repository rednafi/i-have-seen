<h1>
i-have-seen
<img src="https://user-images.githubusercontent.com/30027932/200141283-46138fd1-7575-4aff-886d-181a9c39c1a2.png"
align="right" width="128" height="128">
</h1>

***\>>
Workflow to automatically add a comment when an issue or a pull request is opened
\<<***

![actions-badge]

## Usage

### Add an issue comment

Drop this snippet in a separate file in your `.github/workflows` directory:

```yml
name: CI

on:
  issues:
    types:
      - opened

jobs:
  add-issue-comment:
    uses: rednafi/i-have-seen/.github/workflows/seen.yml@v2
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

Similar to the previous section, drop this snippet in `.github/workflows` directory to
add a comment after a pull request is opened:

```yml
name: CI

on:
  pull_request:
    types:
      - opened

jobs:
  add-pr-comment:
    uses: rednafi/i-have-seen/.github/workflows/seen.yml@v2
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

This snippet will make sure that comments are added to both newly opened issues or pull
requests:

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
    uses: rednafi/i-have-seen/.github/workflows/seen.yml@v2
    with:
      message: |
        Simple comment **works**.
         This is another ~line~.

      where: "issues"

  add-pr-comment:
    uses: rednafi/i-have-seen/.github/workflows/seen.yml@v2
    with:
      message: |
        Simple comment **works**.
         This is another ~line~.

      where: "pull_request"
```

### Add comments only when an issue or a pull request contains a specific label

The following CI snippet will ensure that a comment will be added to an issue or a pull
request only when it's labeled with `bug`:

```yml
name: Test

on:
  issues:
    types:
      - labeled
  pull_request:
    types:
      - labeled

jobs:
  add-issue-comment:
    if: ${{ github.event.label.name == "bug" }}
    uses: rednafi/i-have-seen/.github/workflows/seen.yml@v2
    with:
      message: |
        Simple comment **works**.
         This is another ~line~.

      where: "issues"

  add-pr-comment:
    if: ${{ github.event.label.name == "bug" }}
    uses: rednafi/i-have-seen/.github/workflows/seen.yml@v2
    with:
      message: |
        Simple comment **works**.
         This is another ~line~.

      where: "pull_request"
```

Now, if you create an issue or a pull request and label that with `bug`, this action-bot
will add a comment there. This can be seen in action [here][example].

[actions-badge]: https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white
[issue-comment]: https://user-images.githubusercontent.com/30027932/200104205-62ab9ada-13b7-4a04-94e5-2a1913b1e569.png
[pr-comment]: https://user-images.githubusercontent.com/30027932/200104282-9a574966-6e08-487e-b5f2-3b4c7607e0a6.png
[example]: /.github/workflows/test.yml

<div align="center">
<i> ✨ 🍰 ✨ </i>
</div>
