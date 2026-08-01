# Class 12 — Processes, PID, ps/top, kill, systemctl aur Ports

## 1. Process kya hai? (yaad dilana)
**Process** = koi bhi program jo **abhi chal raha** ho. Chrome kholi = ek process. OS in sab ko sambhalta hai.

---

## 2. PID aur PPID
Har process ko ek **number** milta hai taake system use pehchaan sake.

**PID = Process ID** → har chalte process ka apna **unique number** (jaise har insaan ka CNIC).

**PPID = Parent Process ID** → jis process ne isko **shuru kiya** (parent), uska ID.

**Example:** Tumne terminal khola (PID = 100). Phir terminal se `nano` khola:
- `nano` ka **PID** = 205 (uska apna ID)
- `nano` ka **PPID** = 100 (terminal ne shuru kiya, isliye terminal iska parent)

Yani PID = "meri ID", PPID = "mujhe kisne shuru kiya".

---

## 3. Process ki Commands
```bash
ps aux          # system ke saare processes (PID ke saath)
top             # LIVE chalte processes dikhao (q se bahar)
echo $$         # abhi ke terminal ka PID
```

**Example:** `ps aux` chala kar dekh sakti ho system pe abhi kya chal raha hai — cyber mein suspicious process dhoondne ke liye kaam aata hai.

---

## 4. Foreground vs Background Process
**Foreground** = command **saamne (screen pe)** chale, terminal busy rahe:
```bash
nano file.txt    # jab tak nano khula, terminal busy
```

**Background** = command **peeche** chale, terminal free rahe. Command ke aage **`&`** lagao:
```bash
firefox &        # firefox background mein, terminal free
```

## 5. ps aur top mein farak
- **`ps`** = ek **photo (snapshot)** — us waqt ke processes dikha kar ruk jata hai
- **`top`** = **live video** — processes real-time badalte hue (CPU/RAM ke saath), `q` se bahar

**Ek line:** ps = photo (ek baar), top = live camera.

---

## 6. top command ki keys
Jab `top` chal raha ho, ye keys kaam ki hain:
```
q      # bahar aao (quit)
k      # process ko kill karo
M      # memory (RAM) ke hisaab se sort
P      # CPU ke hisaab se sort
Space  # turant refresh
```

---

## 7. kill command — process band karna
Koi process atak jaye ya band karna ho, to **kill** use hota hai:
bash```

kill <PID>          → PID (number) se process band karta hai
kill -9 <PID>       → forcefully (zabardasti) band karta hai
pkill <name>        → naam se process band karta hai
killall <name>      → us naam ke saare (sab) processes ek saath band karta hai

---

## 8. systemctl command
**systemctl** se hum **services** (background mein chalte system programs, jaise SSH, Apache, network) ko control karte hain — start, stop, check.

```bash
systemctl status ssh     # ssh service ka haal dekho (chalu hai ya nahi)
systemctl start ssh      # ssh service chalu karo
systemctl stop ssh       # ssh service band karo
systemctl restart ssh    # ssh service band karke dobara chalu karo
systemctl enable ssh     # computer on hote hi ssh apne aap chalu ho
systemctl disable ssh    # apne aap chalu hona band karo
```

**Yaad rakho:**
- `status` = haal dekho | `start` = chalu | `stop` = band
- `restart` = dobara chalu | `enable` = boot pe auto-chalu | `disable` = auto-chalu band

**Note:** aksar `sudo` lagana parta hai (jaise `sudo systemctl start ssh`) kyunki ye system-level kaam hai.

**Example:** SSH service chalu karni hai → `sudo systemctl start ssh`. Chalu hui ya nahi check → `systemctl status ssh`.

---

## 9. Ports kya hain?
**Port** = computer ka ek **darwaza (number)** jis se network ka data andar-bahar jaata hai. Har service ka apna port hota hai.

**Aam ports (yaad rakhne layak):**
- **22** = SSH (remote login)
- **80** = HTTP (website)
- **443** = HTTPS (secure website)
- **21** = FTP (file transfer)
- **53** = DNS

**Example:** Cyber mein `nmap` se dekhते hain kaunse ports khule hain — khula port ek "khula darwaza" hai jahan se koi andar aa sakta, isliye security check ke liye ports dekhna zaroori hai.

**Yaad rakho:** Port = network ka darwaza. Har service ka apna number (SSH=22, web=80/443).

---

## Qick Revision
| Cheez | Matlab |
|-------|--------|
| PID / PPID | process ka ID / parent ka ID |
| ps / top | photo / live video of processes |
| foreground / background | saamne / peeche (`&`) |
| kill / kill -9 / killall | id se / zabardasti / naam se band |
| systemctl | services start/stop/status |
| ports | network ke darwaze (SSH=22, web=80) |
