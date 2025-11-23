# 🤖 RAG PDF Chatbot

A Streamlit app that lets you upload PDF files and chat with their content using OpenAI.

## 🧩 Features
- Login & Register system  
- Upload multiple PDFs  
- Ask questions from documents  
- Uses OpenAI API for answers  

* Login & Register system
* Upload multiple PDFs
* Ask questions from documents
* Stores all data in PostgreSQL
* Uses OpenAI API for answers

## 🗄️ Database Used (PostgreSQL + pgAdmin)

This project uses **PostgreSQL** as the main database to store:

* User login & registration details
* Uploaded PDF metadata (file name, path, timestamp)
* Chat history (user question + AI response)

**pgAdmin 4** is used as a **GUI tool** to:

* Create and manage the database
* View stored data (users, PDFs, chats)
* Run SQL queries easily

**How it works internally:**
The app connects to PostgreSQL using a connection string inside the backend.
Whenever a user uploads a PDF or sends a chat message, the data is saved to the database automatically.
pgAdmin allows easy viewing and management of this stored information.

**Example connection string:**

```python
postgresql://username:password@localhost:5432/yourdbname

This makes the app more reliable, professional, and scalable.

## ⚙️ How to Run
1. Clone the repo
**git clone https://github.com/
<[your-username](https://github.com/SHAIKRESHMA2004?tab=repositories)>/streamlit_app.git**

2. Go to the folder  
```cd streamlit_app
3. Create virtual environment  
```python -m venv venv
4. Activate it  
- Windows: `venv\Scripts\activate`  
- Mac/Linux: `source venv/bin/activate`
5. Install packages  
```pip install -r requirements.txt
6. Create `.env` file  
```OPENAI_API_KEY=your_api_key_here
7. Run the app  
```streamlit run app.py

1. **Clone the repo**

```
git clone https://github.com/<your-username>/streamlit_app.git
```
2. **Go to the folder**
3. **Create virtual environment**
```
python -m venv venv
```
4. **Activate it**
* Windows:
```
venv\Scripts\activate
```
* Mac/Linux:
```
source venv/bin/activate
```
5. **Install packages**
```
pip install -r requirements.txt
```
6. **Create `.env` file**
```
OPENAI_API_KEY=your_api_key_here
```
7. **Run the app**
```
streamlit run app.py
```
Great! Here are **three ready-to-paste sections** for your README:
1️⃣ **Architecture Diagram (simple + clean explanation)**
2️⃣ **Database Schema Diagram (table structure)**
3️⃣ **Screenshots Section Template**
Everything is already formatted in Markdown so you can add directly to your README.md.
# 📐 System Architecture
```mermaid
flowchart TD
    A[User] -->|Login / Upload PDF / Ask Question| B[Streamlit Frontend]
    B --> C[Backend Logic - Python]
    C --> D[PDF Processing - PyPDF2]
    C --> E[RAG Pipeline - OpenAI Embeddings & Chat Completion]
    D --> F[Vector Store in Memory / Cache]
    C --> G[(PostgreSQL Database)]
    G -->|Managed with| H[pgAdmin 4]
    E --> C
**Explanation**
* **Streamlit** handles UI (login, upload, chat).
* **PDFs** are processed using PyPDF2.
* Extracted text is sent to **OpenAI** for embeddings + answers.
* **PostgreSQL** stores users, PDF info, and chat history.
* **pgAdmin** is used only for database management.
# 🗄️ Database Schema (PostgreSQL)
Below is a simple and clean structure of how your database tables are organized.
```mermaid
erDiagram
    USERS {
        int id PK
        text username
        text email
        text password
        timestamp created_at
    }
    PDF_FILES {
        int id PK
        int user_id FK
        text file_name
        text file_path
        timestamp uploaded_at
    }
    CHAT_HISTORY {
        int id PK
        int user_id FK
        int pdf_id FK
        text question
        text answer
        timestamp asked_at
    }
    USERS ||--o{ PDF_FILES : uploads
    USERS ||--o{ CHAT_HISTORY : sends
    PDF_FILES ||--o{ CHAT_HISTORY : referenced_in
```

### ✔️ What each table stores

* **USERS** → Login & registration
* **PDF_FILES** → File name, path, upload time
* **CHAT_HISTORY** → Q&A for each document

## 👩‍💻 Built With
- Python  
- Streamlit  
- OpenAI API  
- PyPDF2  

* Python
* Streamlit
* PostgreSQL + pgAdmin
* OpenAI API
* PyPDF2
Made with ❤️ by **Shaik Reshma**

Footer
