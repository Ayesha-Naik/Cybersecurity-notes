# Class 14 — Networking (Internet, IP, ping,ssh,TTL,telent,curl & wget,Request process)

## 1. Internet kya hai?
**Internet** = duniya bhar ke computers ka ek **bada jaal (network)** jo aapas mein jude hue hain aur data (message, photo, video) ek doosre ko bhejte hain.

**Example:** Internet ek **bohat badi sadkon ka jaal** hai jo poori duniya ke gharon (computers) ko jodta hai. Jaise sadkon pe gaadiyan chalti hain, waise internet pe data chalta hai — ek computer se doosre tak.

---

## 2. Network kya hota hai?
**Network** = do ya zyada computers jo aapas mein **jude** hon aur data share kar saken.

**Example:** Tumhare ghar mein WiFi hai — us se laptop, mobile, TV sab jude hain aur aapas mein baat kar sakte hain. Ye ek chhota **network** hai. Internet in sab chhote networks ka bada jaal hai.

---

## 3. IP Address kya hota hai?
**IP Address** = har computer/device ka apna **unique number (pata)** network mein. Jaise har ghar ka apna address hota hai, waise har device ka apna IP.

**Example:** IP address = tumhare **ghar ka pata.** Jab koi tumhe letter (data) bhejta hai, wo address se tum tak pohanchta hai. Waise data sahi computer tak IP se pohanchta hai.
Misaal: `192.168.1.5` ya `8.8.8.8`

---

## 4. MAC Address kya hota hai?
**MAC Address** = har device ke **network card** ka permanent number — jo factory mein hi fix ho jata hai, kabhi badalta nahi.

**Farak (IP vs MAC):**
- **IP address** badal sakta hai (jagah/network badle to badal jata)
- **MAC address** permanent hai (device ki hardware ID)

**Example:** MAC address = tumhara **CNIC/ID card number** (kabhi nahi badalta). IP address = tumhara **abhi ka pata** (jagah badle to badal jata).

---

## 5. NIC (Network Interface Card) kya hai?
**NIC** = wo **hardware card** jo tumhare computer ko network se jodta hai. Iske bina computer network se baat nahi kar sakta. (WiFi card ya LAN card — dono NIC hain.)

**Example:** NIC computer ka **kaan aur zubaan** hai — isi se computer network se sunta aur bolta hai. Bina NIC ke computer "gunga-behra" hai (network se baat hi nahi kar sakta).

**MAC aur IP ka role (connection mein):**
Jab tum kisi website se baat karti ho:
- **IP address** batata hai data **kahan** jaana hai (kaunse computer tak)
- **MAC address** batata hai local network mein **kaunse device** tak
- **NIC** actual mein data bhejta/leta hai

Yani teeno mil kar connection banate hain: NIC (hardware) data bhejta hai, IP raasta batata hai, MAC local device pehchanata hai.

---

## 6. Network ki Commands
```bash
ip a             # apne computer ka IP address dekho (ya: ifconfig)
ping 8.8.8.8     # check karo internet/kisi computer se connection hai ya nahi
hostname         # apne computer ka naam dekho
hostname -I      # apna IP dikhao (short)
netstat -tuln    # khule ports/connections dekho
```

---

## 7. ping aur traceroute (sabse important — aasaan tareeqe se)

### ping kya hai?
**ping** = check karta hai ke koi computer/website **zinda hai aur baat kar rahi hai ya nahi.** Ek chhota message bhejta hai aur dekhta hai jawab aata hai ya nahi.

**Example:** Jaise tum kisi ko phone kar ke poocho "sun rahe ho?" aur wo kahe "haan" — matlab connection theek hai. `ping` bhi yehi karta hai.

```bash
ping 8.8.8.8
```
**Output aisa aayegi:**
```
64 bytes from 8.8.8.8: time=20 ms
64 bytes from 8.8.8.8: time=18 ms
64 bytes from 8.8.8.8: time=21 ms
```
Iska matlab: 8.8.8.8 (Google ka server) zinda hai, jawab de raha hai, aur 20 ms (bohat kam time) mein. **Connection theek hai.** Agar "Request timed out" aaye to connection nahi hai.

### traceroute kya hai?
**traceroute** = batata hai ke tumhara data **kis-kis raaste (stops) se guzar kar** manzil tak pohancha. Har stop (router) dikhata hai.

**Example:** Jaise tum bus se safar karti ho — traceroute batata hai konse konse stops (adde) aaye raaste mein. `ping` sirf batata hai "pohancha ya nahi", `traceroute` batata hai "kaunse raaste se pohancha".

```bash
traceroute 8.8.8.8
```
**Output aisा:**
```
1  192.168.1.1   (tumhara router)      2 ms
2  10.0.0.1      (ISP ka server)       8 ms
3  72.14.x.x     (beech ka raasta)     15 ms
4  8.8.8.8       (Google - manzil)     20 ms
```
Iska matlab: data pehle tumhare router (stop 1), phir ISP (stop 2), phir beech ke raaste (stop 3), phir Google (stop 4) tak pohancha. **Har stop dikh raha hai.**

**Farak:** `ping` = "pohancha ya nahi + kitna time". `traceroute` = "kaunse-kaunse raaste se pohancha".

---

## 8. curl aur wget commands
Ye dono **internet se cheezein laane** ke liye hain.

