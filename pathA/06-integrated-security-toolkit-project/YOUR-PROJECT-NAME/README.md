# RedAlarm 🔴
### Integrated Security Toolkit — by 0xredlog
> Stage 6 of the 24-Month Red Team Roadmap

RedAlarm is a modular security toolkit that combines network scanning, Windows enumeration, hash identification, and password cracking into one tool.

---

## Modules

| # | Module | Description |
|---|--------|-------------|
| 1 | Network + Port Scanner | Ping check, port scan, banner grabbing, HTTP detection |
| 2 | Windows Enumeration | Collects users, groups, processes, services, network connections |
| 3 | Hash Identifier | Identifies hash type using hashid |
| 4 | Password Cracker | Cracks hashes using John the Ripper |

---

## Requirements

- Kali Linux
- Python 3
- hashid
- John the Ripper
- requests library

Install dependencies:

```bash
sudo apt install hashid john -y
pip3 install requests
```

---

## Installation

**Step 1 — Clone the repo**
```bash
git clone https://github.com/0xredlog/RedAlarm.git
```

**Step 2 — Go into the folder**
```bash
cd RedAlarm
```

**Step 3 — Install dependencies**
```bash
sudo apt install hashid john -y
pip3 install requests
```

**Step 4 — Run the toolkit**
```bash
python3 toolkit.py
```

---

## Usage

```
 _____ ___   ___  _     _  _______ _____ 
|_   _/ _ \ / _ \| |   | |/ /_   _|_   _|
  | || | | | | | | |   | ' /  | |   | |  
  | || |_| | |_| | |___| . \  | |   | |  
  |_| \___/ \___/|_____|_|\_\ |_|   |_|  

        by 0xredlog | Stage 6

1. Network + Port Scanner
2. Windows Enumeration
3. Hash Identifier
4. Password Cracker
5. Exit
```

**Module 1 — Network + Port Scanner**
```
Select module: 1
Enter target IP: 192.168.1.1
Enter port range (e.g. 1-1000): 1-1000
```
Results auto-saved to `scan_192.168.1.1_2024-11-16.txt`

**Module 2 — Windows Enumeration**
```
Select module: 2
```
Results auto-saved to `Worm_2024-11-16.txt`

**Module 3 — Hash Identifier**
```
Select module: 3
Enter hash to identify: 5f4dcc3b5aa765d61d8327deb882cf99
```

**Module 4 — Password Cracker**
```
Select module: 4
Enter path to hash file: hashes.txt
Do you have a wordlist? (yes/no): yes
Enter path to wordlist: /usr/share/wordlists/
```

---

## Output Files

| File | Created by |
|------|------------|
| `scan_IP_DATE.txt` | Module 1 — port scan results |
| `Worm_DATE.txt` | Module 2 — Windows enumeration results |

---

## Legal

This tool is for **educational use and authorized testing only.**  
Only run against systems you own or have explicit written permission to test.  
Unauthorized scanning is illegal.

---

## Author

**0xredlog** — 24-Month Red Team Journey  
GitHub: github.com/0xredlog
