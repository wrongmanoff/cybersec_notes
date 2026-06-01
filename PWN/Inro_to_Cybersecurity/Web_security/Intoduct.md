# WEB Security

### 

- **Purpose** — Prevents unauthorized actions on web apps like triggering bank transfers on someone else's behalf without their consent
- **Core Threat** — Attackers can trick users into visiting a malicious URL that silently sends requests to other sites the user is logged into
- **Cookie Risk** — Browsers auto-attach session cookies to every request, so even loading a hidden image can execute an authenticated action on another site
- **JavaScript Danger** — Servers can send executable JavaScript to your browser; it must be sandboxed to prevent system-level damage like file deletion
- **Server-Side Risk** — Malicious client input can manipulate databases, exposing sensitive data (credit cards, SSNs) or trigger unintended server actions
- **Cross-Client Attack** — Client A can corrupt a server, which then delivers malicious code to Client B — attacking others without direct contact
- **Security vs Usability** — Not all cross-site cookie sharing is bad (e.g., embedded YouTube); browsers must intelligently balance security with functionality