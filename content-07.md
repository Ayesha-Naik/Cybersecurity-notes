# Class 07 — File Types, Hidden Files aur Session

## 1. Linux mein File ke different Types
Windows ki tarah Linux mein sab kuch "file" hi hota hai, par unke **types** alag hote hain. Har file ka ek nishaan (letter) hota hai jo `ls -l` command se dikhta hai:

```bash
ls -l        # files ko detail ke saath dikhao (type, size, date.
```

Jab `ls -l` chalao, to har line ke shuru mein ek letter hota hai — wahi file ka type batata hai:

- **`-`** = normal file (photo, text, document) — aam file
- **`d`** = directory (folder)
- **`l`** = link (shortcut, kisi doosri file ka raasta)
- **`c`** / **`b`** = device files (keyboard, disk jaise hardware ke liye)

**Example:** `ls -l` chalane pe agar line `-` se shuru ho to wo **normal file** hai. Agar `d` se shuru ho to wo **folder** hai.

**File ka type dekhne ka aur tareeqa:**
```bash
file filename    # ye batata hai file kis type ki hai (text, image, folder waghera)
```
Example: `file photo.jpg` → "JPEG image" batayega.

---

## 2. Hidden Files kya hain aur kaise dhoondein?
Kuch files **chupi (hidden)** hoti hain — normal `ls` se nazar nahi aati. Linux mein jis file ka naam **dot (`.`)** se shuru ho, wo hidden hoti hai (jaise `.bashrc`, `.config`).

**Kyun chupi hoti hain?** Ye aksar settings/system files hoti hain — taake galti se delete ya change na ho jayen.

**Hidden files dekhne ke liye:**
```bash
ls -a        # -a = all - sari files dikhao, hidden bhi (jo dot se shuru hon)
ls -la       # hidden + detail dono
```

**Yaad rakho:**
- `ls` = sirf normal files
- `ls -a` = **saari** files (hidden bhi) — `-a` = all
- Dot (`.`) se shuru naam = hidden file

**Example:** Tum `ls` chalao to 3 files dikhein. Phir `ls -a` chalao to 8 dikhein — kyunki 5 hidden thi (dot wali).

---

## 3. Session kya hai?
**Session** = jab tum login karti ho, se le kar logout tak ka poora **waqt.** Is beech jo bhi kaam karti ho (commands, files), wo us session ka hissa hota hai.

**Session se judi commands:**
```bash
whoami       # abhi tum kaun ho (kis user ka session)
who          # is waqt kaun-kaun log in hain
w            # kaun log in hain aur kya kar rahe hain
history      # is session mein jo commands chalayi, sab dikhao
exit         # session band karo (logout / terminal band)
```

**Yaad rakho:**
- `whoami` = main kaun hoon
- `who` / `w` = aur kaun log in hai
- `history` = ab tak jo commands chalayi
- `exit` = session khatam

**Example:** `history` chala kar dekh sakti ho ke aaj tumne kaunsi commands chalayi — cyber mein kisi ne kya kiya, ye check karne ke liye kaam aata hai.

---

## 4. Kuch aur zaroori commands (is class se related)
```bash
find . -name "*.txt"       # naam se file dhoondo
find . -type f             # sirf files
find . -type d             # sirf folders
find / -name "file.txt"    # poore system mein dhoondo
stat file.txt              # file ki poori detail (size, banne ka time waghera)
```

---

## Quick Revision:
| Topic | Ek line yaad |
|-------|--------------|
| File types | `-` file, `d` folder, `l` link (ls -l se dikhein) |
| Hidden files | dot (.) se shuru — `ls -a` se dikhein |
| Session | login se logout tak ka waqt |
| whoami / who / history | main kaun / aur kaun / kya chalaya |
| find | naam/type se file dhoondo |
