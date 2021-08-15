---
title:  "How To Add Git Bash to Windows Terminal" 
categories: [tips]
description: Add Git Bash to Windows Terminal
tags: [tips]
--- 

[Windows Terminal](https://docs.microsoft.com/en-us/windows/terminal/) is a new product offering by Microsoft, using which we can access various command line offerings both by Microsoft and Linux.

We can use Powershell, Command Prompt, Ubuntu, etc.

What if I wanted to use Git Bash in Windows Terminal!  
All I need to do is add a profile.

Here's how:

1. Open Windows Terminal
2. Click on the `New Tab Drop Down`
3. Click `Settings`  
** Alternatively you can press `Ctrl + ,` to open settings.

<p align="left">
<img src="{{ "/assets/img/WindowsTerminal1.jpg"  | relative_url }}" alt="Windows Terminal" align="middle"/>
</p>  

As of writing of this blog, Windows Terminal settings will open a `json` file. I recommend using `Visual Studio Code` IDE to open `json` files (its your wish though 🙂).

Once the json is opened, under `Profiles` section, under `list` array, add the following lines.

``` json
{
    "guid": "{a74fc813-a735-4056-8509-95eb32a08d9b}",
    "hidden": false,
    "name": "Git Bash",
    "commandline": "%PROGRAMFILES%\\Git\\bin\\bash.exe",
    "icon": "%PROGRAMFILES%\\Git\\mingw64\\share\\git\\git-for-windows.ico",
}
```

You can generate guid [here](https://www.guidgen.com/).

Now, you will be able to use Git Bash from Windows Terminal.

<p align="left">
<img src="{{ "/assets/img/WindowsTerminal2.jpg"  | relative_url }}" alt="Git Bash in Windows Terminal" align="middle"/>
</p>

Links to Download:  

* [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701?activetab=pivot:overviewtab)  
* [Git Bash](https://git-scm.com/downloads)