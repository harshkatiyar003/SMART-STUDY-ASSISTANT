# 🎓 Smart Study Assistant

**An AI-Powered Academic Support & Student Productivity System**

A full-stack Python application combining a Flask REST backend with a CustomTkinter desktop GUI. It helps students manage schedules and tasks, track attendance, visualize performance, and supports AI-driven features like quiz generation, OCR note processing, and grade prediction.

---

## 📋 Table of Contents

- [Features](#features)
- [Project Structure](#project-structure)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
- [API Reference](#api-reference)
- [Desktop Application](#desktop-application)
- [Future Improvements](#future-improvements)
- [Author](#author)

---

## ✨ Features

- **Attendance Management** — Mark attendance manually or via simulated auto-detection (QR/proximity/facial recognition)
- **Real-Time Attendance View** — See which students are present in a class at any moment
- **Daily Schedule** — Fetch personalized class schedules per student
- **Personalized Tasks & Goals** — View AI-curated tasks and long-term learning goals for each student
- **Daily Routine Generator** — Auto-composes a full structured day combining classes, study blocks, tasks, and goals
- **Performance Graphs** — Visualize student performance using Matplotlib charts
- **Student & Course Management** — Add/remove students and courses; import data from CSV
- **Note Upload & OCR** — Upload image/PDF notes; extract text using Tesseract OCR
- **Quiz Generation** — Auto-generate quizzes from extracted note content
- **Grade Prediction** — Predict student grades using a Linear Regression model (Scikit-learn)
- **QR Code Generation** — Generate QR codes for students

---

## 📁 Project Structure

```
smart-study-assistant/
│
├── app.py                  # Flask REST API backend
├── main_app.py             # CustomTkinter desktop GUI frontend
│
├── templates/              # HTML templates (for web frontend)
│   ├── index.html
│   ├── upload.html
│   ├── quiz.html
│   └── result.html
│
├── static/                 # CSS & JavaScript
│   ├── style.css
│   └── script.js
│
├── uploads/                # Uploaded student note files (auto-created)
│
└── requirements.txt        # Python dependencies
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Backend | Python, Flask |
| Desktop GUI | CustomTkinter, Tkinter |
| Machine Learning | Scikit-learn (Linear Regression) |
| OCR | Tesseract |
| Data Visualization | Matplotlib |
| Image Processing | OpenCV, Pillow |
| Data Handling | Pandas, NumPy |
| QR Codes | qrcode |
| Frontend (Web) | HTML, CSS, JavaScript |

---

## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- Tesseract OCR installed on your system
  - Windows: [Download installer](https://github.com/UB-Mannheim/tesseract/wiki)
  - Linux: `sudo apt install tesseract-ocr`
  - macOS: `brew install tesseract`

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/smart-study-assistant.git
   cd smart-study-assistant
   ```

2. **Create and activate a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate      # macOS/Linux
   venv\Scripts\activate         # Windows
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

### Running the Application

**Step 1 — Start the Flask backend:**
```bash
python app.py
```
The server will run at `http://127.0.0.1:5000`.

**Step 2 — Launch the desktop GUI** (in a separate terminal):
```bash
python main_app.py
```

> The GUI communicates with the Flask backend via HTTP, so both must be running simultaneously.

---

## 📡 API Reference

### Health Check
```
GET /
```
Returns a confirmation that the backend is running.

---

### Attendance

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/attendance` | Mark attendance for a student in a class |
| `GET` | `/realtime_attendance/<class_id>` | Get real-time attendance for a class |

**POST `/attendance` — Request Body:**
```json
{
  "student_id": "S001",
  "class_id": "C101"
}
```

---

### Schedule & Tasks

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/schedule/<student_id>` | Get the class schedule for a student |
| `GET` | `/tasks/<student_id>` | Get personalized tasks for a student |
| `GET` | `/daily_routine/<student_id>` | Get a full generated daily routine |

---

### Data Management

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/update_data` | Add new students and sync backend data |

**POST `/update_data` — Request Body:**
```json
{
  "students": {
    "S021": "New Student Name"
  }
}
```

---

## 🖥️ Desktop Application

The GUI (`main_app.py`) is built with **CustomTkinter** and organized into five tabs:

| Tab | Features |
|---|---|
| **Attendance** | Manual checkbox attendance, simulated auto-marking |
| **Schedule & Tasks** | View schedule and personalized tasks by student ID |
| **Performance** | Performance graphs, real-time attendance display |
| **Manage Data** | Add/remove students and courses, CSV import |
| **About & Resources** | Project info and links |

### Sample Student IDs (pre-loaded)

| ID | Name |
|---|---|
| S001 | Alice Johnson |
| S002 | Bob Smith |
| S003 | Charlie Brown |

### Sample Course IDs (pre-loaded)

| ID | Course |
|---|---|
| C101 | Introduction to Python |
| C102 | Data Structures |
| C103 | Web Development |
| C104 | Database Systems |
| C105 | Machine Learning |

---

## 🔮 Future Improvements

- NLP-based AI question generator for smarter quizzes
- User login and authentication system
- Cloud deployment (AWS / Heroku / Render)
- Real database integration (PostgreSQL / SQLite)
- Mobile-friendly web interface
- Actual facial recognition and QR-based attendance

---

## 👤 Author

**Vedant Mishra**

---

## 📄 License

This project is developed for academic purposes. Feel free to fork and build on it.
