# Adding Anaconda Prompt profile to Windows Terminal
A quick profile for adding Anaconda Prompt in Windows Terminal. Two main things to note. 

1. Commandline: Use the path of Anaconda Promt shortcut in windows. It can be identified by selecting the shortcut > Propeties. 
2. Icons should be located under Menu directory of anaconda installed location like "C:\anaconda3\Menu\".

```yaml
{
    // Anaconda Prompt.
    "guid": "{b6f69604-fb9e-46d8-979f-19d175cc91c7}",
    "name": "Anaconda Prompt",
    "commandline": "cmd.exe /K  D:/Programs/anaconda3/Scripts/activate.bat",
    "icon" : "D:/Projects/icons/anaconda-navigator.ico",
    "hidden": false,
    "acrylicOpacity" : 0.5,
    "background" : "#012456",
    "closeOnExit" : true,
    "colorScheme" : "Campbell",
    "cursorColor" : "#FFFFFF",
    "cursorShape" : "bar",
    "fontFace" : "Consolas",
    "fontSize" : 11,
    "historySize" : 9001,
    "padding" : "0, 0, 0, 0",
    "snapOnInput" : true,
    "startingDirectory" : "%USERPROFILE%",
    "useAcrylic" : false            
},
```
