# toolkit.py
# By 0xredlog | Stage 6 — Integrated Security Toolkit

import socket
import threading
import subprocess
import os
import requests
from datetime import datetime

# ─── Colors ───────────────────────────────────────────────
RED = "\033[91m"
RESET = "\033[0m"

# ─── Banner ───────────────────────────────────────────────
def banner():
    print(f"""
{RED}
 _____ ___   ___  _     _  _______ _____ 
|_   _/ _ \ / _ \| |   | |/ /_   _|_   _|
  | || | | | | | | |   | ' /  | |   | |  
  | || |_| | |_| | |___| . \  | |   | |  
  |_| \___/ \___/|_____|_|\_\ |_|   |_|  

        by 0xredlog | Stage 6
{RESET}
1. Network + Port Scanner
2. Windows Enumeration
3. Hash Identifier
4. Password Cracker
5. Exit
    """)

# ─── Module 1: Network + Port Scanner ────────────────────
def run_scanner():
    ip = input("Enter target IP: ")

    # Ping check
    result = subprocess.run(["ping", "-c", "1", ip], capture_output=True, text=True)
    if result.returncode != 0:
        print(f"[-] Host {ip} is DOWN — stopping.")
        return

    print(f"{RED}[+] Host {ip} is ALIVE — starting scan...{RESET}")

    port_range = input("Enter port range (e.g. 1-1000): ")
    if "-" in port_range:
        parts = port_range.split("-")
        start = int(parts[0])
        end = int(parts[1])
    else:
        start = int(port_range)
        end = int(port_range)

    today = datetime.now().strftime("%Y-%m-%d")
    filename = f"scan_{ip}_{today}.txt"

    print(f"\n{RED}[*] Scanning {ip} ports {start}-{end}...{RESET}\n")

    def scan(port):
        sock = socket.socket()
        sock.settimeout(0.5)
        try:
            result = sock.connect_ex((ip, port))
        except:
            return
        if result == 0:
            print(f"[+] Port {RED}{port}{RESET} OPEN")
            try:
                banner = sock.recv(1024).decode().strip()
                print(f"    Banner: {banner}")
                with open(filename, 'a') as f:
                    f.write(f"Port {port} OPEN - {banner}\n")
            except:
                with open(filename, 'a') as f:
                    f.write(f"Port {port} OPEN\n")
            if port == 80 or port == 443:
                try:
                    protocol = "https" if port == 443 else "http"
                    r = requests.get(f"{protocol}://{ip}", timeout=2)
                    print(f"    HTTP Status: {r.status_code}")
                    print(f"    Server: {r.headers.get('Server', 'unknown')}")
                except:
                    pass
        sock.close()

    threads = []
    for port in range(start, end + 1):
        t = threading.Thread(target=scan, args=(port,))
        t.start()
        threads.append(t)
    for t in threads:
        t.join()

    print(f"\n[+] Scan complete — results saved to {filename}")

# ─── Module 2: Windows Enumeration ───────────────────────
def run_recon():
    ps_script = r"""
# ShellWorm — embedded in toolkit.py
# By 0xredlog

$filename = "Worm_$(Get-Date -Format 'yyyy-MM-dd').txt"

Write-Host "[*] Collecting System Info..." -ForegroundColor Green
Write-Output "=== SYSTEM INFO ===" | Out-File -Append $filename
whoami | Out-File -Append $filename

Write-Host "[*] Collecting Local Users..." -ForegroundColor Green
Write-Output "=== USERS ===" | Out-File -Append $filename
get-localuser | Out-File -Append $filename

Write-Host "[*] Collecting Local Groups..." -ForegroundColor Green
Write-Output "=== GROUPS ===" | Out-File -Append $filename
get-localgroup | Out-File -Append $filename

Write-Host "[*] Collecting Processes..." -ForegroundColor Green
Write-Output "=== PROCESSES ===" | Out-File -Append $filename
get-process | Out-File -Append $filename

Write-Host "[*] Collecting Running Services..." -ForegroundColor Green
Write-Output "=== SERVICES ===" | Out-File -Append $filename
get-service | Where-Object {$_.Status -eq "Running"} | Out-File -Append $filename

Write-Host "[*] Collecting TCP Connections..." -ForegroundColor Green
Write-Output "=== NETWORK ===" | Out-File -Append $filename
get-NetTCPConnection | Out-File -Append $filename

Write-Host "[*] Collecting Local Admins..." -ForegroundColor Green
Write-Output "=== LOCAL ADMINS ===" | Out-File -Append $filename
Get-LocalGroupMember -Group "Administrators" | Out-File -Append $filename

Write-Host "[+] Done - saved to $filename" -ForegroundColor Cyan
"""
    # Write the script to a temp file and run it
    script_path = "/tmp/ShellWorm.ps1"
    with open(script_path, 'w') as f:
        f.write(ps_script)

    print("[*] Running Windows Enumeration via PowerShell...")
    os.system(f"powershell.exe -ExecutionPolicy Bypass -File {script_path}")

# ─── Module 3: Hash Identifier ───────────────────────────
def run_hashid():
    # Check if hashid is installed
    check = subprocess.run(["which", "hashid"], capture_output=True, text=True)
    if check.returncode != 0:
        print("[-] hashid is not installed.")
        print("[*] Install it with: sudo apt install hashid")
        return

    hash_input = input("Enter hash to identify: ")
    os.system(f"hashid {hash_input}")

# ─── Module 4: Password Cracker ──────────────────────────
def run_cracker():
    # Check if john is installed
    check = subprocess.run(["which", "john"], capture_output=True, text=True)
    if check.returncode != 0:
        print("[-] John the Ripper is not installed.")
        print("[*] Install it with: sudo apt install john")
        return

    hash_file = input("Enter path to hash file: ")
    if not os.path.exists(hash_file):
        print(f"[-] File not found: {hash_file}")
        return

    has_wordlist = input("Do you have a wordlist? (yes/no): ").lower()
    if has_wordlist == "yes":
        wordlist = input("Enter path to wordlist: ")
        if not os.path.exists(wordlist):
            print(f"[-] Wordlist not found: {wordlist}")
            print("[*] To extract rockyou: sudo gunzip /usr/share/wordlists/rockyou.txt.gz")
            return
        os.system(f"john {hash_file} --wordlist={wordlist}")
    else:
        print("[*] Running john with built-in wordlist...")
        os.system(f"john {hash_file}")

# ─── Main Loop ────────────────────────────────────────────
while True:
    banner()
    choice = input("Select module: ")

    if choice == "1":
        run_scanner()
    elif choice == "2":
        run_recon()
    elif choice == "3":
        run_hashid()
    elif choice == "4":
        run_cracker()
    elif choice == "5":
        print("Exiting...")
        break
    else:
        print("[-] Invalid choice")

    input("\nPress Enter to return to menu...")
