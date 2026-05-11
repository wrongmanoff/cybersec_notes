## Basic system information 

```cmd
ver
```

it gives the os version 

```cmd
systeminfo
```

it give in-depth information about the system

## network configuration 

```
ipconfig
```

we can check our network information using this.

```
ipconfig /all
```

this gives everything better use this.

## network troubleshooting 

one common troubleshooitng task is checking if the server can access a particular sever on the internt. 

```
ping target_name
```

one more command is tracert which stands for trace route. 

```
tracert target_name
```

traces the network route travesed to reach the target. 

one more command is nslookup. it looks up a host or domain and returns its ip address

```
nslookup example.com
```

one more command is netstat. this display current network connection and listenitng ports. 

## file and disk management

```
dir
```

```
dir /a display hidden and system files as well 
dir /s display files in the current directory and all subdirectories
```

```
tree 
to visually represent the child directories and subdirectories
```

```
mkdir
rmdir
```

```
type
more
copy
move
del file.txt or erase file.txt
```

## task and process management

```
tasklist
we can check all available filters using : 
tasklist /? 
if we want to serach for sshd.exe 
task /FI "imgagename eq sshd.exe"
```

we can kill task by : 

```
taskkill /PID target_pid
taskkill /PID 4567
```

