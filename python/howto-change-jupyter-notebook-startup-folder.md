# How to change Jupyter Start-up Folder (Anaconda)
Assuming the installation of Anaconda is completed in Your respective OS. Reference to the original solution in StackOverflow: https://stackoverflow.com/questions/35254852/how-to-change-the-jupyter-start-up-folder 

In order to change the configuration from Conda command line, we need to follow the instruction. 

1. Run conda command prompt

Open terminal in VS Code and innstall via `conda` directly. 
```
conda install --yes --file requirements.txt
```
2. In case of failure over one can iterate over all lines in the requirements.txt file. 
```
while read requirement; do conda install --yes $requirement; done < requirements.txt
```