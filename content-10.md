# Class 10 — File Permissions aur chmod

## 1. Linux mein 2 tarah ke users
- **Basic user (normal user)** — aam user, limited power, apna kaam karta hai
- **Root user (super user)** — computer ka boss, poori power, kuch bhi kar sakta hai

---

## 2. File Permissions kya hain?
Linux mein har file/folder pe **permission** hoti hai — yani kaun us file ko **padh, likh ya chala** sakta hai. Ye Linux ki security ka dil hai.

**3 tarah ki permission (kaam):**
- **r = read** → file **padhna**
- **w = write** → file **likhna/badalna**
- **x = execute** → file **chalana** (jaise koi program/script)

**3 tarah ke log (kis ke liye):**
- **Owner (maalik)** → jisne file banayi
- **Group (team)** → ek group ke log
- **Others (baaki sab)** → aur sab

Yani har file pe 3 log × 3 kaam = permission ka poora structure banta hai.

---

## 3. Permission dekhna (structure samjho)
Permission dekhne ke liye:
```bash
ls -l file.txt
```
Ye kuch aisa dikhega:
```
-rwxr-xr--
```

Isko break karo (9 letters, 3-3 ke teen hisse):
```
-   rwx      r-x      r--
|   |        |        |
type owner   group    others
```
- Pehla `-` = file type (`-` file, `d` folder)
- `rwx` = **owner** → read + write + execute ,teeno (poori power)
- `r-x` = **group** → read + execute (write nahi)
- `r--` = **others** → sirf read (padh sakte, aur kuch nahi)

Jahan permission na ho, wahan `-` (dash) hota hai.

---

## 4. Permission ke Numbers (sabse zaroori)
Har permission ka ek **number** hota hai:
- **read (r) = 4**
- **write (w) = 2**
- **execute (x) = 1**
- **kuch nahi = 0**

**Jorne se permission banti hai:**
- read + write + execute = 4 + 2 + 1 = **7** (poori permission)
- read + write = 4 + 2 = **6**
- read + execute = 4 + 1 = **5**
- sirf read = **4**
- kuch nahi = **0**

**Example samjho — `chmod 754`:**
Ye 3 number, teen logon ke liye (owner, group, others):
- **7** (owner) = 4+2+1 = read + write + execute (poori power)
- **5** (group) = 4+1 = read + execute (write nahi)
- **4** (others) = sirf read

Yani `754` ka matlab: owner sab kuch kar sakta, group padh+chala sakta, others sirf padh sakta.

**Aur example:**
- `chmod 777` = sabko poori permission (owner, group, others — sab 7) ⚠️ khatarnak
- `chmod 700` = sirf owner ko poori, baaki kisi ko kuch nahi
- `chmod 644` = owner padh+likh (6), group padh (4), others padh (4)

---

## 5. chmod command
**chmod** = **Ch**ange **Mod**e — file/folder ki **permission badalne** wali command.

**Do tareeqe se chalti hai:**

### (1) Numbers se (jo abhi seekha):
```bash
chmod 755 file.sh    # owner=7, group=5, others=5
chmod 777 file.txt   # sabko poori permission
chmod 644 file.txt   # owner padh+likh, baaki sirf padh
chmod 700 secret.txt # sirf owner ko sab, baaki kisi ko kuch nahi
```

### (2) Letters se (aasaan tareeqa):
```bash
chmod +x file.sh     # file ko chalane-layak (execute) banao
chmod -x file.sh     # execute permission hatao
chmod +r file.txt    # read permission do
chmod +w file.txt    # write permission do
chmod u+x file.sh    # sirf owner (u=user) ko execute do
chmod g+w file.txt   # group ko write do
chmod o-r file.txt   # others se read hatao
```
Yahan: `u` = user/owner, `g` = group, `o` = others. `+` = do, `-` = hatao.

---

## 6. Kaam ke chmod examples (rozana ke)
```bash
cat file.txt         # file ka content dekhna
ls -l file.txt       # abhi ki permission check karna
chmod u+x file.sh    # owner ko execute permission dena
chmod 770 file.txt   # owner aur group ko poori permission
chmod +x script.sh   # script ko chalane-layak banana
```

**Example:** Tumne ek script `script.sh` banayi, par wo chalti nahi (kyunki execute permission nahi). Bas `chmod +x script.sh` chalao — ab wo chalne-layak ho gayi.

---

## Yaad rakhne ka short
- **r=4, w=2, x=1, kuch nahi=0**
- Jod kar number banao: 7 = sab, 6 = padh+likh, 5 = padh+chala, 4 = sirf padh
- 3 number = owner, group, others (is tarteeb mein)
- `chmod +x` = chalane-layak banao (sabse aam)

---

## Quick Revision:
| Cheez | Matlab |
|-------|--------|
| r / w / x | read(4) / write(2) / execute(1) |
| owner / group / others | maalik / team / baaki sab |
| `ls -l` | permission dekho |
| chmod | permission badlo |
| 7 = 4+2+1 | poori permission |
| 4 = sirf read, 0 = kuch nahi | |
| chmod +x | file chalane-layak banao |
| 777 / 700 / 644 | sabko sab / sirf owner / normal file |
