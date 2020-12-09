# Introduction to using a Command Line Interface (CLI)

This is a very basic introduction to using a CLI. The following is written for Windows users using PowerShell. The Terminal on a Mac or Unix system works in a similar way.

## To open PowerShell
* From the start menu open PowerShell. The PowerShell opens as a blue window. 
    * Alternatively, you can navigate to a specific folder using Windows Explorer. If you then hold down shift, you can right-click, and select *Open PowerShell here*.
> Sometimes, if you don't have permission to perform certain tasks, you might need to run PowerShell as an administrator. To do this, right click on PowerShell when you select it from the start menu and select 'Run as administrator'

The PowerShell shows the drive and the path to the current directory e.g.

F:\web>

In this case I'm working on the in the *web* directory on the *F:* drive

## To view the contents of a directory (folder)

Type *dir*:
```
F:\web>dir
 Volume in drive F has no label.
 Volume Serial Number is 9061-CF9F

 Directory of F:\web

13/07/2020  16:04    <DIR>          .
13/07/2020  16:04    <DIR>          ..
13/07/2020  17:06             408 index.html
30/08/2020  10:16    <DIR>          blog
               1 File(s)          3,370 bytes
               3 Dir(s)   4,358,488,064 bytes free
```

## To change directory (a folder)

Type *cd* followed by the directory name

```
F:\web>cd blog

F:\web\blog>
```

Directories are specified relative to the current directory. For example ../ will move up one directory level. 
```
F:\web>cd ../

F:\>
```

You can also change directory by typing *cd* and then dragging the folder from windows explorer onto the Command Prompt

## To change drive

Type in the drive letter followed by a colon ':' e.g.

```
F:\web>D:

D:\>
```

## Making a new directory
Type *mkdir* followed by the name for the new directory

```
D:\> mkdir project
D:\> cd project
D:\project> 
```

## Cancelling
Sometimes you will need to stop the execution of the currently running task to do this enter *ctrl+c*.

## Accessing previous commands
You can use the up and down arrows to scroll through previous commands. 







