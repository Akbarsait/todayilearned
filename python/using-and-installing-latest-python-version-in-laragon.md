# Using and Installing latest version of Python in Laragon
Laragon is an light-weight development environment. 

1. Installl Laragon by using the following these steps: [Insall Laragon](https://laragon.org/docs/install.html).  By default, Laragon includes Python 3.10 is included wiht Laragon 6. 
   
2. Open Terminal and navigate to the Laragon installed folder to check the version of the Python. 
   ```cmd
    C:\laragon> python --version
    Python 3.10.6
    C:\laragon>
   ```

3. To install the latest version of the python, open laragon\pacakage.conf file by accessing "Laragon menu > Tools > Quick Add > configuration". Add the following line and use the version needed for your use case. 
```cmd
# Python
python-3.12=https://www.python.org/ftp/python/3.12.3/python-3.12.3-amd64.exe
```

4. Now Python 3.12 can be automatically downloaded and installed by accessing the "Laragon menu > Tools > Quick Add > python-3.12." Now running the version check will return as follows. 
```cmd
    C:\laragon> python --version
    Python 3.12.3
   ```
