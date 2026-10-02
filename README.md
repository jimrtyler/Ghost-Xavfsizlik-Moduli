# 👻 Ghost Xavfsizlik Moduli
**PowerShell asosida Windows va Azure xavfsizlikni mustahkamlash vositasi**

> **Windows so'nggi nuqtalari va Azure muhitlari uchun faol xavfsizlikni mustahkamlash.** Ghost keraksiz xizmatlar va protokollarni o'chirib qo'yish orqali umumiy hujum vektorlarini kamaytirishga yordam beradigan PowerShell asosidagi mustahkamlash funksiyalarini taqdim etadi.

## ⚠️ Muhim javobgarlik rad etish bayonotlari

**SINOVDAN O'TKAZISH ZARUR**: Ghost-ni har doim avval ishlab chiqarish bo'lmagan muhitlarda sinab ko'ring. Xizmatlarni o'chirib qo'yish qonuniy biznes funksiyalariga ta'sir qilishi mumkin.

**KAFOLATLAR YO'Q**: Ghost umumiy hujum vektorlarini nishonga olgan bo'lsa ham, hech qanday xavfsizlik vositasi barcha hujumlarni oldini ola olmaydi. Bu keng qamrovli xavfsizlik strategiyasining bir komponentidir.

**OPERATSION TA'SIR**: Ba'zi funksiyalar tizim funksionalligiga ta'sir qilishi mumkin. Joylashtirshdan oldin har bir sozlamani diqqat bilan ko'rib chiqing.

**PROFESSIONAL BAHOLASH**: Ishlab chiqarish muhitlari uchun sozlamalar tashkilotingiz ehtiyojlariga mos kelishini ta'minlash uchun xavfsizlik mutaxassislari bilan maslahatlashing.

## 📊 Xavfsizlik manzarasi

Ransomware zararlari **2025 yilda 57 milliard dollarga** yetdi, tadqiqotlar ko'plab muvaffaqiyatli hujumlar asosiy Windows xizmatlari va noto'g'ri konfiguratsiyalardan foydalanishini ko'rsatmoqda. Umumiy hujum vektorlari quyidagilarni o'z ichiga oladi:

- **Ransomware voqealarining 90%i** RDP ekspluatatsiyasini o'z ichiga oladi
- **SMBv1 zaifliklar** WannaCry va NotPetya kabi hujumlarga imkon berdi
- **Hujjat makroslari** asosiy zararli dastur yetkazib berish usuli bo'lib qolmoqda
- **USB asosidagi hujumlar** havo bo'shliqlari tarmoqlarini nishonlashda davom etmoqda
- **PowerShell suistemolli** so'nggi yillarda sezilarli darajada oshdi

## 🛡️ Ghost xavfsizlik funksiyalari

Ghost **16 ta Windows mustahkamlash funksiyalari** va **Azure xavfsizlik integratsiyasini** taqdim etadi:

### Windows yakuniy nuqta mustahkamlash

