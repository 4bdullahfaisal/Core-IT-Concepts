# NETWORKING BASICS — IP, DNS, HTTP/HTTPS
---

## WHAT IS A NETWORK
Two or more computers connected together to share data.

## REAL LIFE ANALOGY
A road system connecting houses. Data is the cars driving on roads.

---

## IP ADDRESSES

### What is an IP address

A unique identifier for a device on a network. Like a house address.

### Two versions

| Version | Format | Example |
|---------|--------|---------|
| IPv4 | Four numbers (0-255) separated by dots | 192.168.1.1 |
| IPv6 | Longer hex format (newer) | 2001:0db8:85a3::8a2e:0370:7334 |

### Two types of IP addresses

| Type | Meaning | Example |
|------|---------|---------|
| Public | Visible on the internet | 8.8.8.8 (Google DNS) |
| Private | Only visible inside local network | 192.168.1.100 (your phone at home) |

### Special IP addresses

| IP | What it means |
|----|---------------|
| 127.0.0.1 | localhost (your own computer) |
| 0.0.0.0 | All available interfaces |
| 255.255.255.255 | Broadcast (send to everyone) |

### How to find your IP

```bash
Windows      # Command Prompt
ipconfig

Mac/Linux    # Terminal
ifconfig
or
ip addr

```
---

## PORTS

### What is a port

A door number on a computer. IP address finds the computer, port finds the program.

### Real life analogy

Apartment building:
- IP address = building address
- Port = apartment number

### Common port numbers

| Port | Protocol | What it does |
|------|----------|--------------|
| 80 | HTTP | Regular web traffic |
| 443 | HTTPS | Secure web traffic |
| 22 | SSH | Secure shell (remote access) |
| 25 | SMTP | Email sending |
| 53 | DNS | Domain name resolution |
| 3306 | MySQL | Database |

### Visual

```bash
Your computer (192.168.1.100)
    |
    |-- Port 80: Web browser
    |-- Port 443: Secure browser
    |-- Port 22: SSH connection
    |-- Port 53: DNS queries
```

---

## DNS (DOMAIN NAME SYSTEM)

### What is DNS

The phonebook of the internet. Converts domain names (google.com) to IP addresses (142.250.190.46).

### Real life analogy

You know "John's Pizza Shop" (domain name). You don't know the address (IP). You look it up in phonebook (DNS).

### How DNS works

- Step 1: You type "google.com" in browser

- Step 2: Computer asks DNS server "What is the IP for google.com?"

- Step 3: DNS server replies "142.250.190.46"

- Step 4: Computer connects to that IP address

### Visual

```bash
User: "google.com"
   |
   v
DNS Server: "What IP is google.com?"
   |
   v
DNS Server: "142.250.190.46"
   |
   v
User connects to "142.250.190.46"
```

### How to test DNS

```bash
Windows/Mac/Linux (Terminal):
nslookup google.com

Output example:
Server: 8.8.8.8
Address: 142.250.190.46
```

### Common DNS servers

| DNS Server | Owner | Privacy |
|------------|-------|---------|
| 8.8.8.8 | Google | Default |
| 1.1.1.1 | Cloudflare | More private |
| 9.9.9.9 | Quad9 | Security focused |

---

## HTTP (HYPERTEXT TRANSFER PROTOCOL)

### What is HTTP

The language web browsers use to ask for web pages.

### How HTTP works

- Step 1: Browser sends HTTP request to server
- Step 2: Server sends HTTP response back

### HTTP Methods (verbs)

| Method | What it does | Example |
|--------|--------------|---------|
| GET | Retrieve data | Loading a webpage |
| POST | Send data | Submitting a form |
| PUT | Update data | Editing a profile |
| DELETE | Remove data | Deleting a post |

---

## HTTPS (SECURE HTTP)

### What is HTTPS
HTTP with encryption. The S stands for Secure.

### Real life analogy
HTTP = Postcard (anyone can read it)
HTTPS = Sealed envelope (only recipient can open)

### What HTTPS protects
- Prevents snooping (someone reading your data)
- Prevents tampering (someone changing your data)
- Verifies the website is real (not a fake)

### How to tell if a site uses HTTPS

Look for:

- https:// at the beginning of URL (not http://)

- Padlock icon in address bar

### Visual

`HTTP:  http://example.com     (no padlock, not secure)`

`HTTPS: https://example.com    (padlock, secure)`

### What happens in HTTPS

Step 1: Browser asks server for secure connection

Step 2: Server sends certificate (proof of identity)

Step 3: Browser verifies certificate

Step 4: Both agree on encryption keys

Step 5: All data is now encrypted (scrambled)

Step 6: Only browser and server can unscramble it

---

## COMPLETE FLOW (What happens when you type a URL)

You type: https://www.google.com/search?q=cats

> Step 1: Browser checks if it already knows google.com IP (in cache)

> Step 2: If not, browser asks DNS server: "What IP is google.com?"

> Step 3: DNS replies: "142.250.190.46"

> Step 4: Browser connects to 142.250.190.46 on port 443 (HTTPS)

> Step 5: Browser and server do HTTPS handshake (encryption setup)

> Step 6: Browser sends HTTP GET request for /search?q=cats

> Step 7: Server processes request and sends HTTP response (200 OK with HTML page)

> Step 8: Browser renders the page

Total time: Usually under 1 second

---

## NETWORKING QUICK REFERENCE

| # | Term | What it is | One Sentence | Example |
|---|------|-----------|--------------|---------|
| 1 | IP Address | Device address | Every device has a unique address. | 192.168.1.1 |
| 2 | Port | Program door | Different programs use different doors. | 80 (web), 443 (secure web) |
| 3 | DNS | Domain to IP lookup | Turns names into IP addresses. | google.com → 142.250.190.46 |
| 4 | HTTP | Web protocol (not secure) | Language browsers speak (not secure). | http://example.com |
| 5 | HTTPS | Secure web protocol | Same as HTTP but encrypted (secure). | https://google.com |
| 6 | Status Code | Response number | Server tells browser if request worked. | 200 (OK), 404 (Not found) |

---
