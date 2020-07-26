## Adding Git Bash to ConEmu on Windows. 
The folder path is a hihg level reference. You have to use your own path. [Original Reference](https://gist.github.com/nicolas-t/3fd016c7d08268722a27)

1. Open Conemu
2. Open Settings -> Tasks or go to new tab button -> Setup tasks.
3. Click `+` to add a new task
4. Enter the name as `Git Bash` or whatever you like
5. Task parameters: Make sure the path is properly set. It should be Program Files (x86) in some cases
```
/icon "C:\Program Files\Git\etc\git.ico" /dir "C:\Users\yourprojectfolder"
```
6. Command:
```
"C:\Program Files\Git\bin\sh.exe" --login -i 
```
If you want to force your $HOME directory to be on local HD not network drive, you can do this as the command instead:
```
"set PATH=C:\Users\username;%PATH%" & "set HOME=C:\Users\username" & "C:\Program Files\Git\bin\sh.exe" --login -i 
```