# How to change Jupyter Start-up Folder (Anaconda)
Assuming the installation of Anaconda is completed in Your respective OS. Reference to the original solution in StackOverflow: https://stackoverflow.com/questions/35254852/how-to-change-the-jupyter-start-up-folder 

In order to change the configuration from Conda command line, we need to follow the instruction. 

1. Opent the Anaconda command prompt and enter the following into the prompt:

```
jupyter notebook --generate-config
```
A directory `.jupyter/` should have created in your home with a file `jupyter_notebook_config.py` 

2. Find the above file `jupyter_notebook_config.py`. It will be located in `C:\Users\name\.jupyter`. Open the file and edit it in notepad++ or vscode. Find the following commneted statement:
```
#c.NotebookApp.notebook_dir = ''
```
Uncomment it, by removing "#" in the first column. Now add our target folder address were we want the to start the Jupyter notebook. 
```
c.NotebookApp.notebook_dir = 'C:\\Users\\name\\foldername'
```
Save the file and ipen anaconda prompt again, type jupyter notebook. This should launch Jupyter Notebook in the browser in the folder with the above address. Here, the key point is to UNCOMMENT (which means to delete) the # at front of the line, and then, USE \\ double slashes (for the path separator) between folders. If you use only single slashes \, it won't work.