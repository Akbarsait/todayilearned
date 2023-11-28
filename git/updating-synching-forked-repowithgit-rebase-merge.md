# Updating / Synching a Forked Repo with git rebase / merge
A quick tip on Updating / Synching a Forked repo in Git using rebase or merge.<br/> 
References - [Synching a Fork](https://docs.github.com/en/free-pro-team@latest/github/collaborating-with-issues-and-pull-requests/syncing-a-fork)

1. Add the remote (original repo that you forked) and call it 'upstream' 
```
$ git remote add upstream https://github.com/remoterepurl
```

2. Fetch all branches and their commits from remote upstream

```
$ git fetch upstream
```

3. Checkout the fork's local master
```
$ git checkout master
```

4. Either use rebase or merge based on your need. Let's use merge in our case. (Docs Ref: Git rebase moves a feature branch into a master. Git merge adds a new commit, preserving the history)
```
$ git merge upstream/master
```

5. Push your updates to master. You may need to force the push with force comment (Docs Ref:
Syncing your fork only updates your local copy of the repository. To update your fork on GitHub / Gitlab etc., we must push the change.)
```
$ git push origin master --force
```