# Class 05 — Root vs User Level, sudo, Logs aur Commands

## 1. Root Level aur User Level kya hain?

**User Level (aam user):**
Ye normal user hota hai — roz ka kaam karta hai (files banana, apps chalana). Iske paas **limited power** hoti hai. System ki zaroori (important) cheezein ye chhoo nahi sakta — taake galti se kuch kharab na ho.

**Root Level (admin/super user):**
Ye computer ka **maalik (boss)** hota hai — ise **poori power** hoti hai. Ye kuch bhi kar sakta hai: system files badalna, software install/delete karna, koi bhi setting change karna.

### Farak — Root vs User
- **User** = limited power, sirf apna kaam. Zaroori system cheezein nahi chhoo sakta.
- **Root** = poori power, sab kuch kar sakta hai (banana, mitana, badalna).

**Example:** User ek **hotel ka guest** hai — apne kamre mein kaam kar sakta hai, par kitchen ya office nahi ja sakta. Root **hotel ka manager** hai — har kamre, kitchen, office — har jagah ja sakta hai. Isi liye root wali power soch-samajh kar use karni chahiye.

---

## 2. Request user se root level tak kaise jati hai?
Jab aam user koi aisa kaam karna chahe jiske liye **zyada power** chahiye (jaise software install), to:

1. User command deta hai
2. System dekhta hai: "iske liye to root ki power chahiye"
3. User ko **`sudo`** lagana parta hai (yani "root ki tarah ye kaam karo")
4. System **password** poochta hai (pakka karne ke liye ke user ke paas ijazat hai)
5. Sahi password → kaam ho jata hai (root ki power se)

**Example:** Guest (user) ko kitchen jaana hai. Wo manager (root) se ijazat maangta hai (`sudo`), manager ID check karta hai (password), phir jaane deta hai. Yani user thori der ke liye root ki power udhaar leta hai.

---

## 3. Root aur User Level ki Commands
```bash
whoami         # abhi tum kaun ho? (user ya root) - naam batata hai
sudo command   # ye command root ki power se chalao (password maangega)
sudo -i        # poori tarah root ban jao (ab har command root ki power se)
exit           # root se wapas normal user pe aa jao (ya terminal band karo)
```

**Yaad rakho:**
- `whoami` = main kaun hoon (user ya root)
- `sudo` = sirf ek command root ki power se chalao
- `sudo -i` = poore root ban jao (har command root)
- `exit` = root se bahar aao / wapas user

**⚠️ Dhyan:** `sudo` wali power khatarnak hoti hai — galat command se system kharab ho sakta hai. Isliye soch-samajh kar use karo.

---

## 4. Logs kya hote hain aur kaise kaam karte hain?
**Logs** = computer ki **diary.** System jo bhi kaam karta hai — kaun login hua, kaunsa program chala, koi error aayi, kis time kya hua — ye sab apne aap ek file mein likhta rehta hai. Inhi record wali files ko **logs** kehte hain.

**Kaise bante hain?** Tum kuch nahi karti — **system khud** har kaam ka record automatically likhta rehta hai. Jaise CCTV camera khud recording karta rehta hai, waise logs khud bante rehte hain.

**Example:** Socho tum computer on karti ho, login karti ho, ek app kholti ho. System peeche-peeche likhta jata hai:
- "2:30 PM - Ayesha login hui"
- "2:31 PM - Chrome khula"
- "2:35 PM - error: file na mili"

Ye sab ek log file mein save hota rehta hai.

**Logs Kahan aur kyun or kese use hote hain?**
- **Problem dhoondne** ke liye — kuch kharab ho to log dekh kar pata chalta hai kya aur kab hua
- **Security** ke liye — kisi ne galat login try kiya ya hack karne ki koshish ki, to log mein dikh jata hai
- **Cyber security mein bohat zaroori** — hackers ko pakadne aur system check karne ke liye logs padhe jate hain

**Yaad rakho:** Log = system ki apne aap banti diary. Cyber field mein logs padhna ek important skill hai.

---

## 5. File aur Folder Management Commands (poore naam ke saath)
```bash
pwd     # Print Working Directory - abhi kis folder mein ho
ls      # List - is folder ki files/folders dikhao
ls -R   # List Recursive - folder + andar ke sab folders bhi dikhao
cd      # Change Directory - folder badlo (andar/bahar jao)
mkdir   # Make Directory - naya folder banao
touch   # nayi khaali file banao
cat     # Concatenate - file ka text dikhao
cp      # Copy - file/folder ki copy banao
mv      # Move - file ko hilao (ya rename karo)
rm      # Remove - file delete karo
rm -r   # Remove Recursive - poora folder (sab andar sameत) delete
rmdir   # Remove Directory - khaali folder delete karo
```

**Har command ka poora naam yaad rakho:**
- `pwd` = **P**rint **W**orking **D**irectory
- `ls` = **L**i**s**t
- `cd` = **C**hange **D**irectory
- `mkdir` = **M**a**k**e **Dir**ectory
- `cp` = **C**o**p**y
- `mv` = **M**o**v**e
- `rm` = **R**e**m**ove
- `rmdir` = **R**e**m**ove **Dir**ectory
  
### Most Important Point:
**Farak samajh lo (log confuse hote hain):**
- `rm`    = **file** delete
- `rm -r` = **poora folder** (jisme files hon) delete
- `rmdir` = sirf **khaali folder** delete (agar folder mein kuch ho to ye kaam nahi karega)

---

## Quick Revision:
| Topic | Ek line yaad |
|-------|--------------|
| User level | limited power, apna kaam (hotel guest) |
| Root level | poori power, sab kuch (hotel manager) |
| sudo       | user thodी der ke liye root ki power udhaar le |
| whoami / sudo -i / exit | main kaun / poora root bano / wapas user |
| Logs | system ki apne aap banti diary (CCTV jaisi) |
| cp / mv / rm | copy / move / delete |
| rm vs rm -r vs rmdir | file / poora folder / khaali folder delete |
