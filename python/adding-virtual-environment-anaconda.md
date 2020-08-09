# Adding Virtual Environment with Anaconda
Seting up a virtual environment through terminal using conda for the Anaconda Python distribution . 

1. Open terminal in VS Code and check conda version. 
```
conda -V
```
2. Create a virtual environment using create command. 
```
conda create -n myvirenvname
```
3. Proceed by typing ``y``. Sometimes if the name already exists conda ask you to overwrite. 
```
conda create -n myvirenvname
```
4. We can create a virtual environment with a package by giving the following command. 
```
conda create -n myvirenvname numpy
```
5. Activate Your new virtual environment".

```
conda activate myvirenvname
```
5. Deactivate Your new virtual environment".

```
conda deactivate
```