### curl
```bash
curl google.com         # website ka content terminal pe dikhao
curl -O url/file.zip     # file download karo (usi naam se)
curl -I google.com       # sirf website ka header (info) dekho
```
**curl** = website se data laata hai aur terminal pe dikhata hai (ya file download).

### wget
```bash
wget url/file.zip        # file download karo
wget -c url/file.zip     # ruki hui download dobara shuru karo (continue)
```
**wget** = internet se **file download** karne ke liye (seedha save kar deta hai).

**Farak:** `curl` = data laa kar dikhata/bhejta (zyada options). `wget` = seedha file download (simple).
**Kaam:** dono se internet se files/pages laate hain — cyber mein tools ya files download karne ke liye.

---

## 9. Browser kya hota hai?
**Browser** = wo app jisse tum websites kholti ho (Chrome, Firefox, Edge). Ye tumhari request website tak le jata hai aur jawab (page) tumhe khoobsurat bana kar dikhata hai.

**Kaise kaam karta hai:** Tum address likhti ho (google.com) → browser DNS se uska IP nikaalta hai → us server se page maangta hai → page aa kar screen pe khoobsurat dikhta hai.

**Browser ki functionality (kaam):**
- Websites kholna (URL se)
- Tabs — ek saath kai pages
- Bookmarks — pasand ki site save
- History — kholi hui sites ka record
- Download — files download
- Search — Google se dhoondna
- Extensions — extra features add
- Incognito — bina history ke browse
- Cache/Cookies — site ka data yaad rakhna (speed ke liye)

---

## 10. SSH kya hai?
**SSH (Secure Shell)** = ek **secure (mehfooz) tareeqa** jisse tum door (remote) ke computer/server ko apne terminal se control kar sakti ho — jaise wo tumhare saamne ho.

**Example:** Socho ek server doosre sheher/mulk mein hai. Tum ghar baithe SSH se us server mein login kar ke usme commands chala sakti ho — bilkul jaise tumhare saamne ho. Aur ye connection **encrypted (mehfooz)** hota hai — koi beech mein padh nahi sakta.

```bash
ssh username@ip_address      # remote computer mein login karo
ssh ayesha@192.168.1.10      # ayesha naam se us IP wale computer mein login
```
**Cyber mein bohat use hota hai** — servers ko door se control karne ke liye.

---

## 11. Telnet kya hai?
**Telnet** = SSH jaisा hi — door ke computer se connect karne ke liye. **Par farak:** telnet **mehfooz nahi** (data khula jata hai, koi padh sakta hai). Isliye aaj kal telnet ki jagah **SSH** use hota hai (kyunki SSH secure hai).

```bash
telnet ip_address port    # kisi computer/port se connect karo
```
**Yaad rakho:** Telnet = purana, unsafe. SSH = naya, safe. (Telnet abhi bhi port check karne ke liye use hota hai.)

---

## 12. TTL kya hai?
**TTL (Time To Live)** = ek number jo batata hai data packet **kitne stops (routers) tak** ja sakta hai. Har stop pe ye number 1 kam hota hai. Jab 0 ho jaye, packet mar jata hai (aage nahi jata).

**Kyun?** Taake koi packet hamesha ke liye internet mein na ghoomta rahe — ek limit ho.

**Example:** TTL = ek bus ticket jisme likha "20 stops tak valid". Har stop pe 1 kam. 0 hone pe bus se utar do (packet khatam). Ping/traceroute ke output mein bhi TTL dikhta hai.

---

## 13. Request process: — Google kaise khulta hai? (sabse important)
Jab tum `google.com` likhti ho, data ka poora safar aise hota hai:

1. **Device (tum)** → tum browser mein `google.com` likhti ho
2. **Router** → tumhari request pehle ghar ke router pe jaati hai
3. **ISP** → router se request tumhare Internet company (ISP - jaise PTCL/Jazz) tak
4. **DNS resolve** → DNS `google.com` ka **IP address** nikaalta hai (naam → number)
5. **Internet ke raaste** → request us IP (Google server) tak kai stops se guzar kar jaati hai
6. **Google Server** → server tumhari request leta hai, page tayyar karta hai
7. **Wapas** → wahi page ulta safar kar ke (server → ISP → router → tumhara device) tumhare browser pe aa jata hai
8. **Screen** → page khoobsurat bana kar screen pe dikhta hai

**Ek line mein:** Device → Router → ISP → DNS (IP nikaala) → Google Server → aur wapas → tumhari screen. Ye sab **1-2 second** mein ho jata hai!

**Example:** Jaise tum khaana order karti ho — phone (device) se order, wo restaurant (server) tak jaata hai (router/ISP/raaste se), khaana banta hai, aur delivery (wapas) tumhare ghar aati hai. Website bhi bilkul aise hi "order aur delivery" hai — bas seconds mein.

---

## Quick Revision:
| Cheez | Matlab |
|-------|--------|
| Internet | duniya ke computers ka bada jaal |
| Network | jude hue computers (WiFi jaisा) |
| IP Address | device ka pata (badal sakta) |
| MAC Address | device ki permanent ID |
| NIC | network card (computer ka kaan-zubaan) |
| ping | connection zinda hai ya nahi |
| traceroute | data kis raaste se gaya |
| curl / wget | internet se data/file laana |
| Browser | websites kholne wala app |
| SSH | door ke computer ko secure control |
| Telnet | SSH jaisा par unsafe (purana) |
| TTL | packet kitne stops tak jaye |
| Request ka safar | Device→Router→ISP→DNS→Server→wapas |
