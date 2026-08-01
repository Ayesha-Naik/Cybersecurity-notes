# Lecture 06 — File Read, echo, Operators aur Wildcards

## 1. File ko read (parhne) ki commands
File ke andar ka text dekhne ke liye kai commands hain — har ek ka apna tareeqa:

```bash
cat file.txt          # poori file ek saath dikhata hai
tac file.txt          # poori file ULTI dikhata hai (aakhri line se pehli tak)
head file.txt         # sirf pehli 10 lines dikhata hai
tail file.txt         # sirf aakhri 10 lines dikhata hai
less file.txt         # badi file ko page-by-page dikhata hai (scroll karke padho, q se bahar)
more file.txt         # less jaisa - thoda thoda karke dikhata hai.
```

**Naam aur working:**
- `cat` = **Concatenate** — poori file dikhao (chhoti file ke liye best)
- `tac` = **cat ka ulta** (naam bhi ulta) — file neeche se upar dikhata
- `head` = file ka **sar (upar wala hissa)** — pehli 10 lines
- `tail` = file ka **poonch (neeche wala hissa)** — aakhri 10 lines
- `less` / `more` = badi file page-by-page (jab file itni badi ho ke ek screen mein na aaye)

### head aur tail ke saath number (custom lines):
```bash
head -5 file.txt      # sirf pehli 5 lines dikhao
tail -5 file.txt      # sirf aakhri 5 lines dikhao
tail -f file.txt      # LIVE - file mein jo naya add ho wo turant dikhta rahe
```

**Yaad rakho:**
- `head -5` / `tail -5` = pehli/aakhri **5** lines (number apni marzi ka)
- `tail -f` = **follow** — live dekho (logs check karne ke liye bohat kaam ka!)

**Example:** Ek badi log file hai (1000 lines). Poori dekhne ki zaroorat nahi — `tail -10` se aakhri 10 (naye) dekho, ya `tail -f` se live dekho ke naya kya add ho raha hai.

---

## 2. echo command
`echo` = screen pe ya file mein **text likhna/dikhana.**

```bash
echo "Hello"                    # screen pe "Hello" dikhata hai
echo "Hello" > file.txt         # nayi file bana kar usme "Hello" likhta hai
echo "World" >> file.txt        # file mein "World" line add karta hai (purana rehta)
echo $USER                      # abhi ka username dikhata hai
echo $PWD                       # abhi kis folder mein ho wo dikhata hai
```

**Yaad rakho:**
- `echo "text"` = screen pe dikhao
- `echo "text" > file` = file mein daalo (naya)
- `echo "text" >> file` = file mein add karo (purana rehta)
- `$USER`, `$PWD` = system ki value (naam, folder) dikhata

---

## 3. Operators (redirection ke sign)
Ye khaas nishaan hain jo batate hain data **kahan jaye ya kahan se aaye.**

```bash
>       # output ko file mein daalo (file NAYI banti, purana mit jata)
>>      # output ko file mein ADD karo (purana rehta, neeche naya lagta)
<       # file se input lo (file ka data command ko do)
|       # ek command ka output doosri command ko do (pipe kehte hain)
```

**Ek-ek ka matlab:**
- **`>`** (single greater than) = file mein likho, **purana mita kar** naya daalo
  - `echo "hi" > file.txt` → file mein sirf "hi" (agar pehle kuch tha, gaya)
- **`>>`** (double greater than) = file mein **add** karo, purana rehne do
  - `echo "hi" >> file.txt` → purane text ke neeche "hi" lag gaya
- **`<`** (less than) = file ka data command ko do (input)
- **`|`** (pipe, jo `\` ke paas hota) = pehli command ka result doosri ko bhej do
  - `cat file.txt | grep "error"` → file dikha kar usme se "error" wali line nikaalo

**Yaad rakho:** `>` = naya likho, `>>` = add karo. Ye do sabse zyada use hote hain.

**Example:** `ls > list.txt` → is folder ki sari files ka naam `list.txt` mein save ho jayega (screen pe nahi, file mein).

---

## 4. Wildcards — Star (`*`) ki commands
`*` (star/asterisk) ek **wildcard** hai — iska matlab **"kuch bhi / sab kuch."** Isse ek saath kai files pe kaam kar sakti ho.

```bash
ls *.txt          # sari .txt files dikhao (naam kuch bhi ho)
rm *.log          # sari .log files delete karo
cp * backup/      # is folder ki SARI files backup folder mein copy karo
mv *.jpg photos/  # sari .jpg files photos folder mein move karo
rm *              # is folder ki SARI files delete (⚠️ dhyan se!)
```

**`*` ka matlab:**
- `*.txt` = jis naam ke aage `.txt` ho — sari (a.txt, b.txt, hello.txt sab)
- `*` akela = folder ki har file (sab)

**Star ke saath commands:**
- `cp *` = **sari** files copy karo
- `mv *.jpg` = **sari** jpg files move karo
- `rm *.log` = **sari** log files delete karo

**Example:** Folder mein 50 photos hain, sab move karni hain. Ek-ek nahi — `mv *.jpg photos/` se ek saath saari chali jayengi.

**⚠️ Dhyan:** `rm *` bohat khatarnak hai — folder ki **saari** files delete kar deta hai, wapas nahi aati. Star ke saath `rm` soch-samajh kar.

---

## Quick Revision:
| Topic | Ek line yaad |
|-------|--------------|
| cat / tac | poori file seedhi / ulti |
| head / tail | pehli / aakhri 10 lines |
| tail -f | live dekho (logs ke liye) |
| less / more | badi file page-by-page |
| echo | text screen pe ya file mein |
| `>` / `>>` | file mein naya / add |
| `\|` (pipe) | ek command ka result doosri ko |
| `*` (star) | "sab" — ek saath kai files pe kaam |
