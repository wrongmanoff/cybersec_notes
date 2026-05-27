NETCAT (nc) : its often called as swiss army knife of netwoerking 

basic syntax : 

```bash
nc [opitons] host port
```

```
nc google.com 80
nc scanme.nmap.org 22
nc localhost 8000
these all open a tcp  connection to the specified host and part  
```

## connection to a server

connect to a web server

```
nc google.com 80
```

then manually we need to type : 

```http
GET / HTTP/1.1
Host: google.com
```

we will receive the raw HTTP response 

## verbose mode 

```
nc -v google.com 80
```

show connection deatils : 

![image-20260527191519610](images/image-20260527191519610.png)

## listen for connections 

netcat can wait for incomign connections 

terminal 1 : 

```
nc -lvnp 4444
-l  = listen
-v = verbose
-n = don't resolve DNS
-p 4444 = listen on port 4444
```

Output 

```
Listening on 0.0.0.0 4444
```

## connect to a listner

Terminal 2 : 

```
nc localhost 4444
```

now anyting typed in one terminal appears in other. This demonstrates a raw tcp connection

## tranfer files 

send file  :

```
nc -lvnp 4444 < secret.txt
```

recevice file : 

```
nc localhost 4444 > recevied.txt
```

## port checking

check if port is open : 

```
nc -vz scanme.nmap.org 22
```

## usefull flags

| Flag   | Meaning                  |
| ------ | ------------------------ |
| `-l`   | Listen mode              |
| `-v`   | Verbose                  |
| `-n`   | No DNS resolution        |
| `-p`   | Specify local port       |
| `-u`   | UDP mode                 |
| `-z`   | Scan mode (no data sent) |
| `-w 5` | Timeout after 5 seconds  |

we can write parameter or query stirng like this : 

```http
GET /requrest?query=heelo HTTP/1.1
```

