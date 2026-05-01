# Day 15 - Networking Concepts: DNS, IP, Subnets & Ports

##  Task 1: DNS – How Names Become IPs

###  What happens when you type `google.com` in a browser?
1. Browser checks cache for IP  
2. If not found, it queries DNS resolver  
3. DNS resolver asks root → TLD(Top Level Domain , For ex: .com , .in , .org ) → authoritative server  
4. IP address is returned and browser connects to server  

---

###  DNS Record Types

- **A** → Maps domain to IPv4 address  
- **AAAA** → Maps domain to IPv6 address  
- **CNAME** → Alias of another domain  
- **MX** → Mail server for domain  
- **NS** → Name servers for domain  

---

###  Command
```bash
dig google.com
```

###  Output (example)
```bash
;; ANSWER SECTION:
google.com.    300    IN    A    142.251.142.238
```

- **A Record IP:** `142.251.142.238`  
- **TTL:** `300`

---

##  Task 2: IP Addressing

###  What is IPv4?
IPv4 is a 32-bit address written in 4 parts:
```
192.168.1.10
```
Each part ranges from 0–255.

---

###  Public vs Private IP

- **Public IP:** Accessible over internet  
  - Example: `8.8.8.8`

- **Private IP:** Used inside networks  
  - Example: `172.31.32.244`

---

### Private IP Ranges

- `10.0.0.0 – 10.255.255.255`  
- `172.16.0.0 – 172.31.255.255`  
- `192.168.0.0 – 192.168.255.255`  

---

### Command
```bash
ip addr show
```

### Example Output
```bash
inet 172.31.32.244/20
```
 This is a **private IP**

---

## Task 3: CIDR & Subnetting

### What does `/24` mean?
`192.168.1.0/24` → first 24 bits are network, remaining for hosts

---

### Usable Hosts

- `/24` → 256 total → 254 usable  
- `/16` → 65536 total → 65534 usable  
- `/28` → 16 total → 14 usable  

---

### Why do we subnet?
- Better network organization  
- Security isolation  
- Efficient IP usage  

---

### CIDR Table

| CIDR | Subnet Mask     | Total IPs | Usable Hosts |
|------|----------------|----------|--------------|
| /24  | 255.255.255.0  | 256      | 254          |
| /16  | 255.255.0.0    | 65536    | 65534        |
| /28  | 255.255.255.240| 16       | 14           |

---

## Task 4: Ports – The Doors to Services

### What is a port?
A port is a logical endpoint used by services to communicate.

---

### Common Ports

| Port | Service |
|------|---------|
| 22   | SSH     |
| 80   | HTTP    |
| 443  | HTTPS   |
| 53   | DNS     |
| 3306 | MySQL   |
| 6379 | Redis   |
| 27017| MongoDB |

---

### Command
```bash
ss -tulpn
```

### Example Output
```bash
LISTEN 0 4096 0.0.0.0:22
LISTEN 0 511  0.0.0.0:80
```

### Mapping:
- Port `22` → SSH  
- Port `80` → HTTP  

---

## Task 5: Putting It Together

### Q1: `curl http://myapp.com:8080`
Concepts involved:
- DNS → resolves domain  
- IP → connects to server  
- Port 8080 → service endpoint  
- HTTP → communication  

---

### Q2: App can't reach DB `10.0.1.50:3306`
First checks:
- Service status (`systemctl status mysql`)  
- Port open (`ss -tulpn`)  
- Firewall/Security Groups  
- Correct IP and port  

---

## What I Learned

1. DNS resolves names to IPs  
2. Subnetting improves organization and security  
3. Ports allow multiple services on same system  

---
