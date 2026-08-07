# Class 16 — tar, zip aur Backup

## 1. tar aur zip kya hain?
Dono files ko **ek saath baandhne aur chhota (compress) karne** wale tools hain.

**tar:**
- Kai files/folders ko **ek dabbe (single file)** mein baandh deta hai
- Us file ko `.tar` kehte hain
- Linux mein sabse zyada use hota hai (backup ke liye)

**zip:**
- Bhi files ko ek dabbe mein baandhta + **chhota (compress)** karta hai
- Us file ko `.zip` kehte hain
- Windows aur Linux dono mein chalta hai (isliye share karne ke liye acha)

**Kis liye use hote hain?**
- Kai files ko **ek file** mein baandhna (bhejne mein aasaan)
- File ko **chhota** karna (kam jagah, jaldi transfer)
- **Backup** banana (data safe rakhna)

**Example:** Socho tumhe 100 files kisi ko bhejni hain. Ek-ek bhejna mushkil. Sab ko ek `.zip` ya `.tar` mein baandh do → ab ek hi file, aur chhoti bhi — bhejna aasaan.

---

## 2. tar ke flags (options)
tar ke saath ye flags lagते hain:
```
c    # Create - naya tar banao
x    # Extract - tar khol do (files nikaalo)
v    # Verbose - kya ho raha hai, wo screen pe dikhao
f    # File - file ka naam batao (ye hamesha lagta hai)
z    # gzip se compress karo (.tar.gz banao - chhota)
t    # tar ke andar kya hai, list dekho (kholе bina)
```

**Yaad rakho:**
- `c` = create (banao)
- `x` = extract (kholo)
- `v` = verbose (dikhao)
- `f` = file naam
- `z` = compress (chhota)

---

## 3. Verbose (`v`) kya hai?
**Verbose = "sab kuch bol kar batao".** `v` lagane se command jo bhi kar rahi hoti hai, wo har file ka naam screen pe dikhati jaati hai — taake tumhe pata rahe kya ho raha hai.

**Example:**
- `tar -cf backup.tar folder` → chup-chaap kaam karega (kuch nahi dikhega)
- `tar -cvf backup.tar folder` → har file ka naam dikhata jayega (v = verbose)

**Yaad rakho:** `v` = dekho kya ho raha hai (screen pe naam aate rahenge).

---

## 4. tar ki commands (examples ke saath)
```bash
tar -cvf backup.tar myfolder      # banao - myfolder ko backup.tar mein baandho
tar -xvf backup.tar               # kholo - backup.tar se files nikaalo
tar -tvf backup.tar               # dekho - andar kya hai (khole bina list)
tar -czvf backup.tar.gz myfolder  # banao + compress (chhota .tar.gz)
tar -xzvf backup.tar.gz           # kholo (compressed wala)
```

**Har ek ka matlab:**
- `-cvf` = **c**reate + **v**erbose + **f**ile → naya tar banao
- `-xvf` = e**x**tract + verbose + file → kholo
- `-tvf` = lis**t** + verbose + file → andar dekho
- `-czvf` = create + **z**ip(compress) + verbose + file → chhota tar
- `-xzvf` = extract + zip + verbose + file → compressed kholo

**Example:** `tar -cvf notes.tar mynotes/` → "mynotes" folder ki sab files `notes.tar` mein baandh gayi. Har file ka naam screen pe dikha (v ki wajah se).

---

## 5. zip ki commands
```bash
zip backup.zip file1 file2       # file1 aur file2 ko backup.zip mein daalo
zip -r backup.zip myfolder       # poora folder zip karo (-r = recursive)
unzip backup.zip                 # zip khol do (files nikaalo)
unzip backup.zip -d myfolder     # zip ko us folder mein kholo
unzip -l backup.zip              # zip ke andar kya hai, dekho (khole bina)
```

**Zaroori:**
- `zip file.zip file` = zip banao
- `zip -r file.zip folder` = **poora folder** zip karo (`-r` zaroori folder ke liye)
- `unzip file.zip` = zip kholo

**Unzip karna kya hai?** Zip ek "band dabba" hai. **Unzip** = us dabbe ko **kholna** — andar ki sari files wapas nikaalna.
```bash
unzip backup.zip     # dabba khol diya, files bahar aa gayi
```

---

## 6. tar aur zip ek saath (example)
Kabhi pehle tar banate hain, phir use bhi zip kar dete hain:
```bash
tar -cvf notes.tar mynotes/      # step 1: folder ko tar mein baandho
zip notes.tar.zip notes.tar      # step 2: us tar ko zip (aur chhota) karo
```
Ya seedha ek command mein (tar khud compress kare):
```bash
tar -czvf notes.tar.gz mynotes/  # ek hi baar mein baandho + compress karo
```

**Yaad rakho:** `tar -czvf` = ek saath baandhna + chhota karna (sabse aasaan, aksar yehi use hota).

---

## 7. Backup kya hai?
**Backup** = apne zaroori data (files/folders) ki ek **extra copy** banana — taake agar asli data kharab/delete ho jaye, to backup se wapas mil jaye.

**Kyun zaroori?** Computer kharab ho, file galti se delete ho, ya virus aa jaye — backup ho to data safe rehta hai. Cyber mein backup bohat important hai.

**Example:** Jaise tum apne zaroori kaghazon ki photocopy bana kar alag rakhti ho — asli kho jaye to copy kaam aaye. Backup bhi wahi hai — data ki copy.

**Backup banane ki commands (tar se):**
```bash
tar -czvf backup.tar.gz /home/ayesha/documents   # documents ka backup banao
tar -xzvf backup.tar.gz                           # backup se data wapas nikaalo (restore)
cp -r myfolder myfolder_backup                    # seedha folder ki copy (simple backup)
```

**Yaad rakho:** backup = data ki extra copy. `tar -czvf` se backup banao, `tar -xzvf` se wapas laao (restore).

---

## Quick Revision:
| Cheez | Matlab |
|-------|--------|
| tar | files ko ek dabbe mein baandhna |
| zip | baandhna + chhota (compress) karna |
| c / x / v / f | create / extract / verbose / file |
| z | compress (.tar.gz) |
| verbose (v) | screen pe dikhao kya ho raha |
| unzip | zip kholna (files nikaalna) |
| tar -czvf | baandho + chhota karo (aam) |
| Backup | data ki extra copy (safety ke liye) |
