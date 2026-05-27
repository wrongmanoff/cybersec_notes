## HTTP URL scheme

```
<scheme>://<host>:<port>/<path>?<query>#<fragment>
http://example.com:80/cat.gif?width=246&height=256#t=2s
```

- Scheme: Portocl used to access resource
- host: host that holds resource 
- port : port for program servicing resource
- path : identifies the specific resource
- query: information that the resource can use
- fragment: client information about the resource, allow url to contain client specific infomration. 

## Request-URI : 

Unsafe: **SP**, **<**, **>**, **"**, **#**, **%**, **{**, **}**, **|**, **\**, **^**, **~**, **[**, **]**, **`**

Reserved: **;**, **/**, **?**, **:**, **@**, **=**, **&**

Unprintable: **0x00** - **0x1F**, **0x7F**

Any other character **may** be encoded

URL ENCODING : 

it should be done by this way like first % sign hex hex 

```
% hex hex 
sp = %20
Follow ascii chart 
# = %23
/ = %2f
? = %3f
A = %41
```

### Hello World Reqeust

```http
GET /Hello World HTTP/1.0
Host: hello.example.com
```

see above request is a wrong request cause it's is not encoded properly htere is a sp between 

```http
GET /Hello%20World HTTP/1.0
Host: hello.example.com
```

Now you can see that this is the correct request 

### Hellow world response 

```http
HTTP/1.0 200 OK
Content-Type: text/html; charset=UTF-8
Content-Lenght: 39

<html><body>Hello, WOrld!</body></html>
```

## Content-Type: Form

Content-Type: appliaction/x-www-form-urlencoded 

we have already seen in teh post request. we tell to the server that we are using form it's inthe form of key-value pairs 

```http
POST /greet HTTP/1.0
Host: hello.example.com
Content-Lenght: 11
Content-Type: application/x-www-form-urlencoded

name=Bhavesh
```

## Content-Type: JSON

Content-Type: application/json

javascript object notiaon we can send the structed object throught ths json. 

```http
POST /greet HTTP/1.0
Host: hello.example.com
Content-Lenght: 18
Content-Type: application/json

{"name"="Bhavesh"}
```

