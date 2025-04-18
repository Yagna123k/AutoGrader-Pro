# AutoGrader Pro – A Secure Docker-Powered Python Assignment Evaluator

## 🌎 Overview
AutoGrader Pro is a containerized Python-based system for securely and automatically evaluating programming assignments. Designed for schools, universities, and coding bootcamps, this platform provides a powerful, scalable, and secure way to test and grade Python code submissions in isolated Docker environments.

## 🚀 Key Features
- 📄 **Instructor Test Suite Upload**: Instructors upload assignments with test cases and expected outputs.
- ⚖️ **Secure Evaluation Engine**: Submissions are executed in isolated Docker containers with resource limits.
- 🤖 **Student Submission Portal (CLI/Web)**: Students submit their code via CLI or web interface.
- 🔧 **Customizable Environments**: Supports assignment-specific dependencies via requirements.txt.
- ✅ **Auto Grading**: Uses `pytest` or custom logic to evaluate student submissions.
- 📊 **Results Dashboard**: Displays student scores, error logs, and feedback.
- 🔄 **Versioned Assignment Environments**: Tracks historical environments with Python and package versions.

## ⚡ Tech Stack

- **Language**: Python 3.10+  
- **Frontend**: React.js + Tailwind CSS + Shadcn UI  
- **Backend**: Django + Django REST Framework  
- **Database**: MongoDB  
- **Containerization**: Docker + Docker Compose  
- **Async Tasks**: Celery + Redis 

## 🏁 Getting Started

### Prerequisites
- Docker
- Python 3.10+
- Git
- (Optional) Node.js (for frontend dashboard)

### Installation
```bash
git clone https://github.com/Yagna123k/AutoGrader-Pro.git
cd AutoGrader-Pro
```

#### Backend Setup
```bash
cd backend
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

#### Frontend Setup (Optional)
```bash
cd frontend
npm install
npm run dev
```

## 📂 Project Structure
```
AutoGrader-Pro/
├── backend/                         # Django Backend
│   ├── core/                        # Main Django project (settings, urls, etc.)
│   ├── wellness/                   # Django App for main functionality
│   ├── manage.py
│   └── requirements.txt
│
├── frontend/                        # React Frontend
│   ├── public/
│   ├── src/
│   ├── tailwind.config.js
│   ├── package.json
│   └── .env
│
├── docker/                         # Docker-related files
│   ├── django.Dockerfile
│   ├── react.Dockerfile
│   └── nginx/
│       └── default.conf
│
├── docker-compose.yml              # Docker Compose file
├── .env                            # Root env file
└── README.md
```

## 🧰 Instructor Workflow
1. Upload assignment description + test cases (YAML or Python test files).
2. Define any required packages in `requirements.txt`.
3. System generates a unique assignment ID and environment.

## 🧒 Student Workflow
1. Fetch the assignment using CLI or web UI.
2. Submit a `.py` file through the portal or CLI.
3. System spins up a Docker container with exact requirements and runs tests.
4. Student receives score, error logs, and suggestions.

## ⛏ Docker Integration
Each submission spins up a short-lived container that:
- Installs dependencies
- Copies test cases and user code
- Executes the test suite using `pytest`
- Times out or kills container if limits exceeded

```dockerfile
# Dockerfile.dynamic
FROM python:3.10-slim
WORKDIR /app
COPY . /app
RUN pip install -r requirements.txt
CMD ["pytest", "--tb=short", "--maxfail=1"]
```

## 🥵 Security & Isolation
- Containers auto-remove after execution.
- Memory/CPU limits to prevent abuse.
- Sandboxing user input to prevent system access.

## ⚒ Customization Options
- Select `pytest` or custom evaluation script.
- Set strict time/memory/resource limits.
- Add static code analysis (flake8, pylint).

## 🌐 Live Demo (Coming Soon)
- Hosted at: coming soon...

## 💼 Use Cases
- Universities grading hundreds of Python assignments
- Coding bootcamps that need instant feedback
- Teachers who want reproducible grading environments

## 🛠️ Future Enhancements
- Role-based dashboard (student, instructor, admin)
- Integration with GitHub Classroom
- Real-time result streaming
- API to integrate with LMS (like Moodle or Canvas)

## 💬 Contact & Contributing
- GitHub: [Yagna123k/AutoGrader-Pro](https://github.com/Yagna123k/AutoGrader-Pro)
- Contributions welcome! Fork the repo and submit a PR

## 📄 License
MIT License. See `LICENSE` for details.
