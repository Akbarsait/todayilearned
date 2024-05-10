# Miniconda configuration on Windows for Python
Setting up a Miniconda in windows for Python development . 

1. Install Miniconda for Windows from [https://conda.io/](https://conda.io/).

2. Verify installation and configuration are done correctly by running python command by opening "Anaconda Prompt (Miniconda3)" from your machine.  To exit the Python shell, type exit() and press Enter.
```powershell
(base) PS C:\Users\Mando> python
Python 3.12.2 | packaged by Anaconda, Inc. | (main, Feb 27 2024, 17:28:07) [MSC v.1916 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

3. Configuring 'conda-forge' as default package channel by running the following commands. 
```
(base) PS C:\Users\Mando> conda config --add channels conda-forge
(base) PS C:\Users\Mando> conda config --set channel_priority strict
```

4. Create a Conda environment by using the follwoing comment. 

```
conda create -y -n pydata-labs python=3.12
```
- Arguments 'n' is for the name of the environment and 'y' is for output prompt for "not to ask for confirmation". To activate and deactivate the environment, you can utilze below commands. 
```python
# To activate this environment, use
#     $ conda activate pydata-labs
# To deactivate an active environment, use
#     $ conda deactivate
```