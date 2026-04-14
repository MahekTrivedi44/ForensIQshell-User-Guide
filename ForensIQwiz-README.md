# ForensIQwiz - Cybersecurity Quiz Adventure 🏰

## Overview

ForensIQwiz is an AI-powered cybersecurity quiz platform built with Streamlit. It gamifies learning through a fantasy RPG-style experience where users earn XP, level up, collect pets, and compete on a global leaderboard — all while mastering digital forensics and cybersecurity concepts.

## Features

- 🤖 **AI-Powered Questions**: Uses Groq's Llama 3.1 model to generate dynamic quiz questions
- 📄 **PDF Quiz Generation**: Upload any PDF document and generate a quiz from its content
- 🧙‍♂️ **RPG Progression System**: Earn XP, level up, and track your wizard rank
- 🏆 **Global Leaderboard**: Compete with other users on a live podium-style leaderboard
- 💡 **Hint System**: Request AI-generated hints when you're stuck (with XP penalty)
- ✅ **Daily Tasks**: Complete daily challenges to earn bonus XP and maintain streaks
- 🐾 **Collectible Pets**: Unlock animated companion pets at 200+ XP
- 🔐 **User Authentication**: Secure signup/login with bcrypt password hashing
- ☁️ **Firebase Backend**: Real-time Firestore database for persistent user data

## System Requirements

- **Python**: 3.8 or higher
- **Internet**: Required for Groq API calls and Firebase
- **Firebase Project**: Firestore database with service account credentials
- **Groq API Key**: Free key from [console.groq.com](https://console.groq.com/)

## Installation & Setup

### Step 1: Clone and Navigate

```bash
git clone <your-repo-url>
cd forensiqwiz
```

### Step 2: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 3: Configure API Keys

Create a `.env` file in the project root:

```env
GROQ_API_KEY=your_groq_api_key_here
```

### Step 4: Set Up Firebase

1. Create a Firebase project at [console.firebase.google.com](https://console.firebase.google.com/)
2. Enable Firestore Database
3. Generate a service account key (Project Settings → Service Accounts → Generate new private key)
4. Place the JSON file in `firebase_auth_project/` and update the path in `firebase_config.py`

### Step 5: Run the App

```bash
streamlit run app.py
```

The app will be available at `http://localhost:8501`

## Deployment on Hugging Face Spaces

The app supports Hugging Face Spaces deployment via the included `Dockerfile`.

Set the following secrets in your HF Space:
- `GROQ_API_KEY`
- `FIREBASE_KEY_JSON` (the full contents of your Firebase service account JSON)

## Usage Guide

### Getting Started

1. Open the app and use the sidebar to **Sign Up** or **Log In**
2. Once authenticated, your XP, level, and progress appear in the sidebar

### Taking a Quiz

1. Go to the **🎮 Quest** tab
2. Choose a topic from the predefined list or enter a custom one
3. Optionally upload a PDF to generate questions from your own content
4. Select difficulty and number of questions
5. Click **Start Quest** and answer each question
6. Use **💡 Need a Hint?** if you're stuck (costs 2 XP per hint)
7. Submit answers and continue through the quest

### Difficulty Levels

| Level | Name | XP per Correct Answer |
|---|---|---|
| Easy | Apprentice | 10 XP |
| Medium | Warrior | 15 XP |
| Hard | Master | 25 XP |

### Predefined Topics

- Network Security and Firewalls
- Digital Forensics and Incident Response
- Malware Analysis and Reverse Engineering
- Penetration Testing and Ethical Hacking
- Cryptography and Data Protection
- Web Application Security
- Mobile Device Security
- Cloud Security and Infrastructure
- Social Engineering and Phishing
- Threat Intelligence and Hunting

### Pets

Reach **200 XP** to unlock the pet collection. Navigate to the **🐾 Pet** tab to choose your animated companion.

### Daily Tasks

Check the **✅ Daily Tasks** tab each day for bonus XP challenges. Completing tasks on consecutive days builds your streak.

## File Structure

```
forensiqwiz/
├── app.py                      # Main Streamlit application
├── app_config.py               # HF Spaces deployment config
├── quiz_generator.py           # Groq API quiz generation
├── firebase_config.py          # Firebase initialization
├── firebase_data_manager.py    # Firestore data operations
├── data_manager.py             # Local JSON data manager (legacy)
├── pdf_processor.py            # PDF text extraction
├── style.py                    # Custom CSS styles
├── migrate_to_firebase.py      # JSON → Firebase migration script
├── setup_firebase.py           # Firebase setup helper
├── requirements.txt
├── Dockerfile
├── data/                       # Legacy JSON data files
├── pets/                       # Animated pet GIF files
└── firebase_auth_project/      # Firebase service account credentials
```

## Troubleshooting

**"GROQ_API_KEY not set" error**
- Ensure your `.env` file exists in the project root with the correct key
- Restart the app after adding the key

**Firebase connection errors**
- Verify your service account JSON path in `firebase_config.py`
- Ensure Firestore is enabled in your Firebase project
- Check that your service account has the necessary Firestore permissions

**PDF quiz generation fails**
- Ensure the PDF contains selectable/readable text (not scanned images)
- Try a smaller PDF if the document is very large

## Security Notes

- ⚠️ **Ethical Use Only**: This platform is for educational purposes
- 🔒 **Credentials**: Never commit your `.env` or Firebase service account JSON to version control
- 🛡️ **Passwords**: All passwords are hashed with bcrypt before storage

## Support & Contact

- **Email**: ForensIQally@outlook.com

---

**ForensIQwiz v1.0**
*Level up your cybersecurity knowledge, one quest at a time.*
