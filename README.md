# Manga Translator — ดาวน์โหลด / Releases

โปรแกรมแปลมังงะ / มังฮวา **อังกฤษ → ไทย** บน Windows: อ่านข้อความในภาพ (OCR) → แปลด้วย AI → ลบข้อความเดิม →
วางคำแปลไทยลงในบอลลูน · มีคลังเรื่อง/ตอน, แก้ผลแปลเอง, ตัดหน้าใหม่, ทำปก, export

repo นี้มีไว้**ปล่อยตัวติดตั้งและไฟล์อัพเดต**เท่านั้น (source code อยู่ repo แยก)

**[⬇ ดาวน์โหลดเวอร์ชันล่าสุด](https://github.com/SilSea/translate_manga-releases/releases/latest)**

---

## ต้องมีอะไร

- Windows 10 / 11 แบบ 64-bit
- อินเทอร์เน็ตตอนติดตั้ง (โหลด library ~300 MB – 3 GB)
- ไม่ต้องมี Python · ไม่ต้องใช้สิทธิ์ admin
- การ์ดจอ NVIDIA ช่วยให้เร็วขึ้น (ไม่มีก็ใช้ CPU ได้)
- AI สำหรับแปล เลือกอย่างใดอย่างหนึ่ง:
  - [Claude Code](https://claude.com/claude-code) (ค่าเริ่มต้น) — ติดตั้งแยก แล้ว login (`claude` → `/login`)
  - Claude API / OpenAI-compatible API (ใส่ key ในโปรแกรม) / Ollama (รันในเครื่อง)

## ติดตั้ง

1. ไปที่ [Releases ล่าสุด](https://github.com/SilSea/translate_manga-releases/releases/latest) → โหลด
   `MangaTranslator-Setup-<version>.exe`
2. ดับเบิลคลิก → เลือก shortcut บน Desktop / โหลด model ตอนติดตั้งเลย (~300 MB)
3. หน้าต่างสีดำจะโหลด library (PyTorch แบบ GPU หรือ CPU เลือกให้เอง) ใช้เวลา 5–15 นาที **ห้ามปิดหน้าต่างนั้น**
4. เปิดจาก Start menu → **Manga Translator**

> Windows SmartScreen อาจเตือน "Windows protected your PC" เพราะตัวติดตั้งไม่มีใบรับรองของ Microsoft
> กด **More info → Run anyway**

ติดตั้งไม่สำเร็จ / เน็ตหลุดระหว่างติดตั้ง: ต่อเน็ตแล้วเปิด Start menu → **Repair Manga Translator** (รันซ้ำได้ ปลอดภัย)

บังคับใช้ GPU หรือ CPU:

```bat
MangaTranslator-Setup-<version>.exe /TORCH=cuda
MangaTranslator-Setup-<version>.exe /TORCH=cpu
```

## อัพเดต

- โปรแกรมเช็คเวอร์ชันใหม่เองทุกครั้งที่เปิด → แถบด้านบน **🔄 มีเวอร์ชันใหม่** → กด **อัพเดต**
- ติดตั้งเสร็จโปรแกรมเปิดใหม่เอง · ถ้าเวอร์ชันใหม่เปิดไม่ขึ้น จะย้อนกลับเวอร์ชันเดิมให้เอง
- งานในคลัง ตั้งค่า ลายน้ำ **ไม่ถูกแตะ**
- เครื่องไม่มีเน็ต: โหลดไฟล์ `.mtupdate` จากหน้า Releases มาทาง USB / แชท → เมนู **ช่วยเหลือ → 📦 อัพเดตจากไฟล์…**
- ย้อนเวอร์ชัน: เมนู **ช่วยเหลือ → ↺ ย้อนไปเวอร์ชันก่อน**
- หรือโหลด setup เวอร์ชันใหม่มาติดตั้งทับ ก็ได้ งานและตั้งค่ายังอยู่

ไฟล์อัพเดตทุกไฟล์มี**ลายเซ็นดิจิทัล**ของผู้ทำโปรแกรม ไฟล์ที่ถูกแก้หรือปลอมจะติดตั้งไม่ได้

## ไฟล์ในแต่ละ release

| ไฟล์ | ใช้ทำอะไร |
|---|---|
| `MangaTranslator-Setup-<v>.exe` | ตัวติดตั้ง — **ผู้ใช้ใหม่โหลดอันนี้** |
| `MangaTranslator-<v>.mtupdate` | ไฟล์อัพเดต (โปรแกรมโหลดเอง หรือใช้ "อัพเดตจากไฟล์") |
| `MangaTranslator-<v>-offline.mtupdate` | ไฟล์อัพเดตสำหรับเครื่องไม่มีเน็ต (รวม library ที่เปลี่ยนแล้ว) — มีบางเวอร์ชัน |
| `latest.json`, `latest.json.sig` | ข้อมูลเวอร์ชันล่าสุด + ลายเซ็น ให้โปรแกรมเช็คอัพเดต (ไม่ต้องโหลดเอง) |

## ไฟล์ของโปรแกรมอยู่ไหน

ติดตั้งที่ `%LOCALAPPDATA%\Programs\MangaTranslator`

- งานของคุณ: `library\` · ตั้งค่า: `gui_settings.json` · ลายน้ำ: `watermarks\`
- **Uninstall** ลบตัวโปรแกรม, Python, library, model แต่**เก็บคลัง ตั้งค่า ลายน้ำไว้** — ลบเองถ้าไม่ใช้แล้ว
- model EasyOCR อยู่ที่ `%USERPROFILE%\.EasyOCR` (ไม่ถูกลบตอน uninstall)
- โปรแกรมมีปัญหา: เมนู **ช่วยเหลือ → เปิด folder log**

## แจ้งปัญหา

เปิด [Issue](https://github.com/SilSea/translate_manga-releases/issues) พร้อมบอกเวอร์ชัน (เมนู **ช่วยเหลือ → เกี่ยวกับ**),
ขั้นตอนที่ทำ และแนบไฟล์ log ถ้ามี

---

## English

**Manga Translator** — an English → Thai manga/manhwa translator for Windows (OCR → AI translation → text removal
→ Thai typesetting). This repository only hosts the installer and signed update packages.

1. Download `MangaTranslator-Setup-<version>.exe` from the
   [latest release](https://github.com/SilSea/translate_manga-releases/releases/latest).
2. Run it (Windows 10/11 64-bit, no admin rights, no Python needed). It downloads PyTorch (GPU or CPU) and other
   libraries — keep the console window open (5–15 min).
3. Start **Manga Translator** from the Start menu. Switch the UI to English in
   **ตั้งค่า (Settings) → 🌏 ภาษา / Language**.

Translation uses [Claude Code](https://claude.com/claude-code) by default (install and log in separately), or the
Claude API, an OpenAI-compatible API, or Ollama. The program checks this repository for updates on start; every
update package is signed and a broken update rolls back automatically. Your library and settings are kept on update
and uninstall.
