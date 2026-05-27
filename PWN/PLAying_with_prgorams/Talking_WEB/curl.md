# curl = Client URL

curl is a speciaized tool for speaking HTTP . it lets us send HTTP requests from the command line. here instead of manually typing 

```http
GET / HTTP/1.1
Host: example.com
```

we can simply do : 

```bash
curl http://example.com
```

### basic GET request

```bash
curl http://example.com
```

if you want to see the http headers 

```bash
curl -i https://example.com
```

-i = include response headers.

-I = only show headers

### verbose mode :

see exactly what curl sends and receives : 

```
curl -v https://example.com
```

### save output to  afile

```bash
curl https://example.com -o page.html
```

### follow redirects 

```bash
curl -L http://google.com
```

when 301 moved permanently with -L it direclty goes there to the new location

## post request

send data to server : 

```bash
curl -X POST https://httpbin.org/post
```

-X specifies the HTTP method. 

```bash
curl -X POST \
     -d "username=bhavesh" \
     -d "password=secret" \
     https://httpbin.org/post
```

-d = sends the request body

```bash
curl -X POST \
     -H "Content-Type: application/json" \
     -d '{"name": "bhavesh", "role": "sutdnet"}' \
     https://httpbin.org/post
```

-H adds headers

## most important flags 

| Flag | Meaning                     |
| ---- | --------------------------- |
| `-v` | Verbose output              |
| `-i` | Show response headers       |
| `-I` | HEAD request (headers only) |
| `-L` | Follow redirects            |
| `-X` | Specify method              |
| `-H` | Add header                  |
| `-d` | Send data                   |
| `-o` | Save output to file         |
| `-c` | Save cookies                |
| `-b` | Send cookies                |
| `-u` | Basic auth                  |

for host headers : 

```
curl -H "Host: xss.pwnfunction.com" http://challenge.localhost/gateway
```

multiple query's can be given as : 

```
curl "http://challenge.localhost/gate?verify=euxcdjll&security=idcgvsrs&signature=afhjjtqj"
```