| Funksiya | Maqsad | Mulohazalar |
|----------|---------|----------------|
| `Set-RDP` | Masofaviy ish stoli kirishini boshqaradi | Masofaviy boshqaruvga ta'sir qilishi mumkin |
| `Set-SMBv1` | Eski SMB protokolini nazorat qiladi | Juda eski tizimlar uchun kerak |
| `Set-AutoRun` | AutoPlay/AutoRun-ni nazorat qiladi | Foydalanuvchi qulayligiga ta'sir qilishi mumkin |
| `Set-USBStorage` | USB saqlash qurilmalarini cheklaydi | Qonuniy USB foydalanishiga ta'sir qilishi mumkin |
| `Set-Macros` | Office makros ijrosini nazorat qiladi | Makros yoqilgan hujjatlarga ta'sir qilishi mumkin |
| `Set-PSRemoting` | PowerShell masofaviy kirishni boshqaradi | Masofaviy boshqaruvga ta'sir qilishi mumkin |
| `Set-WinRM` | Windows Remote Management nazorat qiladi | Masofaviy boshqaruvga ta'sir qilishi mumkin |
| `Set-LLMNR` | Nom hal qilish protokolini boshqaradi | Odatda o'chirib qo'yish xavfsiz |
| `Set-NetBIOS` | TCP/IP ustida NetBIOS-ni nazorat qiladi | Eski ilovalar ta'sir qilishi mumkin |
| `Set-AdminShares` | Ma'muriy ulashlarni boshqaradi | Masofaviy fayl kirishiga ta'sir qilishi mumkin |
| `Set-Telemetry` | Ma'lumot to'plashni nazorat qiladi | Diagnostika imkoniyatlariga ta'sir qilishi mumkin |
| `Set-GuestAccount` | Mehmon hisobini boshqaradi | Odatda o'chirib qo'yish xavfsiz |
| `Set-ICMP` | Ping javoblarini nazorat qiladi | Tarmoq diagnostikasiga ta'sir qilishi mumkin |
| `Set-RemoteAssistance` | Masofaviy yordamni boshqaradi | Yordam xizmati operatsiyalariga ta'sir qilishi mumkin |
| `Set-NetworkDiscovery` | Tarmoq kashfiyotini nazorat qiladi | Tarmoq ko'rishga ta'sir qilishi mumkin |
| `Set-Firewall` | Windows Firewall-ni boshqaradi | Tarmoq xavfsizligi uchun muhim |

### Azure bulut xavfsizligi

| Funksiya | Maqsad | Talablar |
|----------|---------|--------------|
| `Set-AzureSecurityDefaults` | Asosiy Azure AD xavfsizligini yoqadi | Microsoft Graph ruxsatlari |
| `Set-AzureConditionalAccess` | Kirish siyosatlarini sozlaydi | Azure AD P1/P2 litsenziyalash |
| `Set-AzurePrivilegedUsers` | Imtiyozli hisoblarni audit qiladi | Global Admin ruxsatlari |

### Korxona joylashtirish variantlari

| Usul | Foydalanish holati | Talablar |
|--------|----------|--------------|
| **To'g'ridan-to'g'ri bajarish** | Sinov, kichik muhitlar | Mahalliy admin huquqlari |
| **Group Policy** | Domen muhitlari | Domen admin, GP boshqaruvi |
| **Microsoft Intune** | Bulut boshqariladigan qurilmalar | Intune litsenziyalash, Graph API |

## 🚀 Tezkor boshlash

### Xavfsizlik baholash
```powershell
# Ghost modulini yuklash
Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1' -OutFile .\Ghost.ps1
Get-Content .\Ghost.ps1
. .\Ghost.ps1

# Joriy xavfsizlik holatini tekshirish
Get-Ghost
```

### Asosiy mustahkamlash (avval sinab ko'ring)
```powershell
# Muhim mustahkamlash - avval laboratoriya muhitida sinab ko'ring
Set-Ghost -SMBv1 -AutoRun -Macros

# O'zgarishlarni ko'rib chiqish
Get-Ghost
```

### Korxona joylashtirish
```powershell
# Group Policy joylashtirish (domen muhitlari)
Set-Ghost -SMBv1 -AutoRun -GroupPolicy

# Intune joylashtirish (bulut boshqariladigan qurilmalar)
Set-Ghost -SMBv1 -RDP -USBStorage -Intune
```

## 📋 O'rnatish usullari

### Variant 1: To'g'ridan-to'g'ri yuklab olish (sinov)
```powershell
Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1' -OutFile .\Ghost.ps1
Get-Content .\Ghost.ps1
. .\Ghost.ps1
```

### Variant 2: Modul o'rnatish
```powershell
# PowerShell Gallery-dan o'rnatish (mavjud bo'lganda)
Install-Module Ghost -Scope CurrentUser
Import-Module Ghost
```

