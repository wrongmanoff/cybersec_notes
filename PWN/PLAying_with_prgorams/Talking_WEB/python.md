**ython's `requests` library** is one of the most important tools you'll use. Think of it as **curl inside Python**.

First install it (if needed):

```
pip install requests
```

Import it:

```python
import requests
```

------

# 1. Simple GET Request

Equivalent to:

```
curl https://example.com
```

Python:

```python
import requests

response = requests.get("https://example.com")

print(response.text)
```

### What is `response`?

It's an object containing:

- Status code
- Headers
- Cookies
- Body
- URL

------

# 2. Status Codes

```python
import requests

r = requests.get("https://example.com")

print(r.status_code)
```

Output:

```
200
```

Common codes:

| Code | Meaning      |
| ---- | ------------ |
| 200  | OK           |
| 301  | Redirect     |
| 403  | Forbidden    |
| 404  | Not Found    |
| 500  | Server Error |

------

# 3. Response Body

HTML:

```python
print(r.text)
```

Raw bytes:

```python
print(r.content)
```

Use `.content` for images/files.

------

# 4. Response Headers

```python
print(r.headers)
```

Example:

```python
print(r.headers["Content-Type"])
```

Output:

```
text/html
```

------

# 5. Send Query Parameters

URL:

```
https://site.com/search?q=python&page=2
```

Python:

```
import requests

params = {
    "q": "python",
    "page": 2
}

r = requests.get(
    "https://httpbin.org/get",
    params=params
)

print(r.url)
```

Result:

```

https://httpbin.org/get?q=python&page=2
```

------

# 6. Custom Headers

Equivalent to:

```

curl -H "User-Agent: HackerBrowser"
```

Python:

```

headers = {
    "User-Agent": "HackerBrowser"
}

r = requests.get(
    "https://httpbin.org/headers",
    headers=headers
)

print(r.text)
```

------

# 7. POST Request

Equivalent to:

```

curl -X POST -d "name=bhavesh"
```

Python:

```

data = {
    "name": "bhavesh"
}

r = requests.post(
    "https://httpbin.org/post",
    data=data
)

print(r.text)
```

------

# 8. Send JSON

Very common in APIs.

```

import requests

payload = {
    "username": "bhavesh",
    "role": "student"
}

r = requests.post(
    "https://httpbin.org/post",
    json=payload
)

print(r.json())
```

Requests automatically:

- Converts dict → JSON
- Sets Content-Type header

------

# 9. Parse JSON Responses

API returns:

```

{
  "name":"Bhavesh",
  "age":20
}
```

Python:

```

data = r.json()

print(data["name"])
```

Output:

```

Bhavesh
```

------

# 10. Cookies

Send cookies:

```

cookies = {
    "session": "abc123"
}

r = requests.get(
    "https://httpbin.org/cookies",
    cookies=cookies
)

print(r.text)
```

------

# 11. Read Cookies

```

r = requests.get("https://example.com")

print(r.cookies)
```

Specific cookie:

```

print(r.cookies.get("session"))
```

------

# 12. Sessions (VERY IMPORTANT)

Without sessions:

```

requests.get(...)
requests.get(...)
```

Cookies are lost between requests.

Use:

```

import requests

session = requests.Session()

session.get("https://example.com/login")

session.get("https://example.com/profile")
```

Cookies persist automatically.

This is how browser-like behavior works.

------

# 13. Login Example

```

import requests

session = requests.Session()

login_data = {
    "username": "admin",
    "password": "password"
}

session.post(
    "https://site.com/login",
    data=login_data
)

profile = session.get(
    "https://site.com/profile"
)

print(profile.text)
```

The session automatically sends authentication cookies.

------

# 14. File Downloading

```

import requests

r = requests.get(
    "https://example.com/image.jpg"
)

with open("image.jpg", "wb") as f:
    f.write(r.content)
```

------

# 15. File Uploading

```

files = {
    "file": open("test.txt", "rb")
}

r = requests.post(
    "https://httpbin.org/post",
    files=files
)
```

------

# 16. Redirects

Requests follows redirects automatically.

Disable:

```

r = requests.get(
    "http://example.com",
    allow_redirects=False
)

print(r.status_code)
```

------

# 17. Timeout

Avoid hanging forever:

```

r = requests.get(
    "https://example.com",
    timeout=5
)
```

------

# 18. Authentication

Basic auth:

```

from requests.auth import HTTPBasicAuth

r = requests.get(
    url,
    auth=HTTPBasicAuth(
        "admin",
        "password"
    )
)
```

Short version:

```

r = requests.get(
    url,
    auth=("admin", "password")
)
```

------

# 19. Useful for CTFs and pwn.college

### Add a Cookie

```

requests.get(
    url,
    cookies={
        "user": "admin"
    }
)
```

### Custom Header

```

requests.get(
    url,
    headers={
        "X-Admin": "true"
    }
)
```

### POST Login Form

```

requests.post(
    url,
    data={
        "username": "admin",
        "password": "admin"
    }
)
```

### Inspect Response

```

print(r.status_code)
print(r.headers)
print(r.text)
```

------

# Mini Real-World Example

```

import requests

session = requests.Session()

login = session.post(
    "https://example.com/login",
    data={
        "username": "bhavesh",
        "password": "secret"
    }
)

print("Login:", login.status_code)

dashboard = session.get(
    "https://example.com/dashboard"
)

print(dashboard.text)
```