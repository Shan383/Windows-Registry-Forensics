
## What is WinVNC?
- **VNC (Virtual Network Computing)** – Remote desktop software
- **WinVNC** – Windows implementation
- **Ports:** 5900 (VNC), 5800 (HTTP Java client)
- **Legitimate use:** Remote administration
- **Abusive use:** Unauthorized access, persistent backdoor

## Password Obfuscation Method
WinVNC does NOT store passwords in plaintext or standard hash. Instead:
1. Password is obscured using a **known static DES key**
2. The key is embedded in the VNC binary (`e7 6d 6a 55 48 1f 6d 87`)
3. This is NOT a cryptographic hash – it's reversible

## Recovery Methods

### Method 1: vncpasswd.py
```bash
python vncpasswd.py -d -f password.bin