### Variant 3: Korxona joylashtirish
```powershell
# Group Policy joylashtirish uchun tarmoq joyiga nusxalash
# Bulut joylashtirish uchun Intune PowerShell skriptlarini sozlash
```

## 💼 Foydalanish holati misollari

### Kichik biznes
```powershell
# Minimal ta'sir bilan asosiy himoya
Set-Ghost -SMBv1 -AutoRun -Macros -ICMP
```

### Sog'liqni saqlash muhiti
```powershell
# HIPAA-ga yo'naltirilgan mustahkamlash
Set-Ghost -SMBv1 -RDP -USBStorage -AdminShares -Telemetry
```

### Moliyaviy xizmatlar
```powershell
# Yuqori xavfsizlik konfiguratsiyasi
Set-Ghost -RDP -SMBv1 -AutoRun -USBStorage -Macros -PSRemoting -AdminShares
```

### Bulut-birinchi tashkilot
```powershell
# Intune boshqariladigan joylashtirish
Connect-IntuneGhost -Interactive
Set-Ghost -SMBv1 -RDP -AutoRun -Macros -Intune
```

## 🔍 Funksiya tafsilotlari

### Asosiy mustahkamlash funksiyalari

#### Tarmoq xizmatlari
- **RDP**: Masofaviy ish stoli kirishini bloklaydi yoki portni tasodifiylashtiradi
- **SMBv1**: Eski fayl ulashish protokolini o'chiradi
- **ICMP**: Razvedka uchun ping javoblarini oldini oladi
- **LLMNR/NetBIOS**: Eski nom hal qilish protokollarini bloklaydi

#### Ilova xavfsizligi
- **Makroslar**: Office ilovalarida makros ijrosini o'chiradi
- **AutoRun**: Olinadigan media-dan avtomatik ijroni oldini oladi

#### Masofaviy boshqaruv
- **PSRemoting**: PowerShell masofaviy seanslarini o'chiradi
- **WinRM**: Windows Remote Management-ni to'xtatadi
- **Remote Assistance**: Masofaviy yordam ulanishlarini bloklaydi

#### Kirish nazorati
- **Admin Shares**: C$, ADMIN$ ulashlarini o'chiradi
- **Guest Account**: Mehmon hisob kirishini o'chiradi
- **USB Storage**: USB qurilma foydalanishini cheklaydi

### Azure integratsiyasi
```powershell
# Azure ijarachiga ulanish
Connect-AzureGhost -Interactive

# Xavfsizlik sukut bo'yicha qiymatlarini yoqish
Set-AzureSecurityDefaults -Enable

# Shartli kirishni sozlash
Set-AzureConditionalAccess -BlockLegacyAuth -RequireMFA

# Imtiyozli foydalanuvchilarni audit qilish
Set-AzurePrivilegedUsers -AuditOnly
```

### Intune integratsiyasi (v2 da yangi)
```powershell
# Intune-ga ulanish
Connect-IntuneGhost -Interactive

# Intune siyosatlari orqali joylashtirish
Set-IntuneGhost -Settings @{
    RDP = $true
    SMBv1 = $true
    USBStorage = $true
    Macros = $true
}
```

## ⚠️ Muhim mulohazalar

### Sinov talablari
- **Laboratoriya muhiti**: Avval barcha sozlamalarni ajratilgan muhitda sinab ko'ring
- **Bosqichma-bosqich joylashtirish**: Muammolarni aniqlash uchun asta-sekin kengaytiring
- **Qaytarish rejasi**: Kerak bo'lganda o'zgarishlarni qaytara olishingizga ishonch hosil qiling
- **Hujjatlashtirish**: Muhitingiz uchun qaysi sozlamalar ishlashini yozing

