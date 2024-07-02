---
title: "On Virtual Environments"
date: 2024-07-02
draft: false
categories:
  - Technical
---

In [a previous post]({{< ref "/terminal,CLI,shell.md" >}} "") I talked a bit about shells. I explained that a shell is a proces that launches other programs. That got me wondering... When I activate a virtual environment, such as a Python or Anaconda venv, is that also launching a program? 

The answer is **NO**

Some commands will launch a new process, some won't. Things that launch new processes are for example .exe files like python.exe, notepad.exe and ping.exe. What doesn't launch a new process, are most built-in commands like cd, mkdir and echo, Powershell cmdlets such as Get-Location, and - as you can see in red - the commands to activate Python virtual environments.


| Launches New Process                           | Does Not Launch New Process                        |
|:------------------------------------------------:|:----------------------------------------------------:|
| python script.py                               | cd /path/to/directory                            |
| notepad.exe                                                 | mkdir new_directory (PowerShell and Bash)          |
|  ping google.com                                     | <span style="color: red;">.\venv\Scripts\Activate.ps1 (PowerShell) </span>        |
|                              | <span style="color: red;">source ./venv/bin/activate (Bash)</span>                  |
|                                                  | Get-Location (PowerShell cmdlet)                   |
|                                                | echo "Hello, World!"                               |
|                                                | Set-Location /path/to/directory (PowerShell)       |



Using '.' in PowerShell or 'source' in Bash runs the script in the current shell session, allowing changes to environment variables and other settings to persist. This is precisely what the venv activation scripts do; they edit environment variables. 


### What is a Virtual Environment?

A virtual environment in Python is a directory that contains a Python installation for a particular version of Python, along with a number of additional packages. It allows you to work on multiple projects that require different dependencies without interference. 

### Activation Script Overview

When you activate a virtual environment, you typically run an activation script provided by the virtual environment. The location and name of the script vary slightly between operating systems:

- Windows: .\venv\Scripts\Activate.ps1 (PowerShell) or .\venv\Scripts\activate.bat (Command Prompt)
- Unix-like systems (Linux, macOS): source ./venv/bin/activate

### What Does the Activation Script Do?

1. Sets Environment Variables:

    - VIRTUAL_ENV: This variable is set to the path of the virtual environment directory. It serves as a marker for tools and scripts to detect that a virtual environment is active.
    - PATH: The script modifies the PATH environment variable to include the virtual environment's bin (or Scripts on Windows) directory at the beginning. This ensures that the virtual environment’s Python interpreter and scripts are used before any global Python installations.

2. Modifies the Shell Prompt:

    - The activation script updates your shell prompt to indicate that you are working within a virtual environment. Typically, it prefixes the prompt with the name of the virtual environment (e.g., (.venv)).

3. Clears PYTHONHOME:

    - If the PYTHONHOME environment variable is set, the script clears it. This prevents conflicts with the Python installation inside the virtual environment.

