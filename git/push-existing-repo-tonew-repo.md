# Push an existing Repository to a new Repositor
A quick tip on pushing an existing repo to a new in Github.<br/> 
References - [stackoverflow.com](https://stackoverflow.com/questions/5181845/git-push-existing-repo-to-a-new-and-different-remote-repo-server)

1. Create a new repo at github.
2. Clone the repo from fedorahosted to your local machine.
3. Run the following commands

```zsh

$ git remote rename origin upstream
$ git remote add origin URL_TO_GITHUB_REPO
$ git push origin main

```

4. Now you can work with it just like any other github repo. To pull in patches from upstream, simply run the below command.

```zsh

$ git pull upstream main && git push origin main

```