<div align="center">

# بِسْمِ اللَّهِ الرَّحْمَنِ الرَّحِيمِ

### * In the name of Allah , the Most Gracious , the Most Merciful *

## الحمد لله على كل شيء — Alhamdulillah for everything 🤲

### * InshAllah — By His will . *

</div>

---

<p align="center">
  <img src="logo.png" alt="RedAlarm Logo" width="800"/>
</p>

![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python)
![Platform](https://img.shields.io/badge/Platform-Linux-black?style=for-the-badge&logo=linux)
![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=for-the-badge)
![Author](https://img.shields.io/badge/Author-0xredlog-red?style=for-the-badge)
![Version](https://img.shields.io/badge/Version-1.0-red?style=for-the-badge)

---

## What is RedAlarm?

```
 _____ ___   ___  _     _  _______ _____ 
|_   _/ _ \ / _ \| |   | |/ /_   _|_   _|
  | || | | | | | | |   | ' /  | |   | |  
  | || |_| | |_| | |___| . \  | |   | |  
  |_| \___/ \___/|_____|_|\_\ |_|   |_|  

        by 0xredlog | Stage 6
```

RedAlarm is a modular integrated security toolkit built from scratch in Python. It combines network scanning, Windows enumeration, hash identification, and password cracking into one clean menu-driven tool — no external files needed, everything runs from one script.

Built as a Stage 6 project by a self-taught red teamer.

---

## Modules

| # | Module | Description |
|---|--------|-------------|
| 1 | Network + Port Scanner | Ping check, port scan, banner grabbing, HTTP detection |
| 2 | Windows Enumeration | Collects users, groups, processes, services, network connections |
| 3 | Hash Identifier | Identifies hash type |
| 4 | Password Cracker | Cracks hashes using a wordlist or built-in |

---

## Features

- 🔍 4 modules in one tool
- ⚡ Multi-threaded port scanner
- 🎯 Banner grabbing — identifies service + version
- 💾 Auto-saves scan results with IP + date in filename
- 🛡️ Checks if tools are installed before running
- 🔴 Red terminal output
- 📡 Host alive check — ping before scan
- 🌐 HTTP recon — status code + server header
- 💻 Pure Python — everything inside one file
- 🖥️ Works on any Linux machine

---

## Usage

```bash
git clone https://github.com/0xredlog/RedAlarm
cd RedAlarm
python3 toolkit.py
```

### Menu

```
1. Network + Port Scanner
2. Windows Enumeration
3. Hash Identifier
4. Password Cracker
5. Exit

Select module:
```

### Module 1 — Network + Port Scanner
```bash
Select module: 1
Enter target IP: 192.168.1.1
Enter port range (e.g. 1-1000): 1-1000

[+] Host 192.168.1.1 is ALIVE — starting scan...
[+] Port 22 OPEN
    Banner: SSH-2.0-OpenSSH_8.9
[+] Port 80 OPEN
    HTTP Status: 200
    Server: Apache/2.4.52

[+] Scan complete — results saved to scan_192.168.1.1_2024-11-16.txt
```

### Module 2 — Windows Enumeration
```bash
Select module: 2
# Auto-runs PowerShell enumeration
# Results saved to Worm_2024-11-16.txt
```

### Module 3 — Hash Identifier
```bash
Select module: 3
Enter hash to identify: 5f4dcc3b5aa765d61d8327deb882cf99
```

### Module 4 — Password Cracker
```bash
Select module: 4
Enter path to hash file: hashes.txt
Do you have a wordlist? (yes/no): yes
Enter path to wordlist: /your/wordlist/path
```

---

## How It Works

```
1. Menu loads — user picks a module
2. Module 1 → ping check → port scan → banner grab → save results
3. Module 2 → writes PowerShell script → runs enumeration → saves results
4. Module 3 → checks if tool installed → identifies hash type
5. Module 4 → checks if tool installed → cracks hash with or without wordlist
```

Under the hood — `socket` → knocks on each port  
`threading` → runs all workers simultaneously  
`requests` → grabs HTTP headers on port 80/443  
`subprocess` → pings target before scanning  
`os` → runs system tools and checks installations  

---

## Output Files

| File | Created by |
|------|------------|
| `scan_IP_DATE.txt` | Module 1 — port scan results |
| `Worm_DATE.txt` | Module 2 — Windows enumeration results |

---

## Legal

> RedAlarm is built for educational purposes and authorized testing only.  
> Only scan targets you own or have explicit written permission to test.  
> Unauthorized scanning is illegal.

---

## Author

Mohamed Cherradi — 0xredlog  
Self-Taught Red Teamer | Offensive Security | AI Red Teaming

- GitHub: [@rtx772-eng](https://github.com/rtx772-eng)
- LinkedIn: [mohamed-cherradi](https://www.linkedin.com/in/mohamed-cherradi-0b0140432)
- Instagram: [@0xredlogz](https://instagram.com/0xredlogz)

---

## Roadmap

- [x] v1.0 — Network + Port Scanner module
- [x] v1.0 — Windows Enumeration module
- [x] v1.0 — Hash Identifier module
- [x] v1.0 — Password Cracker module
- [ ] v2.0 — CVE lookup module
- [ ] v2.0 — Web recon module

---

*One toolkit. All stages. — 0xredlog*

<p align="center">
  <em> إِنْ شَاءَ اللَّهُ </em><br>
  <strong> Inshallah </strong>
</p>
