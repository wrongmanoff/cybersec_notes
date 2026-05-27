# STATE

Modern web applications are not just static websites; they are remote programs running on servers. These applications often maintain state(logged in users, account data, preferences) allowing interactions to evove over time.

- Http iteself does not remeber previous request; every request is independent.
- A server can store application data, but hte http protocol provides no built-in way to identify that multiple request came from the same client

Solution is Cookies : Use HTTP headers for maintaing state. To maintain state Servers use the Set-Cookie response header. 

1. The server sets a cookie in a response with the header: **Set-Cookie**
2. The client includes the cookie in the further request wiht the header: **Cookie**

The server can now use the cookie provided in those future requests.

## login request

```http
POST /login HTTP/1.0
Host: account.example.com
Content-Lenght: 32
Content-Type: application/x-www-form-urlencoded

username=Bhavesh&password=pass223
```

## login response 

```http
HTTP/1.0 302 Moved Temporarily
Location: http://account.example.com/
Set-Cookie: authed=Bhavesh
```

## login redirect request

```http
GET / HTTP/1.0
Host: account.example.com
Cookie: authed=Bhavesh
```

## Login redirect response 

```http
HTTP/1.0 200 OK
Content-Type: text/html; charset=UTF-8
Content-Lenght: 40
Connection: close

<html><body>Hello, Bhavesh!</body></html>
```

## another login request 

```http
POST /login HTTP/1.0
Host: account.example.com
Content-Lenght: 32
Content-Type: application/x-www-form-urlencoded

username=NEw&password=pass223
```

## another login response 

```http
HTTP/1.0 302 Moved Temporarily
Location: http://account.example.com/
Set-Cookie: authed=NEw
```

## another login redirect request

```http
GET / HTTP/1.0
Host: account.example.com
Cookie: authed=NEw
```

## another login redirect response

```http
HTTP/1.0 200 OK
Content-Type: text/html; charset=UTF-8
Content-Lenght: 40
Connection: close

<html><body>Hello, NEw!</body></html>
```

```http
GET / HTTP/1.0
Host: account.example.com
Cookie: authed=admin
```

```http
HTTP/1.0 200 OK
Content-Type: text/html; charset=UTF-8
Content-Lenght: 40
Connection: close

<html><body>Hello, admin!</body></html>
```

here we have secuiryt concern here we don't need pass we can guess the cookie and then get the admin contents.

we can have session_id instead of authed 

## Session ID : login request

```http
POST /login HTTP/1.0
Host: account.example.com
Content-Lenght: 32
Content-Type: application/x-www-form-urlencoded

username=Bhavesh&password=2pasd3
```

## Session Id : login response 

```http
HTTP/1.0 303 Moved Temporraliy
Location: http://account.example.com/
Set-Cookie: session_id=A1B2C3D4
```

## Session Id : redirect request

```http
GET / HTTP/1.0
Host: account.example.com
Cookie: A1B2C3D4
```

## Session id : redirect response

```http
HTTP/1.0 200 OK
Content-Lenght: 40
Content-Type: text/html; charset=UTF-8
Connection: Close

<html><body>Hello, Bhavesh!</body><html>
```

