## System configuration

The system config utility (MSConfig) is for advanced troubleshooting, and its main purpose is to help diagonse startup issues. Launching system config cna be from start menu by typing msconfig

## change uac settings 

The uac setting can be changed from user account conrtol settings : it has 4 levels : 

- **Always notify:** This is the highest security. Windows notifies you whenever any apps or you yourself try to make changes, and the desktop dims (Secure Desktop).
- **Notify for apps**: Windows notifies only when *apps* try to make changes, but not when you change Windows settings. This option is enabled by default.
- **Notify without dimming:** Same as above (Notify for apps), but this time the screen does not dim. 
- **Never notify:** Notifications are turned off. Windows won’t warn you about any changes made by you or any apps. 

## computer management

## System Information 

windows include a tool called microsoft system information (msinfo32.exe). this tool gathers info about your computer and displays hardware, system components, and software environment

![image-20260504121016285](../../images/image-20260504121016285.png)

## resource monitor 

it can be accessed by resmon.exe. it displyas per-process and aggregate cpu, memory, disk and network usage information, in addition to providing details about which processes are using individual file handles and modules. Advanced filtering allows users to isolate the data related to one or more processes ( either applications or services), start, stop, pause, and resume services, and close unresponsive applications fromt he user interface. It aslo includes a process analysis feature that can help identify deadlocked processa nd file locking conflicts so that the user can attempt to resolve the conflict instead of closing an application and potentially losing data. 

## command prompt 

it is the command line cmd. If you need any help in the commands jst type this : 

```cmd
ipconfig /? or 
ipconfig help
```

## registry editor

windows registry is a central hierarchial database used to store information necessary to configure the system for one or more users, applications, and hardware device