# Git and Github

## Get a Git Repository

+ `git init`
+ `git clone <URL> <DIR_NAME>`
  + (default) `<REMOTE>` is named by `origin`
  + (default) `master` tracks `origin/master`
  + `git clone -o <REMOTE>`, change remote name

## File State

+ `git add`
+ `git rm`, remove from the staging area and the working directory
+ `git rm --cached`, remove from the staging area but keep in the working directory
+ `git mv`
+ `git status`
+ `git status -s`, right-hand column: the working directory, left-hand column: the staging area
+ `git diff`, compare the working directory with the staging area
+ `git diff --staged`, compare the staging area with the .git repository
+ `git commit`
+ `git commit -m <COMMIT_MSG>`
+ `git commit -a -m <COMMIT_MSG>`, Git automatically stage every tracked file before doing the commit
+ `git commit --amend`, redo the commit
+ `git restore --staged <FILE>`, unstage the file
+ **(DANGEROUS)** `git restore <FILE>`, discard the changes in the working directory
+ `git stash push`, record the current state of the working directory and the index
+ `git stash list`, see saved stash
+ `git stash apply stash@{<N>}`, apply older stash
+ `git stash drop stash@{<N>}`, remove stash on stack
+ `git log`
+ `git log -<NUM>`, limit the number of log entries displayed
+ `git log -p`, show the difference introduced in each commit
+ `git log --stat`, see some abbreviated stats for each commit
+ `git log --pretty`
  + `git log --pretty=oneline`
  + `git log --pretty=short`
  + `git log --pretty=full`
  + `git log --pretty=fuller`
  + `git log --pretty=format`, specify the format explicitly
+ `git log --graph`
+ `git log --decorate`, show where the branch pointers are pointing
+ `git log --since`, `git log --until`
+ `git log -S <STRING>`, show commits that changed the string

## Git Branch

+ `git branch`, list branches
  + `git branch -v`, list branches with last commit
  + `git branch -vv`, list branches with more information
  + `git branch --merged`, list branches that have been merged into the current branch
  + `git branch --no-merged`, list branches that have not been merged into the current branch
+ `git branch <BRANCH> <START_POINT>`, create `<BRANCH>` at `<START_POINT>`
  + (default) `<START_POINT>` is `HEAD`
+ `git branch -m <OLD_BRANCH> <NEW_BRANCH>`, rename branch
+ `git branch -d <BRANCH>`, delete branch
+ `git push <REMOTE> --delete <REMOTE_BRANCH>`
+ `git branch --track <BRANCH> <START_POINT>`, create `<BRANCH>` tracking at `<START_POINT>`
+ `git branch -u <UPSTREAM> <BRANCH>`, set `<UPSTREAM>` as `<BRANCH>`'s upstream
  + (default) `<BRANCH>` is the current branch
+ `git branch --unset-upstream <BRANCH>`, remove `<BRANCH>`'s upstream information
+ `git switch <BRANCH>`, move `HEAD` to point to the branch
  + `git switch -`, return to the previous branch
+ `git switch -c <BRANCH>`, create a new branch and switch to the new branch

## Working with Remotes

+ `git remote -v`, show remotes and corresponding shortnames
+ `git remote show <REMOTE>`, see information about a remote
+ `git remote rename <OLD> <NEW>`, also change the remote-tracking branch names
+ `git remote add <SHORTNAME> <URL>`
+ `git remote rm <SHORTNAME>`, also delete remote-tracking branches and configuration settings
+ `git fetch <REMOTE>`, only get a new remote-tracking branch, without a local editable copy
  + `git switch -c <LOCAL_BRANCH> <REMOTE_BRANCH>`
+ `git pull`, fetch data and merge automatically
+ `git push <REMOTE> <BRANCH>`
  + `git push <REMOTE> <LOCAL_BRANCH>:<REMOTE_BRANCH>`
+ `git push <REMOTE> <TAG>`, push tags to remote servers
  + `git push <REMOTE> --tags`, push all of the tags
  + `git push <REMOTE> --follow-tags`, push all of the annotated tags
+ `git push <REMOTE> --delete <TAG>`, delete tags from remote servers
+ `git tag`, list the existing tags
  + `git tag -l <STRING>`, search tags that match a particular pattern
+ `git show <STRING>`, show the tagger information
+ `git tag <STRING>`, create a lightweight tag
  + `git tag <STRING> <COMMIT_CHECKSUM>`, tag a specific commit
+ `git tag -a <STRING> -m <TAG_MSG>`, create an annotated tag
+ `git tag -d <TAG>`

## Configuration

+ `git config`
  + (default) `--local`, location: `.git/config`
  + `--global`, location: `~/.gitconfig` or `~/.config/git/config`
  + `--system`, location: `[path]/etc/gitconfig`
  + `--local` overrides `--global` overrides `--system`
+ `git config --list --show-origin`, view settings
+ `git config --global user.name <USER_NAME>`
+ `git config --global user.email <USER_EMAIL>`
+ `git config --global http.proxy <HTTP_PROXY>`
  + `git config --global http.proxy "http://127.0.0.1:7890"`
+ `git config --global https.proxy <HTTPS_PROXY>`
  + `git config --global https.proxy "http://127.0.0.1:7890"`
+ `git config --global alias.<ABBR> <FULL_CMD>`
  + `git config --global alias.lg "log --pretty=oneline --graph --decorate --all"`
  + `git config --global alias.st "status -s"`
+ `git config --global init.defaultBranch main`, change `master` to `main` as default
