# Class 03 — CPU aur OS Basics & Memory Management,Linux, Windows

## 1. CPU kya hai?
**CPU (Central Processing Unit)** computer ka **dimaag** hai. Jo bhi kaam computer karta hai — hisaab, faisle, apps chalana — sab CPU karta hai.

**Kaise kaam karta hai?** CPU har chhote kaam ko 3 steps mein karta hai:
1. **Fetch** — kaam uthao
2. **Decode** — samjho kya karna hai
3. **Execute** — kaam kar do

Aur ye cycle **ek second mein arbon (billions) baar** chalti hai — itni tez ke soch bhi nahi sakte.

**Example:** CPU ek **bawarchi (cook)** jaisa hai. Recipe parhta hai → samajhta hai → khana banata hai. Jitna tez bawarchi, utna jaldi khana. Waise hi jitna tez CPU, utna tez computer.

**CPU aur OS kahan hote hain?**
- **CPU** ek **chip** hai — motherboard pe lagi hoti hai, haath se chhoo sakti ho (hardware).
- **OS** (Windows/Linux) ek **software** hai — Hard Disk/SSD mein rehta hai, computer on hote hi RAM mein aa jata hai.

**Poora process:** Tum koi app kholti ho → OS us kaam ko CPU ki zabaan mein badalta hai → CPU kaam karta hai → result screen pe aata hai.
Yani **OS = translator (beech wala), CPU = asli kaam karne wala.**

---

## 2. Memory Management kya hai?
Computer mein **RAM** hoti hai — wo jagah jahan chalte hue apps rehte hain. Par RAM **limited** hoti hai. To OS ka ek kaam hai **Memory Management** — yani RAM ko samajhdari se baant-na: kis app ko kitni RAM do, kab do, aur kab wapas lo.

**Kaise?**
- App chal raha hai → usse RAM do
- App band ho gaya → us RAM ko khaali karke doosre ko do
- RAM full ho jaye → thodा kaam Hard Disk pe daal do (ise **virtual memory** kehte hain)

**Example — mez:** Socho tumhari padhne ki mez (RAM) chhoti hai. Kaam wali kitaab mez pe rakhti ho, kaam khatam hote hi almari mein wapas, phir agli kitaab laati ho. **OS bhi bilkul yehi karta hai** — isi liye mez kabhi full nahi hoti.

**Faida:** Isi wajah se tum ek saath Chrome, WhatsApp aur gaana chala sakti ho — OS sab ko sahi RAM de kar sambhal leta hai.

---

## 3. Operating System (OS) kya hai?
**OS** wo software hai jo tumhare (user) aur computer ke hardware ke beech **manager** ka kaam karta hai. Iske bina computer sirf ek khaali dabba hai.

**Example:** OS **hotel ka manager** hai. Tum farmaish karti ho, wo kitchen aur staff (hardware) se kaam karwa deta hai — tumhe machine ki zabaan seekhne ki zaroorat nahi.

### OS files aur folders kaise sambhalta hai? (File System)
OS data ko ek tarteeb se rakhta hai jise **File System** kehte hain:
- **File** = ek cheez (photo, gaana, document)
- **Folder** = ek dabba jisme kai files hon
- **File System** = poora tareeqa jisse OS files/folders rakhta, dhoondta aur khol-ta hai

**Example:** Almari (drive) → uske andar dabbe (folders) → dabbon mein kaghaz (files). File system woh tarteeb hai jisse har cheez apni jagah mile aur foran mil jaye.

**Alag OS, alag file system:**
- **Windows** → NTFS (drives C:, D: dikhte hain)
- **Linux** → ext4 (sab kuch ek `/` se shuru, koi drive letter nahi)
- **macOS** → APFS

---

## 4. (OS) Operating System ke Types
Har OS ka apna maqsad aur khaasiyat hai:

**Windows (Microsoft):**
- Sabse aam — ghar aur office mein
- Aasaan, har software/game chalta hai
- Paid hota hai (license lagta hai)

**Linux (Kali, Ubuntu waghera):**
- Free aur open-source (koi paisa nahi)
- Bohat secure aur tez
- Hackers, developers aur cyber security walon ki pasand
- Thodа seekhna parta hai (terminal se kaam)

**macOS (Apple):**
- Sirf Apple ke computers (MacBook) pe
- Bohat smooth, design/editing walon ki pasand
- Mehnga

