# Installing Python dependency in Anaconda. 
Installing python dependency packages through requirement.txt in Anaconda. Original solution via StackOverflow: http://stackoverflow.com/questions/35802939/install-only-available-packages-using-conda-install-yes-file-requirements-t

1. Open terminal in VS Code and innstall via `conda` directly. 
```
conda install --yes --file requirements.txt
```
2. In case of failure over one can iterate over all lines in the requirements.txt file. 
```
while read requirement; do conda install --yes $requirement; done < requirements.txt
```