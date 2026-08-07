# Class 17 — System Information Commands aur Logs

## 1. System Information Commands
Ye commands batati hain ke tumhare computer ka **haal kya hai** — disk kitni bhari, RAM kitni, CPU kaise, kitni der se on hai waghera. Cyber mein system check karne ke liye ye bohat kaam ki hain.

```bash
df           # disk (storage) kitni bhari, kitni khaali hai
du           # koi folder/file kitni jagah le raha hai
free         # RAM (memory) kitni use ho rahi, kitni free
uptime       # computer kitni der se on hai (aur load)
lscpu        # CPU ki poori detail (cores, speed)
uname -a     # system/OS ki poori info (kernel, version)
lsblk        # sari disks/drives aur unke hisse (partitions)
```

### Har command detail mein:

**`df` = Disk Free**
Batata hai tumhari disk (storage) kitni bhar chuki hai aur kitni khaali hai.
```bash
df -h        # -h = human readable (GB/MB mein saaf dikhao)
```
Example: `df -h` → dikhega "50 GB total, 30 GB use, 20 GB free". Yani disk full to nahi ho rahi.

**`du` = Disk Usage**
Batata hai koi **folder/file** kitni jagah le raha hai.
```bash
du -h myfolder    # ye folder kitni jagah le raha (saaf format mein)
du -sh myfolder   # -s = sirf total (ek line mein)
```
Example: `du -sh Downloads` → "2.5 GB Downloads" — matlab Downloads folder 2.5 GB le raha.

**`free` = free memory (RAM)**
Batata hai RAM kitni use ho rahi, kitni khaali.
```bash
free -h      # RAM saaf format mein (GB/MB)
```
Example: `free -h` → "8 GB total, 3 GB used, 5 GB free" — RAM ka haal.

**`uptime`**
Batata hai computer **kitni der se on** hai (kab se chal raha), aur kitna load hai.
Example: `uptime` → "up 3 hours, load average: 0.5" — 3 ghante se on hai.

**`lscpu` = list CPU**
CPU ki poori detail — kitne cores, speed, kaunsa model.
Example: `lscpu` → "4 cores, 2.5 GHz" jaisा dikhega.

**`uname -a` = Unix name (all)**
System/OS ki poori info — kernel ka version, OS ka naam, architecture (32/64 bit).
Example: `uname -a` → Linux version aur kernel ki detail dikhata.

**`lsblk` = list block devices**
Sari disks (hard disk, USB, SSD) aur unke hisse (partitions) dikhata hai.
Example: `lsblk` → sda, sda1, sda2 (disk aur uske hisse) — kaunsi drive kitni badi.

**Yaad rakhne ka short:**
- `df` = **d**isk **f**ree (storage)
- `du` = **d**isk **u**sage (folder ka size)
- `free` = RAM ka haal
- `uptime` = kitni der se on
- `lscpu` = CPU detail
- `uname -a` = OS/kernel info
- `lsblk` = disks aur partitions

---

## 2. Logs kya hain? (detail mein)
**Logs** = computer ki **diary.** System jo bhi kaam karta hai — kaun login hua, kaunsa program chala, koi error aayi, kis time kya hua — ye sab apne aap ek file mein likhta rehta hai. Inhi record wali files ko **logs** kehte hain.

**Kaise bante hain?** Tum kuch nahi karti — **system khud** har kaam ka record automatically likhta rehta hai. Jaise CCTV camera khud recording karta rehta hai, waise logs khud bante rehte hain.

**Example:** Tum computer on karti ho, login karti ho, ek app kholti ho. System peeche-peeche likhta jata hai:
```
2:30 PM - Ayesha login hui
2:31 PM - Chrome khula
2:35 PM - error: file na mili
2:40 PM - USB laga
```
Ye sab ek log file mein save hota rehta hai — tumhare bina.

**Kahan aur kyun use hote hain?**
- **Problem dhoondne** ke liye — kuch kharab ho to log dekh kar pata chalta hai kya aur kab hua
- **Security ke liye** — kisi ne galat login try kiya ya hack karne ki koshish ki, to log mein dikh jata hai
- **Cyber security mein bohat zaroori** — hackers ko pakadne aur system check karne ke liye logs padhe jaate hain

**Logs kahan rehte hain?**
Zyada tar logs is folder mein hote hain:
```
/var/log/
```

**Logs dekhne ki commands:**
```bash
ls /var/log              # sari log files ki list dekho
cat /var/log/syslog      # system ka poora log dekho
tail /var/log/syslog     # log ki aakhri (nayi) lines dekho
tail -f /var/log/syslog  # LIVE log dekho (jo naya add ho turant dikhe)
grep "error" /var/log/syslog   # log mein se sirf "error" wali lines nikaalo
journalctl               # system ka poora log (naya tareeqa)
journalctl -xe           # latest logs + error detail
```

**Sabse kaam ki 2 commands (yaad rakho):**
- `tail -f /var/log/syslog` → **live** log dekho (real-time kya ho raha)
- `grep "error" /var/log/syslog` → log mein se **error** dhoondo

**Example:** Kuch kharab ho gaya, samajh nahi aa raha kya. `tail -f /var/log/syslog` chalao → jab problem dohraogi to live dikhega error kya aa raha hai. Ya `grep "fail" /var/log/auth.log` se dekho kisne galat login try kiya (security check).

**Kuch important log files:**
- `/var/log/syslog` → system ke aam events
- `/var/log/auth.log` → login/security (kaun login hua, kaun fail hua)
- `/var/log/kern.log` → kernel (hardware) ke logs

**Yaad rakho:** Log = system ki apne aap banti diary. Cyber field mein logs padhna ek important skill hai — errors dhoondne aur hackers pakadne ke liye.

---

## Quick Revision:
| Command | Kaam |
|---------|------|
| df -h | disk kitni bhari/khaali |
| du -sh | folder kitni jagah le raha |
| free -h | RAM ka haal |
| uptime | kitni der se on |
| lscpu | CPU detail (cores) |
| uname -a | OS/kernel info |
| lsblk | disks aur partitions |
| Logs | system ki apne aap banti diary |
| /var/log/ | logs yahan rehte hain |
| tail -f / grep | live log / error dhoondo |
