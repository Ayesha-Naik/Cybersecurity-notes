# Class 09 — find Options aur cat / tac / cut

## 1. find command ke options
`find` file ya folder **dhoondne** ke liye use hoti hai. Iske aage options lagते hain jo batate hain kya dhoondna hai.

**Note:** `.` (dot) ka matlab "abhi ke folder mein dhoondo".

```bash
find . -name "notes.txt"   # is naam ki file dhoondo
find . -type f             # sirf files dhoondo
find . -type d             # sirf folders dhoondo
find . -size +10M          # 10 MB se BADI files
find . -size -10M          # 10 MB se CHHOTI files
find . -mtime -1           # pichhle 1 din mein badli files
find . -mtime -7           # pichhle 7 din mein badli files
```

**Har option ka matlab:**

- **`-name`** = naam se dhoondo
  Example: `find . -name "*.log"` → sari .log files (`*` = kuch bhi naam)

- **`-type f`** = sirf files (f = **f**ile)
  **`-type d`** = sirf folders (d = **d**irectory)

- **`-size`** = size se dhoondo
  `+10M` = 10 MB se **badi** | `-10M` = 10 MB se **chhoti**
  Yaad rakho: `+` = badi, `-` = chhoti

- **`-mtime`** = file kab last badli (m = **m**odify **time**)
  `-1` = pichhle 1 din mein | `-7` = pichhle 7 din (hafte) mein

**Example:** Tumhe wo files chahiye jo 10 MB se badi hain — `find . -size +10M` chala do, sab badi files aa jayengi. Cyber mein aise hi suspicious/badi files dhoondi jaati hain.

---

## 2. cat, tac aur cut
Teeno alag kaam karte hain (naam milte-julte, kaam alag):

```bash
cat file.txt         # poori file ka text dikhao
tac file.txt         # poori file ULTI dikhao (aakhri line se pehli tak)
cut -c 1-5 file.txt  # har line ke pehle 5 letters dikhao
```

**Har ek ka matlab:**

- **`cat`** = poori file dikhao (sabse aam command)
  Example: `cat notes.txt` → notes.txt ka poora text

- **`tac`** = `cat` ka **ULTA** (naam bhi ulta likha hai) — file neeche se upar dikhata hai (aakhri line pehle)
  Yaad rakho: cat spelling ulti → kaam bhi ulta

- **`cut`** = file ki har line se koi **hissa** kaat kar dikhata hai (poori line nahi)
  `-c 1-5` = har line ke pehle 5 letters
  Example: agar line hai `Ayesha123`, to `cut -c 1-5` → `Ayesh` dikhega

---

## Quick Revision:
| Command | Kaam |
|---------|------|
| find -name | naam se dhoondo |
| find -type f / d | file / folder |
| find -size +10M / -10M | badi / chhoti |
| find -mtime -1 / -7 | 1 din / 7 din mein badli |
| cat | poori file (seedhi) |
| tac | poori file (ulti) |
| cut | line se hissa kaato |
