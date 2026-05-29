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

