## path traversal 

path traversal is also know as directory traversal. it helps us to read arbitary files on the server that is runnign on application 

### normal behaviour 

suppose a webiste servers files form `/var/www/fiels/` and teh application does : 

```python
open("/var/www/files/" + filename )
```

so if we requeset `report.pdf` the applicatoin opens `/var/www/files/report.pdf` . now instead of requeseting report.pdf an attacker requesets : `../../../etc/passwd` so the path becomes `/var/www/files/../../../etc/passwd` the operating system resolves this to : `/etc/passwd` 

because : `.. = parent directory` so : 

```
/var/www/files/
    ..
/var/www/
    ..
/var/
    ..
/

Then :
/etc/passwd
```

Common Payloads : 

```
../
../../
../../../
../../../../
```

for suppose it's an web application url 

```url
https://example.com/download?file=report.pdf
```

it becomes 

```url
https://example.com/download?file=../../../etc/passwd
```

