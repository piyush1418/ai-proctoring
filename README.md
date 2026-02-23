# 🎓 AI-Based Online Exam Proctoring System

## 📋 Project Overview

An intelligent, AI-powered online examination platform that ensures academic integrity through real-time monitoring and multi-modal cheating detection. Built with Django and advanced computer vision technologies, this system provides comprehensive proctoring capabilities for remote assessments.

## ✨ Key Features

### 🔐 Multi-Modal Proctoring
- **Real-time Camera Monitoring**: Continuous video surveillance during exams
- **Gaze Tracking**: Detects when students look away from the screen
- **Object Detection**: Identifies unauthorized items (phones, books, multiple persons)
- **Audio Detection**: Monitors for suspicious sounds and conversations
- **Tab Switch Detection**: Tracks and limits window/tab switching attempts

### 📝 Comprehensive Exam Management
- **Multiple Question Types**: 
  - Objective (MCQ) questions
  - Subjective (text-based) questions
  - Coding questions with multi-language support (Python, C++, Java)
- **Dynamic Question Randomization**: Unique question order for each student
- **Timed Assessments**: Automatic submission on time expiry
- **Fullscreen Mode Enforcement**: Prevents exam window minimization

### 📊 Advanced Analytics & Reporting
- **Cheating Severity Scoring**: 0-100 scale integrity assessment
- **Visual Performance Charts**: 
  - Score distribution (pie chart)
  - Knowledge assessment (bar chart)
  - Cheating incident breakdown
  - Overall integrity gauge
- **Detailed Incident Logs**: Timestamped records of all suspicious activities
- **Complete Solutions Display**: Post-exam answer review with correct solutions

### 👥 Role-Based Access Control
- **Student Dashboard**: Exam access, profile management, result viewing
- **Admin Dashboard**: Question management, student monitoring, comprehensive reports
- **Secure Authentication**: Login/registration with photo verification

## 🛠️ Technology Stack

### Backend
- **Framework**: Django 5.1.5
- **Database**: SQLite3
- **Server**: Gunicorn (production)

### AI/ML Technologies
- **Computer Vision**: OpenCV, MediaPipe
- **Object Detection**: YOLOv11 (Ultralytics)
- **Deep Learning**: PyTorch
- **Image Processing**: Pillow

### Frontend
- **UI Framework**: Bootstrap 5.3
- **Charts**: Chart.js
- **Icons**: Font Awesome
- **Styling**: Custom CSS with modern animations

## 🚀 Installation & Setup

### Prerequisites
```bash
Python 3.10+
pip
virtualenv (recommended)
```

### Quick Start
```bash
# Clone repository
git clone https://github.com/piyush1418/ai-proctoring.git
cd ai-proctoring/futurproctor

# Create virtual environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run migrations
python manage.py migrate --skip-checks

# Create superuser
python manage.py createsuperuser

# Start server
python manage.py runserver
```

Access at: `http://localhost:8000`

## 📁 Project Structure

```
futurproctor/
├── proctoring/              # Main app
│   ├── models.py           # Database models
│   ├── views.py            # Business logic
│   ├── urls.py             # URL routing
│   ├── forms.py            # Form handling
│   ├── templates/          # HTML templates
│   ├── static/             # CSS, JS, images
│   ├── ml_models/          # AI detection modules
│   └── dummy_data/         # Sample questions (ai.json)
├── futurproctor/           # Project settings
├── media/                  # Uploaded files
├── db.sqlite3             # Database
└── manage.py              # Django CLI
```

## 🎯 Core Functionality

### Cheating Detection System
1. **Tab Switch Monitoring**: Tracks visibility changes, terminates after 5 switches
2. **Gaze Tracking**: Uses MediaPipe for eye movement analysis
3. **Object Detection**: YOLOv11 identifies phones, books, multiple persons
4. **Audio Analysis**: Detects speech and suspicious sounds
5. **Fullscreen Enforcement**: Prevents exam window manipulation

### Integrity Scoring Algorithm
```
Severity Score = (Tab Switches × 15) + (Objects × 20) + 
                 (Multiple Persons × 25) + (Audio × 10) + 
                 (Gaze Issues × 5)
```

Categories:
- **Critical** (75-100): Severe violations
- **High** (50-74): Major concerns
- **Medium** (25-49): Moderate issues
- **Low** (0-24): Minor infractions

## 👨‍💻 Team

- **Piyush Raj** - Project Lead & Data Engineer
- **Varun Suthar** - ML Engineer
- **Ishika Gurjar** - Data Analyst
- **Mohd. Sameer** - Frontend Engineer

## 🔒 Security Features

- CSRF protection enabled
- Secure session management
- Password validation
- SQL injection prevention
- XSS protection
- Clickjacking prevention

## 📈 Future Enhancements

- [ ] Cloud storage integration (AWS S3)
- [ ] PostgreSQL database support
- [ ] Real-time WebSocket notifications
- [ ] Advanced facial recognition
- [ ] Mobile app support
- [ ] Multi-language interface
- [ ] Plagiarism detection for coding questions

## 📄 License

This project is developed for educational purposes.

## 🤝 Contributing

Contributions welcome! Please fork the repository and submit pull requests.

## 📞 Contact

For queries or support:
- GitHub: [@piyush1418](https://github.com/piyush1418)
- LinkedIn: [Piyush Raj](https://www.linkedin.com/in/piyush-raj-ab2260260)

---

**Built with ❤️ by Team FutureProctor**
