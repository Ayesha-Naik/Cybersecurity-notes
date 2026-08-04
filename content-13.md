# Class 13 — Package Management (apt, dpkg, repository)

## 1. Package kya hota hai?
**Package** = ek software/app ka **poora dabba** jisme wo app aur uski sab zaroori cheezein (files) ek saath band hoti hain. Yani jab tum koi app install karti ho, wo ek "package" ki shakl mein aati hai.

**Sabse aasaan example — Play Store:**
Socho Kali mein bhi ek **Play Store** jaisा cheez hai. Waha lakhon apps (packages) padi hoti hain. Tum ek command likhti ho, wo waha se app dhoondh kar, download kar ke, install kar deta hai — bilkul Play Store jaisा, bas mobile ke bajaye terminal se.

---

## 2. Package Management kya hai?
**Package Management** = apps ko **install, update, aur remove** karne ka poora system. Iska kaam:
- App dhoondhna
- Install karna
- Update/upgrade karna
- Uninstall (hatana)

Linux mein ye sab ek tool se hota hai — Kali/Ubuntu mein us tool ka naam **apt** hai.

---

## 3. Repository kya hoti hai?
**Repository (repo)** = ek **online server (store)** jaha hazaron apps/packages rakhe hote hain. Jab tum koi app install karti ho, wo isi repository se aati hai.

**Example:** Repository = Play Store ka **godown (warehouse)** jaha sari apps rakhi hoti hain. Tumhara Kali us godown se cheez utha kar laata hai.

**Repository ki list kahan hoti hai?**
Kali mein repositories ka pata is file mein hota hai:
```
/etc/apt/sources.list
```
Ye file batati hai ke apt ko apps **kahan se** laani hain. Isme un servers ke address hote hain jaha se packages aati hain.

```bash
cat /etc/apt/sources.list    # dekho konsi repositories set hain
```
### /etc/apt/sources.list kya hai?
Ye koi command nahi — ek **file ka path** hai. Is file mein un online servers (repositories) ke **pate** hote hain jahan se apt apps laata hai. Yani ye file apt ko batati hai ke apps **kahan se** laani hain.

**Example:** Ek list jisme kuch restaurants ke pate hain — tum sirf unhi se order kar sakti ho. Kali bhi sirf un servers se apps laata hai jinke pate is file mein hain.

**Dekhne aur edit karne ke liye:**
```bash
cat /etc/apt/sources.list          # kaunsi repositories set hain, dekho
sudo nano /etc/apt/sources.list    # nayi repository add/remove karne ke liye edit
```

- `cat` = sirf dekho (kaunse server set hain)
- `nano` = edit karo (nayi repository add ya purani hatane ke liye) — `sudo` lagta hai kyunki ye system file hai

**Kab use hoti hai:** jab tum `apt update` ya `apt install` chalati ho, apt ye file padh kar decide karta hai apps kahan se laani hain. Kabhi koi app default mein na mile to uski repository yahan add karni parti hai.

---

## 4. App install karne ki commands (apt)
```bash
sudo apt update              # pehle ye - repository ki nayi list laao
sudo apt install nmap        # "nmap" naam ka app install karo
sudo apt remove nmap         # app hatao (uninstall)
```

**Sabse zaroori:** install karne se **pehle hamesha `sudo apt update`** chalao — ye repository se nayi list laata hai (taake latest app mile).

**Install ke andar kya hota hai (steps):** Jab tum `sudo apt install nmap` chalati ho:
1. apt repository (server) se nmap dhoondhta hai
2. Uski aur zaroori files (dependencies) bhi laata hai
3. Sab download karta hai
4. Install kar deta hai
5. App chalne ke liye tayyar

---

## 5. Update aur Upgrade
```bash
sudo apt update      # apps ki nayi list laao (kaunsi update available hai)
sudo apt upgrade     # sari apps ko nayi version pe upgrade karo
```

**Farak (log confuse hote hain):**
- **`update`** = sirf **list** laata hai — batata hai kaunsi apps ki nayi version aayi hai (abhi kuch install nahi hota)
- **`upgrade`** = asal mein apps ko **nayi version** pe le jata hai (asli update yahan hota hai)

**Meri example (mobile se):**
Socho tumhare phone mein WhatsApp hai. Play Store kholti ho:
- Play Store dekhta hai "WhatsApp ki nayi version aa gayi hai" — ye **`update`** hai (bas pata chala)
- Tum "Update" button dabati ho, WhatsApp naya ho jata hai — ye **`upgrade`** hai (asli kaam)

