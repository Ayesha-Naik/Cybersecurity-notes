# Class 11 — chmod Symbols, Folder&file Permissions with chmod, chown aur chgrp

## 1. chmod ka Symbolic tareeqa (letters se)
Pichhli class mein numbers (755, 644) se permission di thi. Ab **letters** se — ye zyada aasaan aur seedha hai.

**Kis ke liye (log):**
- **u** = user (owner/maalik)
- **g** = group (team)
- **o** = others (baaki sab)
- **a** = all (sab — u, g, o teeno ek saath)

**Kya karna (operator):**
- **`+`** = permission **do (add)**
- **`-`** = permission **hatao (remove)**
- **`=`** = permission **exactly set karo** (sirf yehi rahe, baaki hat jaye)

**Kaunsi permission (r/w/x):**
- **r** = read, **w** = write, **x** = execute

**Formula:** `chmod [kis ke liye][operator][permission] file`

---

## 2. File Permissions — chmod examples
```bash
chmod u+x run.sh     # owner ko execute permission DO
chmod g-w file.txt   # group se write permission HATAO
chmod o+r file.txt   # others ko read permission do
chmod a-r file.txt   # sab se read hatao
chmod u+rwx run.sh   # owner ko poori (read+write+execute) do
chmod u=rwx run.sh   # owner ko sirf ye 3 set karo (baaki reset)
chmod +x run.sh      # sabko execute do (bina u/g/o likhe = sab)
```

**Har ek ka matlab :**
- **Permission add karna:**             `chmod u+x run.sh` → owner ko execute do
- **Group se permission remove karna:** `chmod g-w file.txt` → group se write hatao
- **Read permission dena:**             `chmod o+r file.txt` → others ko read do
- **Group ko write dena:**              `chmod g+w file.txt` → group ko write do
- **Owner ko wapas execute dena:**      `chmod u+x run.sh`
- **Owner se write hatana:**            `chmod u-w file.txt`
- **Owner ko poori permission dena:**   `chmod u+rwx file.txt` (ya `chmod u=rwx file.txt`)

**Example:** Tumne `run.sh` banayi par chalti nahi. `chmod u+x run.sh` chalao → owner (tum) ko execute mil gaya, ab chal jayegi.

**Yaad rakho:**
- `+` = do, `-` = hatao, `=` = sirf yehi set
- `u` owner, `g` group, `o` others, `a` sab

---

## 3. Folder Permissions
Folder pe bhi permission hoti hai, par thoda alag matlab:
- **r (read)** = folder ke andar ki list dekh sako (`ls` chal sake)
- **w (write)** = folder mein file bana/delete kar sako
- **x (execute)** = folder ke **andar ja sako** (`cd` chal sake)

**Zaroori baat:** folder mein jaane ke liye **x (execute) zaroori** hai. Sirf read ho aur execute na ho, to `cd` nahi chalega.

**Folder ke chmod examples:**
```bash
chmod u+x myfolder     # owner folder ke andar ja sake (cd)
chmod g+rx myfolder    # group folder dekh + andar ja sake
chmod 755 myfolder     # owner=sab, group+others=dekho+andar jao
chmod -R 755 myfolder  # folder + andar ki SARI cheezon pe (R = recursive)
```

**Note:** folder pe permission lagao to aksar **`-R`** (recursive) use karte hain — taake andar ki sab files/folders pe bhi lag jaye.

---

## 4. chown — Change Owner (maalik badalna)
**chown** = **Ch**ange **Own**er — file/folder ka **maalik (owner)** badalne wali command.

```bash
chown ayesha file.txt        # file.txt ka owner "ayesha" bana do
sudo chown root file.txt     # owner root bana do (sudo lagega)
chown ayesha:team file.txt   # owner "ayesha" aur group "team" dono set
chown -R ayesha myfolder     # folder + andar sab ka owner badlo
```

**Example:** Ek file ka owner koi aur hai, tum use apne naam karna chahti ho → `sudo chown ayesha file.txt`.

---

## 5. chgrp — Change Group (group badalna)
**chgrp** = **Ch**ange **Gr**ou**p** — file/folder ka **group** badalne wali command.

```bash
chgrp team file.txt          # file.txt ka group "team" bana do
sudo chgrp admin file.txt    # group "admin" bana do
chgrp -R team myfolder       # folder + andar sab ka group badlo
```

**Farak (chown vs chgrp):**
- **chown** = **owner** (maalik) badlo
- **chgrp** = sirf **group** badlo
- (chown se dono ek saath bhi: `chown owner:group file`)

---

## Yaad rakhne ka short
- **u/g/o/a**   = user / group / others / all
- **+ / - / =** = do / hatao / sirf-yehi-set
- **r/w/x**     = read / write / execute
- Folder mein jaane ke liye **x** zaroori
- **chmod**     = permission badlo
- **chown**     = owner badlo
- **chgrp**     = group badlo

---

## Quick Revision:
| Command | Kaam |
|---------|------|
| chmod u+x file   | owner ko execute do |
| chmod g-w file   | group se write hatao |
| chmod o+r file   | others ko read do |
| chmod u=rwx file | owner ko sirf ye 3 set |
| chmod -R 755 folder | folder + andar sab pe |
| chown ayesha file | owner badlo |
| chgrp team file   | group badlo |
