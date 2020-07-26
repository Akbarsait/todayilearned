# Transfer a repository from Bitbucket to Github
A quick tip on transfering the Bitbucket repository to Github.<br/> 
References - [http://www.blackdogfoundry.com/blog/moving-repository-from-bitbucket-to-github/](http://www.blackdogfoundry.com/blog/moving-repository-from-bitbucket-to-github/) & [http://www.paulund.co.uk/change-url-of-git-repository](http://www.paulund.co.uk/change-url-of-git-repository)
1. Navigate to the folder of repo on windows. 
```
$ cd /d/Projects/repo-directory (master)
```
or Navigate to them in MacOS

```
$ cd $HOME/Projects/repo-directory (master)
```
2. Run the following commands with your new repo name. 
```
$ git remote rename origin bitbucket
$ git remote add origin https://github.com/akbarsait/the-new-repo.git
$ git push origin master

$ git remote rm bitbucket
```