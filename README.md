QR Code Attendance System

🔗 Live Demo: qr-code-attendance-system-l04f.onrender.com

A smart, location-aware attendance management system built with Django, allowing teachers to generate time-limited QR codes for each class session and students to mark their attendance by scanning them.

🚀 Features
Dynamic QR Code Generation — Teachers generate a unique QR code for each class/subject session
Time-Limited Sessions — QR codes automatically expire after a set duration, preventing proxy attendance
Class Year & Subject Filtering — Dependent dropdowns to select class year and subject dynamically
Live Dashboard — Real-time attendance statistics (total students, present today, attendance rate)
Excel Export — Download daily attendance records as an .xlsx file
Student Self-Service — Students scan the QR and enter their roll number to mark attendance
Duplicate Prevention — Students can't mark attendance twice for the same session
Admin Panel — Manage Class Years, Subjects, Students, and Attendance Records
🛠️ Tech Stack
Backend: Python, Django 5.1
Database: SQLite (local) / PostgreSQL (production)
QR Generation: qrcode + Pillow
Reports: openpyxl (Excel export)
Frontend: Bootstrap 5, Font Awesome
Deployment: Render (Gunicorn + Whitenoise)
📦 Local Setup
bash
# 1. Clone the repository
git clone https://github.com/kalevaishnavi04/QR_code-Attendance-System.git
cd QR_code-Attendance-System/attendance_system

# 2. Create and activate a virtual environment
python -m venv venv
venv\Scripts\activate        # Windows
source venv/bin/activate     # Mac/Linux

# 3. Install dependencies
pip install -r requirements.txt

# 4. Run migrations
python manage.py migrate

# 5. Create an admin/teacher account
python manage.py createsuperuser

# 6. Run the development server
python manage.py runserver

Visit http://127.0.0.1:8000/ in your browser.

📱 Testing on your phone (same WiFi network)
bash
python manage.py runserver 0.0.0.0:8000

Then find your PC's local IP (ipconfig → IPv4 Address) and open http://<your-ip>:8000/login/ on both your PC and phone (both must be on the same WiFi).

⚙️ Admin Panel Setup

After creating a superuser, log in at /admin/ and add:

Class Years (e.g., FY, SY, TY)
Subjects (linked to a Class Year and assigned Teachers)
Students (linked to a Class Year)
☁️ Deployment (Render)
Push this repo to GitHub
On Render, create a New Web Service and connect the repo
Settings:
Root Directory: attendance_system
Build Command: ./build.sh
Start Command: gunicorn attendance_system.wsgi
Add environment variables:
SECRET_KEY
DEBUG=False
DATABASE_URL (recommended — attach a Render PostgreSQL instance)
📁 Project Structure
attendance_system/
├── attendance_system/    # Project settings, URLs, WSGI/ASGI
├── core/                 # Main app: models, views, forms, admin
├── templates/core/       # HTML templates
├── manage.py
├── requirements.txt
└── build.sh              # Render build script
👩‍💻 Author

Vaishnavi Kale — GitHub · Portfolio
