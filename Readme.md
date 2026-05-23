# 🧬 MedAI — AI Medical Assistant

> ระบบผู้ช่วยแพทย์อัจฉริยะที่พัฒนาด้วย Python, FastAPI, Google Gemini และ YOLO

---

## 👨‍💻 ผู้จัดทำ

| รายละเอียด | ข้อมูล |
|---|---|
| **ชื่อ-นามสกุล** | นาย สิปปกร แก้วกลม |
| **โรงเรียน** | ราชประชาสมาสัย ฝ่ายมัธยม รัชดาภิเษก ใน พระบรมราชูปถัมภ์ |
| **สาขาที่สนใจ** | Biomedical Engineering |

---

## 📌 ภาพรวมโปรเจค

**MedAI** คือระบบ AI Medical Assistant ที่ช่วยสนับสนุนการทำงานของบุคลากรทางการแพทย์ โดยนำเทคโนโลยี AI มาประยุกต์ใช้ใน 4 ด้านหลัก ได้แก่ การวิเคราะห์ภาพทางการแพทย์, การให้คำปรึกษาผ่าน AI Chatbot, การแสดงสถิติผู้ป่วย และการค้นหาข้อมูลผู้ป่วย

---

## ✨ ฟีเจอร์หลัก

### 1. 📊 Dashboard
- แสดงสถิติข้อมูลผู้ป่วยแบบ Real-time จาก `/patient/stats`
- แสดงจำนวนผู้ป่วยทั้งหมด, อายุเฉลี่ย, โรคที่พบบ่อย, หมู่เลือด และเพศ

### 2. 🔬 Image Analysis
- รองรับการวิเคราะห์ **X-ray** ด้วย YOLO Classification Model
- รองรับการนับ **เซลล์เลือด** ด้วย YOLO Detection Model
- อัปโหลดภาพแบบ Drag & Drop พร้อมแสดงผลและ Confidence Score

### 3. 🤖 AI Doctor Chat
- แชทให้คำปรึกษาด้านสุขภาพด้วย **Google Gemini 2.0 Flash**
- จดจำบทสนทนาต่อเนื่องผ่านระบบ Session
- ตอบเป็นภาษาไทยที่เข้าใจง่าย

### 4. 🔍 Patient Search
- ค้นหาผู้ป่วยด้วยชื่อ, โรค/อาการ หรือหมู่เลือด
- แสดงผลเป็นตารางพร้อมข้อมูลครบถ้วน

---

## 🛠️ เทคโนโลยีที่ใช้

### Backend
| เทคโนโลยี | การใช้งาน |
|---|---|
| **Python** | ภาษาหลักในการพัฒนา |
| **FastAPI** | Web Framework สำหรับ REST API |
| **Google Gemini 2.0 Flash** | AI สำหรับ Chatbot ให้คำปรึกษา |
| **YOLO (Ultralytics)** | วิเคราะห์ภาพ X-ray และเซลล์เลือด |
| **Pandas** | จัดการข้อมูลผู้ป่วยจาก CSV |
| **Uvicorn** | ASGI Server |

### Frontend
| เทคโนโลยี | การใช้งาน |
|---|---|
| **HTML5 / CSS3** | โครงสร้างและ Styling |
| **Vanilla JavaScript** | Logic และ Fetch API |
| **Single Page Application** | ระบบ Tab Navigation ไม่โหลดหน้าใหม่ |

---

## 📁 โครงสร้างโปรเจค

```
medai-project/
│
├── backend_simple.py          # FastAPI Backend หลัก
├── ai-medical-assistant.html  # Frontend (Single File)
├── healthcare_dataset.csv     # ฐานข้อมูลผู้ป่วย
├── .env                       # เก็บ API Key (ไม่ควร commit)
├── requirements.txt           # Python dependencies
│
└── models/
    ├── xray_best.pt           # YOLO Model สำหรับ X-ray
    └── blood_best.pt          # YOLO Model สำหรับเซลล์เลือด
```

---

## ⚙️ วิธีติดตั้งและรัน

### 1. ติดตั้ง Dependencies

```bash
pip install fastapi uvicorn google-generativeai ultralytics pillow pandas python-dotenv
```

### 2. ตั้งค่า API Key

สร้างไฟล์ `.env` แล้วใส่:

```env
GEMINI_API_KEY=your_gemini_api_key_here
```

### 3. รัน Backend

```bash
python backend_simple.py
```

Backend จะทำงานที่ `http://localhost:8000`
ดูเอกสาร API ได้ที่ `http://localhost:8000/docs`

### 4. รัน Frontend

```bash
python -m http.server 5500
```

เปิด browser ไปที่ `http://localhost:5500` แล้วคลิก `ai-medical-assistant.html`

---

## 🔌 API Endpoints

| Method | Endpoint | คำอธิบาย |
|---|---|---|
| `GET` | `/` | ทดสอบว่า Server ทำงาน |
| `GET` | `/patient/stats` | ดึงสถิติข้อมูลผู้ป่วย |
| `POST` | `/patient/search` | ค้นหาผู้ป่วย |
| `POST` | `/analyze` | วิเคราะห์ภาพทางการแพทย์ |
| `POST` | `/chat` | แชทกับ AI แพทย์ |
| `GET` | `/chat/clear/{session_id}` | ล้างประวัติการสนทนา |

---

## 💡 แนวคิดและที่มา

โปรเจคนี้เกิดจากความสนใจใน **Biomedical Engineering** ที่ต้องการนำ AI มาช่วยในงานทางการแพทย์ เพื่อลดภาระของบุคลากร ลดโอกาสผิดพลาด และเพิ่มความรวดเร็วในการวินิจฉัยเบื้องต้น โดยเฉพาะการนำ Computer Vision มาวิเคราะห์ภาพ X-ray และเซลล์เลือด ซึ่งตรงกับหลักการของ Biomedical Engineering ที่ผสานวิทยาศาสตร์การแพทย์เข้ากับวิศวกรรมศาสตร์

---

## ⚠️ ข้อควรระวัง

> ระบบนี้พัฒนาเพื่อการศึกษาเท่านั้น ผลการวินิจฉัยจาก AI **ไม่สามารถใช้แทนการวินิจฉัยของแพทย์ผู้เชี่ยวชาญได้** ควรปรึกษาแพทย์เสมอ

---

*พัฒนาโดย นาย สิปปกร แก้วกลม — โรงเรียนราชประชาสมาสัย ฝ่ายมัธยม*