
## Configuration Values
| Value Name | Data | Interpretation |
|------------|------|----------------|
| Start | 1 (RegDword) | System-level service (boot start) |
| Type | 1 (RegDword) | Kernel device driver |
| ErrorControl | 1 (RegDword) | Normal error handling |
| ImagePath | \??\C:\Program Files\TrueCrypt\TrueCrypt.sys | Driver location |
| DisplayName | TrueCrypt | Service display name |
| Group | Boot Bus Extender | Loads early in boot process |

## What Start = 1 Means
- **System-level service:** TrueCrypt loads at boot time (not manual/user-triggered)
- **Kernel driver:** Runs with highest privileges (Ring 0)
- **Persistence:** Survives reboots without user interaction
- **Common scenarios:** Full disk encryption, system encryption, hidden volumes

## Forensic Significance

### Primary Implications:
1. **Full Disk Encryption Likely** – System-level service suggests entire drive or system partition encrypted
2. **Hidden Volumes Possible** – TrueCrypt supports plausible deniability with hidden containers
3. **Data Inaccessible Without Password** – Decryption requires password or keyfile
4. **Counter-Forensic Awareness** – Subject deliberately used encryption to prevent examination

### Correlated Evidence:
- BitLocker key file referenced in RecentDocs (encryption alternative)
- Encrypted document "How To Steal Credit Numbers.doc" found in Windows Mail
- CameraShy.exe steganography tool present (pattern of concealment)

## Investigative Next Steps

### Priority 1: Password Recovery
- Interview subject for password disclosure
- Memory analysis (if RAM capture available)
- Dictionary/brute-force attacks against TrueCrypt header
- Keyfile search on system (look for *.key, *.tc, *.vol)

### Priority 2: Container Location
- Search for files with no extension or large file sizes
- Look for `.tc` or `.vol` extensions
- Examine unallocated space for TrueCrypt headers

### Priority 3: Timeline Correlation
- Installation date of TrueCrypt (from SOFTWARE hive uninstall keys)
- First use vs. suspicious activity dates
- Deletion/shredding attempts

## Technical Reference
- TrueCrypt (discontinued 2014, but still in use)
- Successor: VeraCrypt
- Recovery tools: Hashcat (mode 13711-13773), John the Ripper, tcplay
