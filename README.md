# firewall-filtering
blocking ports in firewall

sudo ufw enable -- ⚠️ This will start blocking/allowing based on rules.

LIST OF THE PRESENT RULES

sudo ufw status numbered

Status: active

<img width="465" height="233" alt="Screenshot From 2025-09-26 09-51-03" src="https://github.com/user-attachments/assets/68f2c043-a9a4-401b-a70c-04dccd70cae1" />

RULE TO BLOCK INBOUND TRAFFIC ON A SPECIFIC PORT 23 (TELNET)

 sudo ufw deny 23/tcp

<img width="466" height="319" alt="Screenshot From 2025-09-26 09-52-55" src="https://github.com/user-attachments/assets/a71c927b-bfa8-4b78-a1ff-9154bcb8f332" />


TRYING TO CONNECT TO PORT 23

telnet localhost 23

Trying ::1...
Connection failed: Connection refused
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

<img width="524" height="158" alt="Screenshot From 2025-09-26 09-52-08" src="https://github.com/user-attachments/assets/5ad58507-bc96-4c0a-8366-087d891e3324" />


RULE TO ALLOW SSH (PORT 22)

sudo ufw allow 22/tcp

<img width="236" height="139" alt="Screenshot From 2025-09-26 09-51-53" src="https://github.com/user-attachments/assets/5c8439ee-2ba1-487e-82d8-6bbaa768185a" />

TEST BLOCK RULE TO RESTORE ORIGINAL STATE BY REMOVING

sudo ufw delete deny 23/tcp
<img width="320" height="170" alt="Screenshot From 2025-09-26 09-53-50" src="https://github.com/user-attachments/assets/e63070a9-409e-4ca3-aa15-a5fa22427198" />


COMMANDS

Commands run (ufw allow, ufw deny, ufw status).



A firewall acts like a security guard between your computer/network and the outside world.
It decides whether to allow or block network packets based on rules.

🔹 1. Packet Inspection

Every piece of network communication is broken into packets.

A firewall examines these packets (header + data).

It checks:

Source IP (where it came from)

Destination IP (where it’s going)

Protocol (TCP, UDP, ICMP, etc.)

Port number (e.g., 80 for web, 22 for SSH, 23 for Telnet)

🔹 2. Rule Matching

Firewalls have a rule set (like an if-else list).

Rules can say things like:

Allow traffic to port 22 (SSH).

Deny traffic from IP 203.0.113.5.

Block all inbound Telnet (port 23).

The firewall compares each packet to its rules from top to bottom until it finds a match.

🔹 3. Filtering Methods

Packet Filtering: Looks at packet headers only (fast but basic).

Stateful Inspection: Tracks connections and only allows packets that are part of a valid session (more secure).

Application Layer Filtering: Examines actual data (e.g., blocks malicious HTTP requests).

🔹 4. Types of Filtering

Inbound filtering: Controls traffic coming into your device/network. Example: Block Telnet (23) from outside.

Outbound filtering: Controls traffic going out. Example: Stop malware from sending data to a hacker’s server.

🔹 5. Example (UFW)
