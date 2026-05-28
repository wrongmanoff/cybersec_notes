# Security Mitigations 

example 

most command injection vulnerabilites end up hijacking /bin/sh

### mitigation :

if /bin/sh is run as SUID

i.e eUID == 0 but rUID !=0, 

it will drop privileges to the ruid

i.e euid = ruid and ruid !=0

To disable that : sh -p 