Yani `update` = "kya naya aaya hai check karo", `upgrade` = "ab naya install karo".

---

## 6. Dependency kya hoti hai?
**Dependency** = ek app ko chalne ke liye jo **doosri chhoti cheezein/files** chahiye hoti hain, unhe dependency kehte hain. App akela nahi chalta, kuch aur cheezein bhi saath chahiye.

**Example:** Socho tum cake banati ho (app). Cake ke liye anda, aata, cheeni (dependencies) chahiye — bina inke cake nahi banega. Waise hi app ke liye kuch files chahiye. **Achhi baat:** `apt` ye dependencies **apne aap** laa kar install kar deta hai — tumhe alag se laani nahi parti.

---

## 7. dpkg method (doosra tareeqa)
Kabhi app internet se nahi, ek `.deb` file (ready package) ke roop mein milti hai. Use install karne ke liye **dpkg** use hota hai.

```bash
sudo dpkg -i app.deb     # .deb file se app install karo
sudo dpkg -r app         # app hatao
dpkg -l                  # sari installed apps ki list dekho
```

**Steps (dpkg se install):**
1. Kahin se `.deb` file download karo
2. `sudo dpkg -i filename.deb` chalao
3. Agar dependency ki kami ho to `sudo apt install -f` chala do (kami poori kar deta hai)

**apt vs dpkg (farak):**
- **apt** = internet (repository) se aap laata + dependency khud sambhal leta (aasaan)
- **dpkg** = ready `.deb` file se install (dependency khud nahi laata)

---

## 8. App dhoondhne aur detail dekhne ki commands
```bash
apt search nmap    # "nmap" naam se milte-julte apps dhoondo (kaun-kaun available)
apt show nmap      # nmap app ki poori detail dekho (kya hai, version, size)
```

**Kaam:**
- `apt search` = koi app **dhoondo** (install se pehle — dekho available hai ya nahi)
- `apt show` = kisi app ki **detail** dekho (version, size, wo karta kya hai)

**Example:** Koi tool chahiye par naam yaad nahi — `apt search scanner` chalao, sab scanner tools dikh jayenge. Phir `apt show [naam]` se uski detail dekho.

---

## 9. App/file ki location dhoondhna
Kisi installed app ya file kahan padi hai, ye dhoondne ke liye:
```bash
which nmap       # nmap command kahan install hai, uska raasta dikhao
whereis nmap     # nmap se judi sab jagah (program, help files) dikhao
locate file.txt  # poore system mein file.txt dhoondo (tez)
```

**Kaam:**
- `which` = command ka raasta (kahan hai)
- `whereis` = command + uski help/config files kahan hain
- `locate` = poore system mein koi bhi file jaldi dhoondo

---

## 10. Package original hai ya nahi — kaise pata chale?
Tumne poocha tha: jo package install karte hain, wo **asli (original)** hai ya **naqli (fake/khatarnak)** — kaise pata chale?

**Jawab:** Linux khud check karta hai! Har repository ke paas ek **digital signature (key)** hoti hai — jaise asli note pe security mark hota hai. Jab tum `apt install` karti ho:
- apt package ki **signature check** karta hai
- Agar signature sahi (repository asli) → install ho jata hai
- Agar signature galat ya missing → apt **warning** deta hai ("this package is not verified") — matlab package pe bharosa mat karo

**Isliye:** hamesha **official repository** (jo `/etc/apt/sources.list` mein hoti hai) se hi install karo. Kisi random website ki `.deb` file se bacho — wo naqli/khatarnak ho sakti hai.

**Example:** Jaise asli medicine sirf licensed pharmacy se leti ho (bharosemand), waise apps sirf official repository se lo. Random jagah se li app mein virus ho sakta hai.

---

## Quick Revision:
| Cheez | Matlab |
|-------|--------|
| Package | app ka poora dabba (files ke saath) |
| Repository | online store/godown jaha apps hoti hain |
| apt update / upgrade | list laao / apps naye karo |
| apt install / remove | app install / hatao |
| apt search / show | dhoondo / detail dekho |
| dpkg -i | .deb file se install |
| dependency | app ko chalne ke liye zaroori extra files |
| which / whereis / locate | app/file kahan hai |
| /etc/apt/sources.list | repositories ki list |
| signature | asli/naqli package check karta hai |
