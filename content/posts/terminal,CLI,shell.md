---
title: "Terminal, CLI, shell"
date: 2024-06-25
draft: false
categories:
  - Technical
tags:
  - Trivia
---

Terminal, command line interface (CLI), shell... 

They are commonly known terms used interchangeably to mean "the nerdy box where you type in commands". 

However these words all have slightly different meanings. 

## Terminal

A computer needs some way for the users to be able to interact with it. Years ago they used a seperate physical 'terminal' to do that. It was a screen with a keyboard attached to it. That way you could type in commands to control another more powerfull pc. 

![](/images/terminals/terminal_smaller.png)


Nowadays we use terminal emulators to interact with the computer. Terminal emulators are not part of the OS, they are just programs. Some popular ones include:

- GNOME Terminal
- Windows Terminal
- Konsole
- Terminator

All terminals offer a way to type in commands. This environment is called the *command line interface* (CLI). My router software


![](/images/terminals/gnome_terminal.png)


## CLI

A CLI (command line interface) is basically the exact opposite of a GUI (graphical user interface). Both offer human interfaces to interact with the pc. CLI's are not limited to terminals. For example, MySQL workbench is a GUI program that also offers a CLI to type queries to interact with the database. 

![](/images/terminals/mysql.png)

Another example is how I access [my router]({{< ref "/DNS-over-https-for-my-whole-family-with-openWRT.md" >}} "openWRT") running OpenWRT. I usually do it via the LuCI web interface, which is a GUI. But it can also be accessed via the openWRT CLI over SSH. 

![](/images/terminals/openwrt_cli.png)

## Shell

A shell is a program for starting other programs. It's just a proces like any other. In UNIX systems, when you enter a command, a child process is forked and the parent process (the shell) waits for it to terminate. 

Some well known ones are:
- bash
- zsh
- fish
- windows commmand prompt
- powershell

Shells differ from one another on:

- Syntax
- Scripting capabilities
- Interactive features
- Customization
- Compatibility with operating systems

All shells also come with prompts. A prompt is just a sequence of characters that tells the user that the shell is waiting for a command. In many shells this prompt can also be customized. 

- Bash: ``tibo@my_thinkpad:~$``
- Powershell: ``PS C:\Users\tibo>``










