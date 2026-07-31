# Class 04 — Kernel, Process, Thread aur CLI Commands

## 1. Kernel kya hai?
**Kernel** OS ka **sabse andar wala hissa (dil)** hai jo seedha hardware (CPU, RAM, disk) se baat karta hai. Programs aur hardware ke beech pul (bridge) ka kaam karta hai.

**Kernel ka process (kaam):**
- Programs ki farmaish leta hai (jaise "file kholni hai")
- Hardware ko hukum deta hai (CPU, RAM, disk se kaam karwata)
- Memory aur processes sambhalta hai
- Sab kuch sahi chalta rahe, iska dhyan rakhta hai

**Example:** OS ek **gaadi** hai, kernel us gaadi ka **engine.** Baaki OS (screen, icons) tum dekhti ho, par asli kaam engine (kernel) chupa hua karta hai.

### Simple Kernel vs Linux Kernel — farak
- **Simple kernel** ek aam lafz hai — kisi bhi OS ke core ko kernel kehte hain (Windows ka bhi kernel hota hai, macOS ka bhi).
- **Linux Kernel** ek **khaas kernel** ka naam hai — jo Linus Torvalds ne banaya, free aur open-source hai. Kali, Ubuntu, Android — sab isi Linux kernel pe bane hain.

Yani "kernel" = general cheez (har OS mein hoti hai). "Linux kernel" = ek particular, mashhoor, free kernel.

---

## 2. Process kya hai?
**Process** = koi bhi program jo **abhi chal raha** ho. Jab tum koi app kholti ho, wo ek process ban jata hai.

**Example:** Chrome kholi → ek process. WhatsApp kholi → doosra process. Har chalta hua program ek process hai. OS in sab ko sambhalta hai (kis ko kitni CPU/RAM milegi).

---

## 3. Thread kya hai?
**Thread** = ek process ke **andar ka chhota kaam.** Ek process ke andar kai threads ho sakte hain jo ek saath chalte hain.

**Example:** Socho ek video kholi (process = video player). Uske andar:
- Ek thread video chala raha hai
- Ek thread awaaz (sound) chala raha hai
- Ek thread subtitle dikha raha hai

Ye teeno ek saath chal rahe — ye alag-alag **threads** hain, par sab ek hi process (video player) ke andar.

### Process vs Thread — farak
- **Process** = poora program (bada, apni alag memory)
- **Thread** = us process ke andar ka ek chhota kaam (chhota, memory share karta hai)

**Ek line:** Process = poora daftar (office). Thread = us office ke andar kaam karne wale log. Ek office (process) mein kai log (threads) alag-alag kaam ek saath karte hain.

---

## 4. CLI (Command Line Interface) kya hai?
**CLI** ek tareeqa hai computer se baat karne ka jahan tum **text commands likhti ho** (mouse-click nahi). Terminal/CMD isi ki misaal hai.

**Kaunse OS mein hota hai?** **Dono mein!**
- **Linux** → Terminal (bohat powerful, cyber ke liye zaroori)
- **Windows** → CMD aur PowerShell

Yani CLI Windows aur Linux **dono** mein hota hai. Bas commands thodी alag hoti hain. Linux ka CLI zyada powerful mana jata hai, isi liye hackers/cyber walon ki pasand hai.

**Example:** GUI (mouse) = restaurant ka menu, point karke order karo (aasaan). CLI = seedha chef ko recipe bolo (tez aur powerful, par alfaaz aane chahiyen).

---

## 5. Basic Commands
```bash
pwd            # Print Working Directory - abhi tum kis folder mein ho, wo dikhata hai
ls             # current directory ki files/folders list karta hai
clear          # terminal ki screen saaf karta hai (kaam delete nahi hota)
date           # abhi ka time aur date dikhata hai
```

### cd — Change Directory (folder badalna)
`cd` ke kai tareeqe (uses) hain:
```bash
cd folder_name        # us naam ke folder ke andar jao
cd Desktop/file_name  # Desktop ke andar us folder mein seedha jao
cd ..                 # ek folder peeche (bahar) aao
cd                     # seedha home folder pe wapas (akela cd)
cd /                   # bilkul root (sabse upar) pe jao
```

**Yaad rakho:**
- `cd folder` = andar jao
- `cd ..` = peeche/bahar aao
- `cd` (akela) = home
- `cd /` = root (sabse upar)

---

## 6. File Management Commands
```bash
touch file_name    # khaali nayi file banao
cat file_name      # file ka andar ka text dekho
rm file_name       # ek file delete karo
rm -r folder_name  # poora folder (uski sab files ke saath) delete karo
```

**Yaad rakho:**
- `touch` = nayi file banao
- `cat` = file ka text dekho
- `rm` = file delete
- `rm -r` = poora folder delete (`-r` = recursive, andar sab kuch)

**⚠️ Dhyan:** `rm` se cheez seedha delete hoti hai — Recycle Bin mein nahi jati, wapas nahi aati. Isliye soch-samajh kar use karo.

---

## Quick Revision:
| Topic | Ek line yaad |
|-------|--------------|
| Kernel       | OS ka engine — hardware se seedha baat |
| Linux Kernel | ek khaas free kernel (Kali, Android sab isi pe) |
| Process      | chalta hua program (jaise khuli Chrome) |
| Thread       | process ke andar ka chhota kaam (video+sound saath) |
| CLI | text commands se baat — Windows aur Linux dono mein |
| pwd/ls/cd | kahan ho / list / folder badlo |
| touch/cat/rm | file banao / dekho / delete |
