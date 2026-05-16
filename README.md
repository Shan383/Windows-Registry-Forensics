# 🧠 Windows Registry Forensics – Mantooth Case (USERPROF, SYSTEM, SAM, SOFTWARE)

## 📌 Project Overview
This repository contains a complete Windows registry analysis of the Mantooth.E01 forensic image. Five registry hives (SYSTEM, SAM, SOFTWARE, NTUSER.DAT, USRCLASS.DAT) were extracted and parsed to uncover user activity, encryption tools, USB history, and evidence of financial fraud.

## 🛠️ Tools Used
- **Registry Explorer (Eric Zimmerman)** – Primary registry parsing
- **RegRipper** – Automated registry artifact extraction
- **FTK Registry Viewer** – Cross-reference validation
- **Custom Python scripts** – RunMRU and USB history parsing

## 🎯 Key Findings Summary

### 1. System Information
| Artifact | Value |
|----------|-------|
| Computer Name | WESMANTOTOP-PC |
| Time Zone | Mountain Time (UTC-7 / UTC-6 DST) |
| Registered Owner | Wes Mantooth |
| Registered Organization | Volturi Enterprises |
| OS Install Date | 2007-02-27 |
| Product ID | [Extracted from SOFTWARE hive] |

### 2. User Accounts (SAM Analysis)
| Username | Account Type | Created | Last Login | Password Hint |
|----------|--------------|---------|------------|---------------|
| Wes Mantooth | Administrator | 2007-02-27 | 2007-03-07 | None |
| dracula | Standard | 2007-03-06 | Never | None |
| Laurent | Standard | 2008-02-12 | Never | None |

### 3. Encryption & Anti-Forensic Tools
| Tool | Registry Location | Start Type | Significance |
|------|-------------------|------------|---------------|
| TrueCrypt | SYSTEM\ControlSet001\Services\TrueCrypt | 1 (System) | Full disk/container encryption |
| WinVNC | SOFTWARE\ORL\WinVNC3\Password | Obfuscated | Remote access with recoverable password |
| AccessData DNA | SOFTWARE\AccessData\DNA Worker | Installed | Password cracking software |

### 4. USB Device History (SYSTEM\CurrentControlSet\Enum\USBSTOR)
| Device | Serial Number | Last Write Time | Drive Letter |
|--------|---------------|-----------------|--------------|
| Apple iPod | 000A2700148302AB | 2007-07-14 | G: |
| Sony DSC Camera | 5D4C33421A23 | 2007-08-01 | H: |
| Generic USB Drive | 07A6031200B10D | 2007-07-20 | E: |
| Generic USB Drive | 8C5713D7 | 2007-07-25 | F: |
| SanDisk Cruzer | 20060809210A | 2007-08-15 | Not assigned |

### 5. Network Artifacts (SYSTEM\ControlSet001\Services\Tcpip\Parameters\Interfaces)
- **Last Assigned IP:** 192.168.1.106
- **DHCP Server:** 192.168.1.1
- **Subnet Mask:** 255.255.255.0
- **Default Gateway:** 192.168.1.1
- **DHCP Domain:** hsdl.co.comcast.net (Comcast residential ISP)

### 6. Wireless Network Profile
| Profile Name | SSID | Security |
|--------------|------|----------|
| linksys | linksys | WEP (vulnerable) |

### 7. Program Execution (RunMRU – NTUSER.DAT)
| Command | Executed |
|---------|----------|
| regedit | 2008-02-12 19:28:02 |
| devmgmt.msc | (not recorded) |
| calc | (not recorded) |
| c:\gdisk\32.exe | (not recorded) |
| msconfig | (not recorded) |

### 8. Recent Documents (RecentDocs – NTUSER.DAT)
| File Name | Path | Status |
|-----------|------|--------|
| How To Steal Credit Numbers.doc | Windows Mail Inbox | ENCRYPTED |
| ATM_THEFTS1.ppt | E:\Business Ideas | MISSING |
| BitLocker key file | Desktop | Reference only |

### 9. Email Addresses Found in Registry
| Email Address | Source Location |
|---------------|-----------------|
| mantooth2007@aol.com | NTUSER.DAT (AOL config), ntuser.dat.LOG1 |
| chkwasher@comcast.net | NTUSER.DAT (RecentDocs) |
| smee.rox@gmail.com | NTUSER.DAT (RecentDocs) |
| dollyrhde86@comcast.net | DHCP lease (ISP) |

### 10. Internet Explorer Artifacts
| Artifact | Value |
|----------|-------|
| Default Browser | Internet Explorer |
| Start Page | http://www.google.com |
| Download Directory | C:\Users\Wes Mantooth\Downloads |
| Typed URLs | google.com, aol.com, comcast.net |

### 11. Yahoo Messenger Username
