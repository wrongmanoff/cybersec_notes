# WINDOWS fundamentals

## The file System

The file system used in modern versions of Windows is the **New Technollogy File System** or **NTFS**. Beofer ntfs there was FAT16/FAT32 ( file allocation table ) and HPFS ( High Performance FIle System)

NTFS has : 

- Supports files larger than 4gb 
- set specific permission on folders and files
- folder and file compression 
- encrryption (Encryption FIle System or EFS)

On NTFS volumes we can set The permissions : 

1. full control
2. modify
3. read & execute
4. list folder contenets 
5. read 
6. write

Another important feature of NTFS is ADS Alternate Data Streams : it is a file attribute specific to windows NTFS. Every file has atleast one data setream ($DATA)

THe system environment variable for the windows directory is 

```
%windir%
```

Environment Variables : it stores information about the os env. the information includes details such as the os path, the no of processor used by the os, and the location of the temporary folders. 

There are many  folders in Windows, so one of the many folders is **System32** it holds the imp files that are critical for the os

## User accounts, profiles and permissions

By using run in run type this 

```
lusrmgr.msc
```

so from there you can access users groups and everything realted to this. 

## UAC (user accounts control)

uac make sure that no program can make important changes to your system without your permission. it basically ask us do you want to allow this app to make tchanges to your device? 

### how it works : 

- even if we are logged in as an administartor, windoes doesn't give full power by default 
- it runs most programs with standard user priv
- when elevated access is need uac prompts for permission. 