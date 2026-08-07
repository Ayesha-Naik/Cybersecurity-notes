# Class 15 — SSH aur SSHD (detail mein)

## 1. SSH kya hai?
**SSH = Secure Shell.** Ye ek **mehfooz (secure) tareeqa** hai jisse tum door (remote) ke computer ya server ko apne terminal se control kar sakti ho — jaise wo tumhare saamne ho.

**Sabse zaroori baat:** SSH ka connection **encrypted (band-mutthi jaisा)** hota hai — beech mein koi tumhara data padh nahi sakta. Isi liye naam mein "Secure" hai.

**Example:** Socho ek server doosre sheher ya mulk mein hai. Tum ghar baithe SSH se us server mein login kar ke usme commands chala sakti ho — bilkul jaise tumhare saamne rakha ho. Aur jo bhi baat hoti hai wo mehfooz (koi sun/padh nahi sakta) rehti hai.

**SSH kyun important hai (cyber ke liye)?**
- Servers ko **door se control** karne ka standard tareeqa
- Bank/company ke servers, cloud (AWS), sab SSH se manage hote hain
- Mehfooz hai — isi liye Telnet (purana, unsafe) ki jagah aaj SSH use hota hai

**SSH ka default port = 22**

---

## 2. SSH ki basic commands
```bash
ssh username@ip                  # remote computer mein login karo
ssh ayesha@192.168.1.10          # ayesha naam se us IP wale computer mein login
ssh username@ip -p 2222          # agar port alag ho (jaise 2222) to -p se batao
ssh -i mykey.pem user@ip         # key file se login (password ke bajaye)
exit                             # SSH session se bahar aao (wapas apne computer)
```

**Kaam:**
- `ssh user@ip` = login karo
- `-p` = alag port ho to batao
- `-i` = key file se login
- `exit` = bahar aao

**Example:** `ssh ayesha@192.168.1.10` → password poochega → sahi password → tum us door wale computer mein aa gayi, ab usme commands chala sakti ho.

---

## 3. SSH Keys kya hain? (password ke bina login)
Har baar password likhne ke bajaye, SSH **keys** se login kar sakti ho — ye zyada mehfooz aur aasaan hai.

**2 keys hoti hain (jodi):**
- **Private key** = tumhare paas rehti hai (secret, kisi ko nahi deni) — ye taala kholne wali **chaabi**
- **Public key** = server pe rakhi jaati hai — ye **taala**

**Kaise kaam karti hain?** Jodi milti hai — tumhari private chaabi server ke public taale se match ho, to login ho jata hai. Password ki zaroorat nahi.

**Key banane aur bhejne ki commands:**
```bash
ssh-keygen                        # nayi key jodi (public + private) banao
ssh-copy-id user@ip               # apni public key server pe bhejo
ssh user@ip                       # ab bina password login (key se)
```

**Keys kahan rehti hain?**
- Private key: `~/.ssh/id_rsa` (chupi, secret)
- Public key: `~/.ssh/id_rsa.pub` (ye share hoti hai)

**Purpose (keys ka faida):**
- Har baar password nahi likhna (aasaan)
- Zyada mehfooz (password chori ho sakta, key mushkil)
- Automation mein kaam (bina ruke commands chal saken)

**Example:** Jaise ghar ki chaabi — tumhare paas chaabi (private key) hai, ghar pe taala (public key) laga hai. Chaabi lagao, ghar khul gaya — har baar password (guard se poochna) ki zaroorat nahi.

---

## 4. SSHD kya hai?
**SSHD = SSH Daemon.** "Daemon" ka matlab = ek **background service** jo hamesha chupke chalti rehti hai.

Simple lafzon mein: **SSHD wo service hai jo server pe chalti hai aur SSH connections ka intezaar karti hai.** Jab koi tumhare server pe SSH se aana chahe, SSHD use sunta hai aur andar aane deta hai (agar sahi ho).

**Farak (SSH vs SSHD):**
- **SSH** = tum (client) — jo **jaati** ho doosre computer mein (login karne wala)
- **SSHD** = server pe chalti **service** — jo aane walon ka **intezaar** karti aur andar aane deti hai

**Example:** SSH tum ho jo **hotel mein aati** ho. SSHD hotel ka **receptionist** hai jo darwaze pe baitha hai — jab tum aati ho, wo tumhe check karke andar aane deta hai. Bina receptionist (SSHD) ke koi andar nahi aa sakta.

---

## 5. SSHD ki commands (service control)
SSHD ek service hai, isliye **systemctl** se control hoti hai:
```bash
sudo systemctl status ssh      # SSHD chalu hai ya nahi, dekho
sudo systemctl start ssh       # SSHD service chalu karo
sudo systemctl stop ssh        # SSHD band karo
sudo systemctl restart ssh     # band karke dobara chalu
sudo systemctl enable ssh      # computer on hote hi SSHD apne aap chalu ho
sudo systemctl disable ssh     # apne aap chalu hona band
```

**Note:** kabhi service ka naam `ssh` hota hai, kabhi `sshd` — dono chal sakte hain (`systemctl status sshd` bhi try kar sakti ho).

---

## 6. SSHD ki settings (configuration)
SSHD ki settings ek file mein hoti hain:
```
/etc/ssh/sshd_config
```
Is file mein SSH ke rules hote hain — jaise port kya ho, root login allow ho ya nahi, password login ho ya sirf key.

```bash
sudo nano /etc/ssh/sshd_config    # SSHD ki settings edit karo
sudo systemctl restart ssh        # settings badalne ke baad ye zaroori (taake naya lagu ho)
```

**Kuch aam settings (is file mein):**
- `Port 22` → SSH kaunse port pe chale (security ke liye badal sakti ho)
- `PermitRootLogin no` → root ko seedha login se roko (zyada safe)
- `PasswordAuthentication no` → sirf key se login, password band (aur safe)

**Yaad rakho:** settings badalne ke baad **hamesha `restart ssh`** karo, warna naya change kaam nahi karega.

---

## 7. Keys aur Purpose — ek nazar mein
| Cheez | Kya hai | Purpose |
|-------|---------|---------|
| SSH | client (jaane wala) | door ke computer mein secure login |
| SSHD | server ki service | aane walon ko sunna/andar aane dena |
| Private key | tumhari secret chaabi | login karo (kisi ko na do) |
| Public key | server pe rakha taala | private key se match ho to login |
| Port 22 | SSH ka default darwaza | connection yahin se hota |
| /etc/ssh/sshd_config | SSHD ki setting file | rules (port, login) badalne ke liye |

---

## Quick revision:
- **SSH** = door ke computer ko secure control (client)
- **SSHD** = server ki service jo SSH connections sunti hai (receptionist)
- **Keys** = private (secret chaabi) + public (taala) — password ke bina safe login
- **Commands:** `ssh user@ip` (login), `ssh-keygen` (key banao), `systemctl start ssh` (service)
- **Settings:** `/etc/ssh/sshd_config` (edit ke baad `restart ssh`)
- **Port 22** = SSH ka default darwaza
