# HTTP (HYPER TEXT TRANSFER PROTOCOL)

HTTP is the common tongue through which web applications, servers, and clients communicate. 

## WWW - world wide web

web of information it's a bunch of information distrubted across the world which uses http. It was created by Sir Tim Berners-Lee. There are lot of websites. all distributed systems speak one single language 

## Static HTTP Request

we are sending an request in a language / protocol so other systems can also understand HTTP

```http
GET /cat.gif HTTP/1.0
```

## Static HTTP Response 

and the response from the system to source system is also in same protocol in http. 

```http
HTTP/1.0 200 OK
```

## Dynamic HTTP request

over system will go fetech out other system and ask what is teh time of the utc 

```http
GET /time?tz=UTC HTTP/1.0
```

## Dynamic HTTP response 

```http
HTTP/1.0 200 ok
Content-Type: text/plain
Contetn-Length: 19

2023-01-12 03:34:45
```

 WE CAN BASICLALY say that http is the standard lanuguage 