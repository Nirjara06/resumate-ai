# 🎓 Resumate AI — AI-Powered Resume Analyzer & Interview Coach

<div align="center">

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python)
![Streamlit](https://img.shields.io/badge/Streamlit-1.40%2B-red?style=for-the-badge&logo=streamlit)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.5%2B-orange?style=for-the-badge&logo=scikit-learn)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

**Transform Your Career with Intelligent Resume Analysis**

[Features](#-features) · [Installation](#-installation) · [Usage](#-usage) · [Tech Stack](#-tech-stack) · [Project Structure](#-project-structure)

</div>

---

## 📖 Overview

**Resumate AI** is a full-stack AI-powered web application built with Streamlit that helps job seekers optimize their resumes, practice for interviews, and discover relevant job opportunities. It combines machine learning, NLP, and generative AI to provide personalized career guidance — all through an intuitive dark-themed interface.

---

## ✨ Features

### 👤 User Module — Resume Analysis
- **PDF Resume Upload & Parsing** — Extracts text from uploaded resumes using `pdfminer.six`
- **ATS Resume Scoring** — Scores resumes out of 100 based on key sections: contact info, summary, experience, education, skills, projects, certifications, achievements, and professional links
- **Career Field Prediction** — Automatically classifies the resume into fields such as Data Science, Web Development, Mobile Development, DevOps, Cybersecurity, or UI/UX Design using TF-IDF and cosine similarity
- **Skill Gap Analysis** — Detects existing skills and recommends missing skills for the predicted career field
- **Course Recommendations** — Suggests relevant online courses and curated YouTube video tutorials based on the user's field
- **Live Job Listings** — Fetches real-time job postings via the JSearch RapidAPI matching the candidate's profile
- **Resume Download Tips** — Actionable, section-by-section feedback to improve the resume score
- **User Level Detection** — Classifies the candidate as Fresher, Intermediate, or Experienced based on resume content

### 🛰️ AI Interview Questions
- **Configurable Mock Interviews** — Choose your career field and number of questions (5–15)
- **AI-Generated Questions** — Questions dynamically generated via the **Groq API** (Llama 3 8B) tailored to the selected role and difficulty
- **Fallback Question Bank** — Pre-built curated questions for all supported fields when the AI API is unavailable
- **AI Answer Evaluation** — Each submitted answer is evaluated by the Groq LLM for score (0–100), feedback, and improvement suggestions
- **Skip & Progress Tracking** — Users can skip questions; progress bar tracks completion
- **Interview Results Dashboard** — Displays overall score, number of good answers, time taken, and a full question-by-question breakdown
- **Session Persistence** — Interview data (scores, fields, time) is saved to CSV for admin analytics

### 💬 Feedback
- Users can submit star ratings (1–5) and written comments
- All feedback is stored and surfaced in the Admin dashboard

### 🔐 Admin Dashboard
- **Password-protected** admin panel
- **User Analytics** — Visualizes resume score distributions, predicted fields, candidate levels, and skill trends using Plotly charts
- **K-Means User Clustering** — Groups users into High Performers (90–100), Average (75–89), and Low Performers (<75) based on ATS scores
- **Interview Analytics** — Tracks interview sessions, field-wise difficulty, score distributions, fastest completions, and top performers
- **User Data Table** — Full downloadable CSV of all resume submissions
- **Feedback Overview** — Aggregated rating and comment viewer

### ℹ️ About
- Overview of the application, team information, and technology stack

---

## 🛠 Tech Stack

| Category | Technology |
|---|---|
| Frontend / UI | Streamlit, Plotly, Custom CSS |
| PDF Processing | pdfminer.six |
| Machine Learning | scikit-learn (TF-IDF, Cosine Similarity, K-Means, PCA) |
| NLP | NLTK (stopwords, tokenization) |
| Generative AI | Groq API (Llama 3 8B) |
| Job Data | JSearch API via RapidAPI |
| Geolocation | geocoder, geopy |
| Data Handling | Pandas, NumPy |
| Image Processing | Pillow |
| Storage | CSV-based flat-file persistence |

---

## 📁 Project Structure

```
resumate-ai/
├── app2.py                  # Main application (single-file Streamlit app)
├── requirements.txt         # Python dependencies
├── resumate_data/           # Auto-created on first run
│   ├── users.csv            # User resume submission records
│   ├── feedback.csv         # User feedback data
│   └── interviews.csv       # Interview session records
├── uploaded_resumes/        # Auto-created directory for uploaded PDF files
└── Logo/
    └── Resu.png             # App logo (optional)
```

---

## ⚙️ Installation

### Prerequisites

- Python 3.8 or higher
- pip

### 1. Clone the Repository

```bash
git clone https://github.com/Nirjara06/resumate-ai.git
cd resumate-ai
```

### 2. Create a Virtual Environment (Recommended)

```bash
python -m venv venv
source venv/bin/activate        # On Windows: venv\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Set Up Environment Variables

The application uses two external APIs. Set the following environment variable:

```bash
export GROQ_API_KEY="your_groq_api_key_here"
```

On Windows:
```cmd
set GROQ_API_KEY=your_groq_api_key_here
```

> **Note:** A RapidAPI key for JSearch (job listings) is embedded in the code. For production use, move it to an environment variable as well.

### 5. Run the Application

```bash
streamlit run app2.py
```

The app will open at `http://localhost:8501` in your browser.

---

## 🚀 Usage

### For Job Seekers
1. Select **User** from the sidebar
2. Enter your name, email, and mobile number
3. Upload your resume as a **PDF file**
4. View your ATS score, predicted career field, detected skills, recommended skills, course suggestions, and live job listings

### For Interview Practice
1. Select **AI Interview Questions** from the sidebar
2. Enter your name and email
3. Choose your target career field and number of questions
4. Click **Start AI Interview**
5. Answer each question and receive instant AI-powered feedback
6. Review your full performance report at the end

### For Admins
1. Select **Admin** from the sidebar
2. Enter the admin password
3. Explore user analytics, clustering insights, interview data, and feedback

---

## 🔑 API Keys

| API | Purpose | How to Get |
|---|---|---|
| **Groq API** | AI interview question generation & answer evaluation | [console.groq.com](https://console.groq.com) |
| **RapidAPI (JSearch)** | Live job listings | [rapidapi.com/letscrape-6bRBa3QguO5/api/jsearch](https://rapidapi.com/letscrape-6bRBa3QguO5/api/jsearch) |

---

## 📊 Supported Career Fields

Resumate AI currently supports analysis and interview preparation for the following fields:

- **Data Science** — Python, ML, Deep Learning, NLP, Tableau, Power BI, and more
- **Web Development** — HTML, CSS, JavaScript, React, Node.js, Django, REST APIs, and more
- **Mobile Development** — Android, iOS, Flutter, React Native, Swift, Kotlin, and more
- **DevOps** — Docker, Kubernetes, AWS, CI/CD, Terraform, Linux, and more
- **Cybersecurity** — Penetration Testing, Network Security, Ethical Hacking, and more
- **UI/UX Design** — Figma, Adobe XD, Wireframing, Prototyping, and more

---

## 🤝 Contributing

Contributions are welcome! To get started:

1. Fork the repository
2. Create a new branch: `git checkout -b feature/your-feature-name`
3. Make your changes and commit: `git commit -m "Add your feature"`
4. Push to your fork: `git push origin feature/your-feature-name`
5. Open a Pull Request

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

## 👩‍💻 Built By

**Team Resumate AI** — built with 🤍 to help candidates land their dream jobs.

---

> **Tip:** For the best experience, use a modern browser and ensure your resume PDF contains selectable (non-scanned) text for accurate parsing.
