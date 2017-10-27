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

Five stages

- Ignored
- Untracked
- Unmodified
- Modified
- Staged

Initialize a new git repo:

- `$ git init repo-name`

Check the status of current repo:

- `$ git status`

Add file to current repo for git to watch:

- `$ git add filename`
- `$ git add .` (add all files currently not watched by git)
- `$ git add . -A` (add all files modified or current not watched by git)
- Git tracks the contents of files, so empty file can't be added.

Commit file(s) at the staging phase to current repo

- `$ git commit`
- `$ git commit -a` (add modified file when doing the commit)
- `$ git commit -m` (add commit message when doing the commit)
- Frequent commit is recommended.
- Commit message can't be empty.
- Split filename changes and file content modifications into separate commits

Remove file from staged phase

- `$ git rm filename`

Ignore files from repo

- Create `.gitignore` file and add patterns in it
- `*.log` and `**/*.log` (the latter one ignores any `*.log` files in any sub-directories)

Temporary Ignores

- `$ git update-index --assume-unchanged filename`
- `$ git update-index --no-assume-unchanged filename`

# Cloning Repositories

Git supports many cloning protocols

- ssh (most common and secure)
    - `$ git clone ssh://user@server:reponame.git`
    - `$ git clone user@server:reponame.git`
- git (often peer to peer and read only)
    - `$ git clone git://server/reponame.git`
- https
    - `$ git clone https://server/reponame.git`
- file
    - `$ git clone file://myrepos/reponame`
    - `$ git clone /myrepos/reponame`

We can specify the different name when cloning:

- `$ git clone user@server:reponame.git aliasname`

# Branch of Git

Default branch of any git repo is **master**.