### Potentsial ta'sir
- **Foydalanuvchi samaradorligi**: Ba'zi sozlamalar kundalik ish oqimlariga ta'sir qilishi mumkin
- **Eski ilovalar**: Eski tizimlar ma'lum protokollarni talab qilishi mumkin
- **Masofaviy kirish**: Qonuniy masofaviy boshqaruvga ta'sirini hisobga oling
- **Biznes jarayonlari**: Sozlamalar muhim funksiyalarni buzmasligini tekshiring

### Xavfsizlik cheklovlari
- **Chuqur mudofaa**: Ghost xavfsizlikning bir qatlami, to'liq yechim emas
- **Doimiy boshqaruv**: Xavfsizlik doimiy monitoring va yangilanishlarni talab qiladi
- **Foydalanuvchi ta'limi**: Texnik nazorat xavfsizlik xabardorligi bilan birlashtirilishi kerak
- **Tahdid evolyutsiyasi**: Yangi hujum usullari joriy himoyani chetlab o'tishi mumkin

## 🎯 Hujum stsenariylari misollari

Ghost umumiy hujum vektorlarini nishonga olgan bo'lsa-da, aniq oldini olish to'g'ri amalga oshirish va sinovga bog'liq:

### WannaCry uslubidagi hujumlar
- **Kamaytirish**: `Set-Ghost -SMBv1` zaif protokolni o'chiradi
- **Mulohaza**: Hech qanday eski tizim SMBv1-ni talab qilmasligiga ishonch hosil qiling

### RDP asosidagi Ransomware
- **Kamaytirish**: `Set-Ghost -RDP` masofaviy ish stoli kirishini bloklaydi
- **Mulohaza**: Muqobil masofaviy kirish usullari kerak bo'lishi mumkin

### Hujjat asosidagi zararli dastur
- **Kamaytirish**: `Set-Ghost -Macros` makros ijrosini o'chiradi
- **Mulohaza**: Qonuniy makros yoqilgan hujjatlarga ta'sir qilishi mumkin

### USB orqali yetkazilgan tahdidlar
- **Kamaytirish**: `Set-Ghost -USBStorage -AutoRun` USB funksionalligini cheklaydi
- **Mulohaza**: Qonuniy USB qurilma foydalanishiga ta'sir qilishi mumkin

## 🏢 Korxona xususiyatlari

### Group Policy qo'llab-quvvatlash
```powershell
# Group Policy registr orqali sozlamalarni qo'llash
Set-Ghost -SMBv1 -RDP -AutoRun -GroupPolicy

# GP yangilanishidan keyin sozlamalar domen bo'ylab qo'llaniladi
gpupdate /force
```

### Microsoft Intune integratsiyasi
```powershell
# Ghost sozlamalari uchun Intune siyosatlarini yaratish
Set-IntuneGhost -Settings $GhostSettings -Interactive

# Siyosatlar boshqariladigan qurilmalarga avtomatik joylanadi
```

### Muvofiqlik hisoboti
```powershell
# Xavfsizlik baholash hisobotini yaratish
Get-Ghost | Export-Csv -Path "Xavfsizlik-Audit-$(Get-Date -Format 'yyyy-MM-dd').csv"

# Azure xavfsizlik holati hisoboti
Get-AzureGhost | Out-File "Azure-Xavfsizlik-Hisoboti.txt"
```

## 📚 Eng yaxshi amaliyotlar

### Joylashtirish oldidan
1. **Joriy holatni hujjatlashtiring**: O'zgarishlardan oldin `Get-Ghost` ishga tushiring
2. **To'liq sinab ko'ring**: Ishlab chiqarish bo'lmagan muhitda tasdiqlang
3. **Qaytarish rejasini tuzing**: Har bir sozlamani qanday qaytarishni bilib oling
4. **Manfaatdorlar tekshiruvi**: Biznes bo'linmalari o'zgarishlarni ma'qullashini ta'minlang

