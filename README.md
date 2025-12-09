# Network Honeypot – Fake FTP Service (Learning Project)

This repository is my learning project for Python & cybersecurity.
The goal is to build a **fake FTP service honeypot** that:
[]
- Accepts connections like a normal FTP server
- Captures attacker IPs, usernames and passwords
- Logs everything to a file
- (Future) Sends email alerts with attack details
- (Future) Adds port mapping / scanning logic

I’m building this step-by-step together with my tutor.

---

## Project Structure

_Currently:_

- `honeypot.py` – Python script where the fake FTP logic will live 
- `notes.txt` – My planning file with:
  - project goals
  - architecture diagrams
  - TODOs and ideas
- `main.py` – Original notes / placeholder from the TryHackMe task

_Later:_

- `email_reporter.py` – Send attack logs to email
- `port_scanner.py` – Port mapping & response logic
- `docs/` – More diagrams and documentation

---

## Architecture – Step 1: Fake FTP Honeypot

High-level flow for the first part of the project:

1. **Attacker / Bot** tries to connect to `ftp://<my-ip>:2121`
2. **Fake FTP server (Python / pyftpdlib)** accepts the connection
3. Server captures:
   - IP address
   - Username
   - Password
   - Timestamp
4. **Logging module** writes these details into `honeypot.log`
5. (Future) **Email reporter** sends an alert with the captured data

The detailed ASCII diagram is in `notes.txt`.

---

## Goals for This Project

### Technical goals

- Learn how FTP works and why it’s often attacked
- Learn how to:
  - write Python server code
  - use `logging` correctly
  - handle events like `on_connect`, `on_login`, `on_login_failed`
  - structure a small security project with multiple modules
- Get comfortable with:
  - Git & GitHub workflow
  - VS Code + Python + virtual environments

### Security / Honeypot goals

- Understand how attackers probe FTP services
- Capture and analyze login attempts
- Prepare for future honeypots (SSH, HTTP, etc.)

---

## How to Run (current stage)

Right now this project is still in **early development**.
The basic steps (on my local machine):

```bash
# Inside project folder
python3 honeypot.py


## Step 2: Port Scan Detection (Planning Stage)

I created a file called `port_scanner.py` where we will build the logic
with my tutor. For now it only contains TODOs and structure.

Goal:
- detect basic port scan activity
- log attacker IP + ports
- later connect this to the email alert system