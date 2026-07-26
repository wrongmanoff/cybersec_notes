## DNS

Sure! Here's a clear explanation of **DNS (Domain Name System):**

------

**Why Do We Need DNS?**

- No one wants to memorize IP addresses like `93.184.215.14` just to visit a website
- **DNS acts like a phonebook for the internet** — it translates human-friendly domain names (like `example.com`) into machine-friendly IP addresses
- Without DNS, you'd have to type the exact IP address of every website you want to visit

------

**What is DNS?**

- **DNS (Domain Name System)** maps domain names to their corresponding IP addresses
- Operates at **Layer 7 (Application Layer)** of the OSI model
- Uses **port 53** by default for both queries and responses
- Uses **UDP** for fast lookups (and TCP as fallback for larger responses)

------

**4 Key DNS Record Types**

**1. A Record (Address)**

- Maps a domain name to an **IPv4 address**
- Example: `example.com` → `172.17.2.172`
- Used when your browser needs to find a website

**2. AAAA Record (Quad-A)**

- Same as A record but maps to an **IPv6 address**
- Called "Quad-A" because it has **four A's**
- Example: `example.com` → `2606:2800:21f:cb07:...`

**3. CNAME Record (Canonical Name)**

- Maps a **domain name to another domain name**
- Example: `www.example.com` → `example.com`
- Useful for creating aliases or redirects between domains

**4. MX Record (Mail Exchange)**

- Specifies the **mail server** responsible for handling emails for a domain
- Example: When sending to `test@example.com`, the mail server looks up the MX record to find where to deliver the email

**How DNS Lookup Works — Step by Step**

1. You type `example.com` in your browser
2. Your device sends a **DNS query** to the DNS server asking for the **A record**
3. The DNS server responds with the **IP address**
4. Your browser uses that IP address to connect to the website

If you want to lookup the ip address of a domain from teh command line, you can usa a tool such as nslookup 

```bash
            
user@TryHackMe$ nslookup www.example.com
Server:         127.0.0.53
Address:        127.0.0.53#53

Non-authoritative answer:
Name:   www.example.com
Address: 93.184.215.14
Name:   www.example.com
Address: 2606:2800:21f:cb07:6820:80da:af6b:8b2c
```

## WHOIS

**Who Controls DNS Records?**

- When you **register a domain name**, you gain the authority to set its DNS records (A, AAAA, MX, CNAME, etc.)
- Example: If you register `example.com`, you decide which IP address it points to, which mail server handles its emails, etc.
- This registration is managed through **domain registrars** (companies like GoDaddy, Namecheap, etc.)

------

**Domain Registration — Key Facts**

- You can register any **available domain name** for one or more years
- You must pay an **annual fee** to keep the domain
- You are required to provide **accurate contact information** as the registrant
- This contact information becomes part of the **publicly accessible WHOIS records**

------

**What is WHOIS?**

- **WHOIS** (pronounced "who is") is a public record system that stores information about **who registered a domain**
- It is **not an acronym** — just the question "who is" this domain registered to?
- You can look up WHOIS records using:
  - Online WHOIS lookup services
  - Command line: `whois example.com` (available on Linux)

**What Does a WHOIS Record Contain?**

| Field              | Description                                 |
| ------------------ | ------------------------------------------- |
| Domain Name        | The registered domain                       |
| Creation Date      | When the domain was first registered        |
| Updated Date       | When the record was last modified           |
| Expiration Date    | When the registration expires               |
| Registrar          | Company through which domain was registered |
| Registrant Name    | Name of the domain owner                    |
| Registrant Email   | Contact email of the owner                  |
| Registrant Phone   | Contact phone of the owner                  |
| Registrant Address | Physical address of the owner               |

```
whois x.com
```

## FTP (File transferring protocol)

FTP is bascially designed to transfer files. examples command defined by the FTP protocl are : 

- `USER` is used to input the username
- `PASS` is used to enter the password
- `RETR` (retrive) is used to download a file from the FTP server to the client 
- `STOR` (store) is used to upload a file from the client to the FTP server.

It listens on TCP port 21
Usage : 

```bash
ftp 10.49.151.33
```

we use above command to connect to the remote ftp server using the local `ftp` client. These all details are asked/done during this : 

- Username (`USER`)
- password (`PASS`)
- ls ( here ls mean `LIST`)
- type ascii ( here ascii is given we can switch to any mode ) `TYPE A`
- get coffe.txt ( it retrives the file we want ) here get mean `RETR`
- `QUIT` 

## SMTP ( Simple Mail Transfer protocol ) (Sending email)

SMTP defines how a mail client talks with a mail server like for example its bascially like gmail is client talking to its server using the smtp protocol. And that mail server talks with another. SOme of the commands are : 

- `HELO` or `EHLO` it initiates an SMTP session 
- `MAIL FROM` specifies teh sender's email address
- `RCPT TO` specifies the recipient's email address
- `DATA` it tells that client will begin sending the content of the email message.
- `.` it's sent to show that it's and end of the email message. 

SMTP server listens on TCP port 25 

## POP3 (Post Office Protocol version 3) (receiving email)

pop3 is designed to allow the client to communicate with a mail server and retrive email messages. Its like opposite version of smtp where it sends to mail server from mail client but here it recives mail from mail server to mail client. Some comman commandas are : 

- `USER` <username> identifies teh user
- `PASS` <password> provides teh user's password 
- `STAT` requests the no of msg's and total size
- `LIST` lists all msg and sizes 
- `RETR <message_number>` retrives a specified message 
- `DELE <Message_number>` it delets a specified message  
- `QUIT`

POP3 server listens on TCP port 110 

## IMAP(Internet MEssage Access Protocl) ( synchornizing email)

POP3 is limited only to one device. if you want to check email from your office desktop, laptop, phone synchronization is required. SO IMAP maintains a synchronized mailbox across mulitple devices. 

With IMAP we could synchornize read, moved, and deleted messages. SOme commands are : 

- `LOGIN <username> <password>` auth users
- `SELECT <mailbox> ` selects the mailbox folder to work with
- `FETCH <mail_number> <data_item_name>` example `fetch 3 body[]` to fetch message number3 header and body.
- `MOVE <sequence_set> <mailbox>` move teh specified messages to antoher mailbox
- `COPY <sequence_set> <data_item_name>` copies the specified msg to anotherm mailbox 
- `LOGOUT`

IMAP server listens on TCP port 143. 
