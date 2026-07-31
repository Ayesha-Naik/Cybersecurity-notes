# Class 08 — grep Command (poori detail)

## grep kya hai?
**grep** ka full name = **G**lobal **R**egular **E**xpression **P**rint.

Simple lafzon mein: **grep file ke andar se koi word ya line dhoondta hai.** Jaise Ctrl+F (find) hota hai — grep terminal ka find hai. Ye cyber security mein bohat use hota hai (logs mein error ya password jaisi cheezein dhoondne ke liye).

**Basic tareeqa:**
```bash
grep "word" file.txt      # file mein jis line mein "word" ho, wo dikhao
```
Example: `grep "error" log.txt` → sirf wo lines dikhega jinme "error" hai.

---

## grep ke saare flags (options)

```bash
grep -i "word" file       # Ignore case - chhota/bada letter ka farak ignore
grep -n "word" file       # Number - line number bhi dikhao
grep -v "word" file       # inVert - jin lines mein word NAHI hai, wo dikhao (ulta)
grep -c "word" file       # Count - word kitni baar aaya, ginti dikhao
grep -r "word" folder     # Recursive - folder ke andar SARI files mein dhoondo
grep -w "word" file       # Word - poora word match karo (aadha nahi)
grep -o "word" file       # Only - sirf matched word dikhao (poori line nahi)
grep -l "word" folder     # List - kaun si file mein word hai, sirf file ka naam
grep -A 2 "word" file     # After - match ke baad ki 2 lines bhi dikhao
grep -B 2 "word" file     # Before - match se pehle ki 2 lines bhi dikhao
grep -E "word1|word2" file # Extended - ek saath do word dhoondo (ya/or)
```

---

## Har flag ka matlab aur example

**`-i` = Ignore case (chhota/bada letter ignore)**
`Linux`, `linux`, `LINUX` — sab ko ek jaisa samajhta hai.
```bash
grep -i "linux" file.txt   # teeno (Linux, linux, LINUX) mil jayenge
```

**`-n` = line Number (kis line pe hai)**
Word kis line number pe hai, wo bhi batata hai.
```bash
grep -n "error" log.txt    # jawab: 5:error found (yani 5th line pe)
```

**`-v` = inVert (ulta)**
Jin lines mein word **NAHI** hai, sirf **wo** dikhata hai.
```bash
grep -v "error" log.txt    # sirf wo lines jinme "error" nahi hai
```

**`-c` = Count (ginti)**
Word kitni **baar** aaya, sirf number batata hai (line nahi).
```bash
grep -c "error" log.txt    # jawab: 3 (yani error 3 baar aaya)
```

**`-r` = Recursive (poore folder mein)**
Sirf ek file nahi — poore folder aur uske andar ki sab files mein dhoondta hai.
```bash
grep -r "password" /home   # /home folder ki har file mein "password" dhoondo
```

**`-w` = Word (poora word)**
Sirf **poora** word match karta hai, aadha nahi. `grep "cat"` to "category" bhi dhoond leta, par `grep -w "cat"` sirf poora "cat" dhoondta.
```bash
grep -w "cat" file.txt     # sirf "cat" (category, catch nahi)
```

**`-o` = Only (sirf word)**
Poori line nahi, sirf woh **matched word** dikhata hai.
```bash
grep -o "error" log.txt    # sirf "error" word dikhega, poori line nahi
```

**`-l` = List (file ka naam)**
Batata hai **kaunsi file** mein word mila (line nahi, sirf file naam).
```bash
grep -l "error" *.log      # kaunsi .log file mein "error" hai, uska naam
```

**`-A` / `-B` = After / Before (aas-paas ki lines)**
Match ke baad (`-A`) ya pehle (`-B`) ki lines bhi dikhata hai.
```bash
grep -A 2 "error" log.txt  # "error" wali line + uske baad ki 2 lines
grep -B 2 "error" log.txt  # "error" wali line + uske pehle ki 2 lines
```

**`-E` = Extended (ek saath kai word)**
`|` (pipe) ke saath ek se zyada word dhoond sakti ho.
```bash
grep -E "error|failed" log.txt   # "error" YA "failed" wali lines
```

---

## Flags ko jodna (ek saath 2 flag)
Kai flags ek saath bhi laga sakti ho:
```bash
grep -in "error" file      # ignore case + line number dono
grep -rn "password" /home  # poore folder mein + line number
grep -ic "error" file      # ignore case + count
```

---

## Yaad rakhne ka short trick
Pehla letter hi aksar matlab batata hai:
- `-i` = **I**gnore case
- `-n` = line **N**umber
- `-c` = **C**ount
- `-r` = **R**ecursive (folder)
- `-w` = **W**ord (poora)
- `-o` = **O**nly (sirf word)
- `-l` = **L**ist (file naam)
- `-v` = in**V**ert (ulta — v ko "reverse" soch lo)
- `-A` = **A**fter, `-B` = **B**efore

---

## Quick Revision:
| Flag | Kaam |
|------|------|
| `grep "word" file` | word wali line dhoondo |
| `-i` | chhota/bada letter ignore |
| `-n` | line number dikhao |
| `-v` | ulta (jisme word nahi) |
| `-c` | ginti (kitni baar) |
| `-r` | poore folder mein dhoondo |
| `-w` | poora word match |
| `-o` | sirf word dikhao |
| `-l` | kaunsi file mein hai |
| `-A / -B` | baad/pehle ki lines |
| `-E` | ek saath kai word (ya/or) |