**Android / iOS:**
- Mobile phones ke OS (Android to Linux hi pe bana hai)

---

## 5. Linux Kernel kya hai?
**Kernel** kisi bhi OS ka **dil (core)** hota hai — sabse andar wala hissa jo seedha hardware se baat karta hai.

**Linux Kernel** wo asli hissa hai jo:
- CPU, RAM aur baaki hardware ko control karta hai
- Programs aur hardware ke beech pul (bridge) banta hai
- Memory aur process — sab sambhalta hai

**Example:** OS ek **gaadi** hai, kernel us gaadi ka **engine.** Tum steering, seat, screen (baaki OS) use karti ho, par asli kaam engine (kernel) karta hai — chupa hua, par sab kuch usi pe chalta hai.

**Yaad rakho:** "Linux" asal mein **kernel ka naam** hai. Ubuntu, Kali waghera us kernel ke upar bane poore OS hain.

---

## 6. Windows vs Linux — poora farak
Sabse zaroori sawaal: jab Windows hai to Linux kyun? Pehle dono ko alag-alag samjho.

### Windows kya hai?
Microsoft ka banaya OS — duniya mein sabse zyada use hone wala. Ghar aur office ke computers mein aksar yehi hota hai.
- **Free nahi** — license kharidna parta hai
- Iska code **band (secret)** hai — koi dekh/badal nahi sakta
- **Aasaan** — mouse se click karke sab ho jata hai
- Har software aur game chalta hai
- **Kami:** virus zyada ate hain, aur kabhi dheema ho jata hai

**Kiske liye:** aam log, students, office, gaming.

### Linux kya hai?
Free aur open-source OS. Kali, Ubuntu waghera sab Linux hi hain.
- **Bilkul free** — koi paisa nahi
- Code **khula (open)** hai — koi bhi dekh aur samajh sakta hai
- Bohat **secure** — virus bohat kam
- **Halka aur tez** — purane computer pe bhi chalta hai
- **Terminal** bohat powerful hai
- **Kami:** shuru mein seekhna parta hai

**Kiske liye:** hackers, developers, servers, cyber security walon ke liye.

### Dono ka role kya hai? (aur Linux kyun?)
Dono **OS hi hain** — dono ka basic kaam ek hi hai: user aur hardware ke beech manager banna, files sambhalna, apps chalana. Farak sirf **maqsad** ka hai:
- **Windows ka role:** roz ke aam kaam — padhai, office, internet, gaming. Aaram-deh aur aasaan.
- **Linux ka role:** technical/professional kaam — hacking, cyber security, servers, coding. Powerful aur khula.

**Toh Windows hote hue Linux kyun install karte hain?**
Kyunki **cyber security ka saara kaam Linux pe hota hai:**
1. Security tools (Nmap, Metasploit waghera) Linux ke liye bane hain
2. Terminal se powerful kaam hota hai
3. Free aur khula — andar tak sab seekh sakti ho
4. Duniya ke zyada tar servers Linux pe chalte hain — isliye cyber field mein Linux zaroori

**Example:** Windows ek **aam gaadi** hai — roz ghar/office jaane ke liye, aaram-deh, bina kuch jaane chala lo. Linux ek **mechanic/racing gaadi** hai — bonnet khol kar engine dekh sakti ho, tez, aur professional kaam ke liye. Tum cyber field mein ho, isliye tumhe wo "khuli gaadi" chahiye jahan sab seekh sako.

**Isi liye** laptop mein Windows ke saath Linux (Kali) chalate hain — **Windows roz ke kaam ke liye, Linux cyber security seekhne aur karne ke liye.**

---

## QUICK REVISION:
| Topic | Ek line yaad |
|-------     |--------------|
| CPU        | Dimaag — Fetch, Decode, Execute (bawarchi jaisa) |
| OS         |  Manager — user aur hardware ke beech |
| Memory Management | OS RAM ko samajhdari se baant-ta hai (mez wali example) |
| File System       | Files/folders ki tarteeb (almari-dabbe-kaghaz) |
| OS Types | Windows (aam), Linux (cyber/free), macOS (Apple) |
| Linux Kernel | OS ka engine — hardware se seedha baat |
| Windows vs Linux | Linux: free, secure, tez — cyber ke liye best |