### Joylashtirish paytida
1. **Bosqichma-bosqich yondashuv**: Avval pilot guruhlariga joylang
2. **Ta'sirni kuzating**: Foydalanuvchi shikoyatlari yoki tizim muammolarini kuzatib boring
3. **Muammolarni hujjatlashtiring**: Kelajakda murojaat qilish uchun har qanday muammoni yozing
4. **O'zgarishlarni xabar bering**: Xavfsizlik yaxshilanishlari haqida foydalanuvchilarni xabardor qiling

### Joylashtirish keyin
1. **Muntazam baholash**: Sozlamalarni tekshirish uchun vaqti-vaqti bilan `Get-Ghost` ishga tushiring
2. **Hujjatlarni yangilang**: Xavfsizlik konfiguratsiyalarini dolzarb saqlang
3. **Samaradorlikni ko'rib chiqing**: Xavfsizlik hodisalarini kuzatib boring
4. **Doimiy yaxshilash**: Tahdid manzarasiga asoslanib sozlamalarni sozlang

## 🔧 Muammolarni hal qilish

### Umumiy muammolar
- **Ruxsat xatolari**: Yuqori darajali PowerShell seansini ta'minlang
- **Xizmat bog'liqliklari**: Ba'zi xizmatlarda bog'liqliklar bo'lishi mumkin
- **Ilova mosligi**: Biznes ilovalar bilan sinab ko'ring
- **Tarmoq ulanishi**: Masofaviy kirish hali ham ishlayotganini tekshiring

### Tiklash variantlari
```powershell
# Kerak bo'lganda aniq xizmatlarni qayta yoqing
Set-RDP -Enable
Set-SMBv1 -Enable
Set-AutoRun -Enable
Set-Macros -Enable
```

## 👨‍💻 Muallif haqida

**Jim Tyler** - PowerShell uchun Microsoft MVP
- **YouTube**: [@PowerShellEngineer](https://youtube.com/@PowerShellEngineer) (10,000+ obunachi)
- **Axborot byulleteni**: [PowerShell.News](https://powershell.news) - Haftalik xavfsizlik razvedkasi
- **Muallif**: "PowerShell for Systems Engineers"
- **Tajriba**: PowerShell avtomatlashtirish va Windows xavfsizligida o'nlab yillar

## 📄 Litsenziya va javobgarlik rad etish

### MIT litsenziyasi
Ghost bepul foydalanish, o'zgartirish va tarqatish uchun MIT litsenziyasi ostida taqdim etiladi.

### Xavfsizlik javobgarlik rad etish
- **Kafolat yo'q**: Ghost hech qanday kafolatisiz "bor holatida" taqdim etiladi
- **Sinov zarur**: Har doim avval ishlab chiqarish bo'lmagan muhitlarda sinab ko'ring
- **Professional yo'l-yo'riq**: Ishlab chiqarish joylashtirish uchun xavfsizlik mutaxassislari bilan maslahatlashing
- **Operatsion ta'sir**: Mualliflar har qanday operatsion uzilish uchun javobgar emaslar
- **Keng qamrovli xavfsizlik**: Ghost to'liq xavfsizlik strategiyasining bir komponenti

### Qo'llab-quvvatlash
- **GitHub Issues**: [Xatolar haqida xabar berish yoki xususiyatlar so'rash](https://github.com/jimrtyler/Ghost/issues)
- **Hujjatlar**: Batafsil yordam uchun `Get-Help <function> -Full` dan foydalaning
- **Jamiyat**: PowerShell va xavfsizlik jamiyati forumlari

---

**🔒 Ghost bilan xavfsizlik holatini mustahkamlang - lekin har doim avval sinab ko'ring.**

```powershell
# Taxminlar bilan emas, baholash bilan boshlang
Get-Ghost
```

**⭐ Agar Ghost xavfsizlik holatini yaxshilashga yordam bersa, ushbu repozitoriyga yulduz qo'ying!**