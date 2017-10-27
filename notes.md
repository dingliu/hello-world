# Basic Initial Config

Identity config

- `$ git config --global user.name 'User Name'`
- `$ git config --global user.email 'username@example.com'`

Coloring of UI config

- `$ git config --global color.ui auto`

# Three Stage Thinking

Think 3-stage like a shoping cart.

- Working: `add` file to staging
- Staging: `commit` file to repo
- Repo: `checkout` to working

Initialize a new git repo:

- `$ git init repo-name`

Check the status of current repo:

- `$ git status`

Add file to current repo for git to watch:

- `$ git add filename`

Commit file(s) at the staging phase to current repo

- `$ git commit`