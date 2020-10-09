+++
author = "Hocine BEKKOUCHE"
date = 2020-10-09
title = "Add 'Open in VSCode' to Context Menu in Windows"
summary = "when you are installing vs code there is tow checkboxes you could select to make it open in the context menu."
series = "Operations"
thumbnail = "/images/02-vscode.jpg"
thumbnail_bg_color = "#8d26d8"
dark_thumbnail = true
tags = ["ide","tools"]
+++
## Introduction
In this article, 
we will try to add 'Open in VSCode' to Context Menu in Windows.

## During installation
when you are installing vs code there is tow checkboxes you could select to make it open in the context menu.
![Example image](/images/02-vscode-02.png)

## After installation
if you missed the configuration during installation the solution
create a reg file with this content (Replace the paths if you have a custom installation):
{{< highlight bash>}}
Windows Registry Editor Version 5.00
; Open files
[HKEY_CLASSES_ROOT\*\shell\Open with VS Code]
@="Edit with VS Code"
"Icon"="C:\\Program Files\\Microsoft VS Code\\Code.exe,0"
[HKEY_CLASSES_ROOT\*\shell\Open with VS Code\command]
@="\"C:\\Program Files\\Microsoft VS Code\\Code.exe\" \"%1\""
; This will make it appear when you right click ON a folder
; The "Icon" line can be removed if you don't want the icon to appear
[HKEY_CLASSES_ROOT\Directory\shell\vscode]
@="Open Folder as VS Code Project"
"Icon"="\"C:\\Program Files\\Microsoft VS Code\\Code.exe\",0"
[HKEY_CLASSES_ROOT\Directory\shell\vscode\command]
@="\"C:\\Program Files\\Microsoft VS Code\\Code.exe\" \"%1\""
; This will make it appear when you right click INSIDE a folder
; The "Icon" line can be removed if you don't want the icon to appear
[HKEY_CLASSES_ROOT\Directory\Background\shell\vscode]
@="Open Folder as VS Code Project"
"Icon"="\"C:\\Program Files\\Microsoft VS Code\\Code.exe\",0"
[HKEY_CLASSES_ROOT\Directory\Background\shell\vscode\command]
@="\"C:\\Program Files\\Microsoft VS Code\\Code.exe\" \"%V\""
{{< / highlight >}}

Double click it to create the registry entries