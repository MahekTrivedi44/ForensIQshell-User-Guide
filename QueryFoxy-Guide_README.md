# Query Foxy

#### An AI-Powered Chat and Data Management Tool

---

### 🚀 Introduction

Query Foxy is a cute and clever, full-featured, AI-powered chatbot application designed to help users manage their conversations. It features a secure user authentication system, a conversational interface, and powerful data management capabilities, including the ability to store chat history and export conversations into summary documents or flashcards.

### ✨ Key Features

* **User Authentication**: Secure user registration and login system with password hashing powered by `bcrypt`.
* **AI-Powered Chatbot**: Leverages the powerful Groq API to provide real-time, intelligent responses to user queries.
* **Persistent Conversations**: All chat messages and conversations are stored in a local SQLite database, allowing users to revisit and continue their chats.
* **Content Generation & Export**: Generate and export chat summaries and flashcards in PDF format (`.pdf`) and HTML as well for easy sharing and offline use.
* **Intuitive UI**: A clean, single-page web interface built with Gradio and styled with custom CSS for a friendly user experience.

### ⚙️ Technologies Used

* **Backend**: Python, FastAPI
* **Frontend**: Gradio, Custom CSS
* **AI API**: Groq API
* **Authentication**: `bcrypt`
* **Database**: SQLite
* **Data Export**: `fpdf`

### 📦 Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

#### Prerequisites

-   Python 3.8 or higher
-   `pip` (Python package installer)
-   Git

#### Installation

1.  **Clone the repository**:
    ```bash
    git clone [https://github.com/your-username/query-Foxy.git](https://github.com/your-username/query-Foxy.git)
    cd query-Foxy
    ```

2.  **Create a virtual environment** (recommended):
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3.  **Install dependencies**:
    ```bash
    pip install -r requirements.txt
    ```

4.  **Set up the database**:
    The database will be automatically created and initialized with the schema when you run the application for the first time, thanks to the `init_db()` function.

5.  **Configure your API key**:
    Set your Groq API key as an environment variable. **DO NOT hardcode your key in the `chatbot.py` file.**
    * **On macOS/Linux:**
        ```bash
        export GROQ_API_KEY="gsk_YOUR_API_KEY_HERE"
        ```
    * **On Windows (Command Prompt):**
        ```bash
        set GROQ_API_KEY="gsk_YOUR_API_KEY_HERE"
        ```

#### Running the Application

This application runs as a single process, serving both the FastAPI backend and the Gradio frontend.

1.  **Open a terminal windows** in the project's root directory.

2.  **In app.py**, uncomment the main function for local deployment:

3.  **Start the app** by running:
    ```bash
    uvicorn appxx:fastapi_app --reload --host 127.0.0.1 --port 8000
    ```

Your application should now be running. Open your web browser and navigate to the address provided by Gradio, typically `http://127.0.0.1:7860/gradio`.

### 🦊 How to Use Query Foxy

#### 1. Create an Account
- On the app's landing page, go to the **Sign Up** tab.
- Enter a username and password, then click **Sign Up**.
- Once registered, switch to the **Login** tab.

#### 2. Log In
- Enter your credentials and click **Log In**.
- Check **Remember Me** if you want your session to persist across browser refreshes.
- After a successful login, you'll be taken to the main chat interface.

#### 3. Chat with the Bot
- Type your message in the input box at the bottom and press **Enter** or click **Send**.
- The AI will respond in real time. Your conversation is automatically saved.

#### 4. Manage Conversations
- Click **New Conversation** to start a fresh chat thread.
- Your past conversations appear in the sidebar — click any of them to reload and continue that chat.

#### 5. Generate a Summary
- While in a conversation, click **Generate Summary**.
- Query Foxy will produce a concise summary of the current chat.
- Download it as a **PDF** or **HTML** file using the export button that appears.

#### 6. Generate Flashcards
- Click **Generate Flashcards** to turn the current conversation into study-ready flashcards.
- Choose your preferred format (**PDF** or **HTML**) before generating.
- The file will be available for download once ready.

#### 7. Log Out
- Click the **Log Out** button at any time to end your session securely.

---

### 📂 Project Structure
```bash
├── app.py                   # Main backend app (FastAPI or Flask)
├── auth.py                  # User authentication logic
├── chatbot.py               # Chatbot Groq integration
├── db.py                    # SQLite and DB helpers
├── requirements.txt         # All Python dependencies
├── DejaVuSans-Bold.tff      # Bold font for PDF generation
├── DejaVuSans.tff           # Regular font for PDF generation
├── schema.sql               # SQL schema for users/conversations
├── style.css                # Custom Gradio styling
├── Dockerfile               # For deployment
├── assets/                  # ✅ For main UI images
│   ├── logo.png             # Logo (header, etc.)
│   └── about.png            # About/branding image
├── extras/                  
│   ├── Dockerfile           # For Gradio+Flask app to expose 2 ports
│   ├── supervisord.conf     # Gradio+Flask app to expose 2 ports
│   └── FastAPI_Backend.py   
│   └── Gradio_Frontend.py   # Gradio+Flask app
│   └── Flask_Backend      

```
**Note:** The python files chatbot.py, auth.py, db.py have some code commented out. That is to be used for Flask+Gradio application.
