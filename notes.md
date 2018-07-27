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

# Command Composition

Two flavors

- Plumbing: low level utilities
- Porcelain: set of useful higher level commands
    + Porcelain is composite of plumbing tools

# Git Storage Mechanism

Git uses DAG storage, copy the entire tree during checkin.

- Compression: zlib deflates blobs
- Hard link: to identical blobs

# Inline Hash

- Centralized VCSs use sequential revision numbers
- Git uses a SHA-1 hash (use as little as unique: treeish)
    - `9AB223`
    - `9AB223^` (the commit that right before `9AB223`)
- HEAD
    + One repo can has multiple heads
    + we usually refer to the HEAD of branch we are currently working on
    + `HEAD^` the commit that right before current HEAD
    + `HEAD~3` 3 commits before HEAD

Display the history of commits

- `$ git log`
- `$ git log --pretty=oneline` display every commit in one line
- `$ git log 583fa` display the commit that has the has `583fa` and commits before that
- `$ git log 583fa^..583fa` display the commit `583fa` and one commit backwards
- `$ git log HEAD~3..HEAD`

Display the last commit

- `$ git show`

Display the difference between two commits in patch format

- `$ git log HEAD~4..HEAD~2 -p`

Add modifications and commit at the same time

- `$ git commit -a -m 'commit message'` (can't track changes other than file modifications)

What get hashed

- blob
- tree
- commit
- tag

Author & committer in git

Commit can has parent(s), or nil as parent for the initial commit

# Branching of Git

Default branch of any git repo is **master**.

- When should you branch: always branch.
- Branching isolates volatile work.
- Categorize by lifetime
    + Short lived
    + Feature
    + Release

Create new branches

- `$ git remote -v` show more info about remote repo
- `$ git branch idea-a` create a new branch `idea-a`
    + then `$ git checkout idea-a` switch to this branch
- `$ git checkout -b idea-b` create and switch to branch `idea-b`
- `$ git branch` display current branches
- `$ git branch --set-upstream branch-a origin/branch-a` set the upstream for a local branch
- `$ git checkout e79ff9e` checkout to certain commit, 'detached HEAD' state
    + Then `$ git branch yesterday` start a branch 'yesterday' from that certain commit.
    + Or, `$ git branch yesterday e79ff9e` also do the same thing.
- `$ git log --graph --pretty=oneline` show git log in a 'graphical' way

# Remotes

- Remotes are just **symbolic names**
- You can have as **many** as you like
- The default name is **origin**, if you've cloned
- `$ git remote -v` verbosely showing remote info
- `$ git remote add another https://username@gitrepo.com/reponame.git` add another remote
- Remote branches are locally **immutable**
- **Bidirectional** code transmission
    + clone
    + pull (fetch and merge)
    + fetch (without merge)
    + push
- `$ git diff idea-a origin/idea-a` showing diff between local branch and the branch fetched from remote, without merge first
    + `$ git diff master^^ origin/idea-a` showing diff between local master branch, 2 commits back to current HEAD, with remote idea-a branch
    + `$ git diff --word-diff` showing diff word by word

# Tagging

- **True** tagging and **cheap** tags
- Tagging at **each level** of approval
- **Light** and **object** tag types
    + Comments attached to tag
    + Actual object (commit) for object tag
    + GPG signing
- `$ git tag <TAGNAME>` default
- `$ git tag -a <TAGNAME>` heavy weight
- By default, tags are not pushed.
    + `$ git push --tags` push with tags
- `$ git tag -a` needs commit message
    + Heavy tag also not pushed by default
- Pull contains tags by default
- `$ git branch -d branch_name` delete a branch
- `$ git help tag` show the man page for `help` command
- `$ git tag -d TAG_NAME` delete the tag
- By default, git doesn't allow tags with the same name
- Tags (heavy or light) can be applied to the same commit

# Merging

- `$ git checkout master` then `$ git merge idea-a`, merge branch `idea-a` into branch `master`
- `$ git diff` display the diffs
- `$ git checkout --ours -- confilict.filename`
- `$ git checkout --theirs -- conflict.filename`
- `$ git add conflict.filename` then commit and push

# Rebase

- Only on local machine, local history not being shared out yet.
- You can rebase frequently with remote, to keep the effort small
- 
