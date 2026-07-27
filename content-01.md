# Class 01 — Cybersecurity Basics
## 1. Cybersecurity kya hai?
Computer, network aur data ko bina ijazat access, chori ya nuksan se bachana.
**Example:** Digital duniya ka taala + CCTV + chowkidar.
**CIA Triad (3 asool):**
- **Confidentiality** — data sirf haqdar dekhe (raazdaari)
- **Integrity** — data beech mein koi badle na (sahih rahe)
- **Availability** — jab chahiye, tab mile (mojood rahe)
 
## 2. Communication ke types
Data kis taraf jata hai:
TYPE                        COMMUNICATION                     EXAMPLE
|   Simplex      | Sirf ek taraf  communication    | TV/Radio, keyboard → PC |
| Half-Duplex    |        Dono taraf , bari bari   | Walkie-talkie |
| Full-Duplex    | Dono taraf, ek saath            | Phone calls;google meet |
Connection: **Wired** (cable, fast) ya **Wireless** (WiFi, aasaan).
 
## 3. Computer ke Parts
Computer Ke parts samjho:
- **External Parts:** 
         INPUT DEVICES: Keyboard/Mouse/Mic     
       OUTPUT DEVICES: Monitor/Speaker/Printer
- **Internal Parts:**
  - **CPU** — dimaag, saara hisaab
  - **RAM** — kaam wali mez, tez lekin bijli gayi to saaf (temporary)
  - **Hard Disk/SSD** — almari, permanent storage
  - **Motherboard** — sab ko jodne wali nasein
  - **Power Supply** — bijli pump karta hai (dil)
 
**RAM vs Hard Disk:** RAM = chhoti tez mez (abhi ka kaam). Disk = badi almari (sab rakha rehta).
 
## 4. Operating System (OS)
                   Software jo user aur hardware ke beech manager/translator hai.
          e.g: (Windows, Linux, Android)
**EXAMPLE:** Hotel manager — tum farmaish karte ho, wo machine se kaam karwata hai.
**WORKING:** process, memory, file, device manage karna + security.
User OS se do raaston se baat karta hai → **GUI** ya **CLI**.
 
## 5. GUI vs CLI
- **GUI** (Graphical) — icons, buttons, mouse. Aasaan. (Windows desktop)
- **CLI** (Command Line) — text commands. Tez, powerful. **Cyber field mein CLI zyada use hoti hai.** (CMD, PowerShell
**Example:** GUI = tasveer wala menu (point karo). CLI = chef ko seedhi recipe bolo (tez, par alfaaz aane chahiyen).
  
## 6. Hum computer se kaise baat karte hain?
Computer sirf **0 aur 1** (Binary) samajhta hai. 1 = light ON, 0 = OFF.
**PROCESS:** Input → CPU process (Fetch → Decode → Execute) → Output
**EXAMPLE:** 'A' dabaya → binary `01000001` bana → CPU ne process kiya → screen pe 'A'. Sab milliseconds mein.
Beech mein **OS translator** ka kaam karta hai — hamari baat ko machine ki zubaan (0/1) mein badalta hai.

## 7. DNS (Domain name System):
Domain name system jo domain names ko ip addresses ma change karta ha.
*Kyun?* Insaan *naam* yaad rakhta hai, computer *number (IP)* samajhta hai. DNS beech mein translator ka kam karta hai.
### Client kya hai?
Tumhara apna computer/browser jo poochta hai: "google.com ka IP kya hai?"
Yaani jo *maangta* hai = client.
### Cache kya hai?
Pehle se *yaad kiya hua jawab*, taake baar na poochna pare → speed barhti hai.
*Misaal:* Ek number mila to phone mein save kar liya — agli baar phonebook nahi kholni parti.
Cache kai jagah: browser → OS → resolver (ISP).
### DNS kaam kaise karta hai? (Steps)
1. google.com type kiya
2. Computer apni *cache* dekhta hai — pata hai? Haan → khatam
3. Nahi → *Recursive Resolver* (ISP, jaise PTCL/Jazz) se poochta hai
4. Resolver *Root server* se → Root kehta hai ".com wale TLD se poocho"
5. *TLD (.com) server* → authoritative server ka pata deta hai
6. *Authoritative server* → asli IP deta hai
7. Resolver IP wapas deta hai + *cache mein save* karta hai → website khul jati ha.
