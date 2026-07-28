# Class 02 — CPU, Memory, Buses & Boot

## 1. CPU, Memory, Buses (intro)
Computer ke 3 main kirdaar:
- **CPU** — dimaag, saara hisaab aur faisle karta hai
- **Memory** — data rakhne ki jagah (RAM + Storage)
- **Buses** — CPU aur memory ke beech data le jaane wali "sadkein"

## 2. Memory ke types + CPU ka basic kaam
**Memory 2 tarah ki:**
- **RAM** — abhi ka kaam yahan chalta hai (temporary, fast).
- **Storage (SSD/HDD)** — sab kuch permanent yahan rehta hai
**CPU ka basic kaam:** RAM se instruction leta hai → samajhta hai → kaam karta hai. Yeh baar               baar (billions/second) hota hai.

## 3. Volatile vs Non-volatile Memory
**RAM (Volatile):**
- Temporary memory — abhi ka kaam yahan chalta hai
- Bahut fast
- Light gayi to saara data **gayab** ho jata hai.
  
**SSD / HDD (Non-volatile):**
- Permanent storage — sab kuch yahan save rehta hai
- RAM ke muqable slow
- Light gayi tab bhi data **safe** rehta hai
**Yaad rakho:** RAM = mez (bijli gayi to saaf). SSD = almari (bijli gayi tab bhi safe).
  
## 4. CPU, RAM, SSD ka aapas mein relation
**Golden rule:** CPU **kabhi bhi** directly SSD/HDD se data nahi parhta. Pehle data SSD se **RAM** mein aata hai, phir CPU RAM se leta hai.

**Office wala example:** Store Room = SSD/HDD, Desk = RAM, Worker = CPU. File almari se nikaal kar mez par rakhte ho, phir kaam karte ho. Har baar almari nahi bhaagte.
**Data-flow:** `SSD → RAM → CPU`

## 5. Buses — 3 "highways" (System Bus)
CPU aur RAM ke beech 3 lines (buses) hoti hain, har ek ka apna kaam:
- **Address Bus** — CPU batata hai RAM ke **kis jagah (address)** se data lena hai. *One-way.*
- **Data Bus** — asli **data** yahan aata-jaata hai. *Two-way* (read + write).
- **Control Bus** — **READ ya WRITE** ka command le jaata hai.

**Ek line yaad rakho:** Address bus = "kahan", Control bus = "kya karna", Data bus = "asli maal".

## 6. CPU ke andar ka kaam (Internal working)
CPU har instruction ko 3 steps mein karta hai:
1. **Fetch** — RAM se agla instruction laao
2. **Decode** — samjho kya karna hai (Control Unit)
3. **Execute** — kaam kar do (ALU calculation karti hai)
**Parts:** Control Unit (samajhta), ALU (hisaab karti), Program Counter (agle instruction ka address rakhta).

## 7. Registers — CPU ki apni fast memory
CPU ke andar bohat chhoti aur **sabse tez** memory hoti hai jise **Register** kehte hain. Jis cheez pe CPU abhi kaam kar raha ho, woh yahan rehti hai.
**Speed order:** `Register (sabse fast) > RAM > SSD > HDD (slow)`

## 8. Data RAM se CPU tak kaise aata hai
1. CPU **Address Bus** se batata hai: "is address ka data chahiye"
2. **Control Bus** se command: "READ karo"
3. RAM woh data **Data Bus** par bhej deti hai → CPU ke **Register** mein aa jaata hai

## 9. Example — calculation aur result kaise store hota hai
Maan lo `20 + 30` karna hai:
1. CPU dono number RAM se leta hai → **Registers** mein rakhta hai
2. **ALU** jod deta hai → result **50**
3. Result pehle **Register** mein aata hai → phir **RAM** mein
4. RAM se SSD par **sirf tab** jaata hai jab tum **Save** karo

## 10. Example — Ctrl+S se file kaise save hoti hai
Tum Word mein likhti ho → woh sab abhi **RAM** mein hai (temporary).
Jab **Ctrl + S** dabati ho:
1. RAM ka data uthaya jaata hai
2. **SSD/HDD par permanently** likha jaata hai (ek `.docx` file ban jaati hai)

**Isi liye:** bina save kiye light chali jaye to kaam **kho jaata hai** — kyunki woh sirf RAM (volatile) mein tha, SSD par nahi pohancha.

## 11. ROM aur BIOS

**ROM kya hai?**
- **ROM** (Read Only Memory) ek memory hai jispe data pehle se likha hota hai
- Non-volatile — bijli jaye tab bhi data mit-ta nahi
- Motherboard par lagi ek chip (kabhi ise EEPROM/Flash bhi kehte hain)

**BIOS kya hai?**
- **BIOS** (Basic Input Output System) ek chota program/firmware hai jo **ROM ke andar** store hota hai
- Computer OFF ho to RAM khaali hoti hai — CPU ko pata hi nahi Windows kahan hai
- Isi liye power dabate hi **sabse pehle BIOS chalta hai**

**BIOS ka kaam (steps):**
1. **POST (Power-On Self Test)** — check karta hai ke computer ke saare parts (RAM, keyboard, hard disk, graphics) sahi kaam kar rahe hain ya nahi
2. Agar sab theek ho to BIOS **operating system dhoondta hai** (jaise Windows) jo SSD/HDD mein hota hai
3. Phir OS ko **RAM mein load** karna shuru karta hai, taake computer boot ho sake

**Simple:** BIOS ek "sabse pehla worker" hai jo system ON hote hi jaag jaata hai, sab check karta hai, phir baaki system (OS) ko jagata hai — taake computer use karne ke liye ready ho jaye.

** Example:** Jaise ghar ka chowkidar subah sabse pehle uthta hai, ghar ke saare darwaze/lights check karta hai (**POST**), phir baaki ghar walon (**OS**) ko jaga kar kaam start karwata hai — bilkul waise hi BIOS computer ke saath karta hai.
