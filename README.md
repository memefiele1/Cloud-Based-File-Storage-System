# ☁️ Cloud-Based File Storage System

The **Cloud-Based File Storage System** is a secure, lightweight web application built using **Flask**, **MySQL**, and the **Google Drive API**.  
It allows users to **upload**, **download**, and **share** files safely and efficiently through a personal dashboard interface.

Designed for clarity, modularity, and educational purposes, this project replicates the essential features of larger platforms (like Dropbox or Google Drive) while remaining fully open-source, customizable, and lightweight.

---

## 📋 Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [System Architecture](#system-architecture)
- [Folder Structure](#folder-structure)
- [Setup Instructions](#setup-instructions)
- [Usage Guide](#usage-guide)
- [API Endpoints](#api-endpoints)
- [Environment Variables](#environment-variables)
- [Contributors](#contributors)
- [License](#license)

---

## ✨ Features

- **User Authentication**: Secure registration, login, and session management via Flask-Login.
- **File Upload**: Upload and store various file formats (PDF, PNG, DOCX) up to 10MB.
- **File Download**: Users can view and download previously uploaded files securely.
- **Shareable Links**: Generate secure, time-limited shareable links via Google Drive integration.
- **Metadata Tracking**: All uploads are logged into a **MySQL** database, including file names, timestamps, user IDs, and Google Drive IDs.
- **Modular Codebase**: Clean separation of backend, frontend, and service logic for maintainability.

---

## 🛠️ Tech Stack

| Layer       | Technology                    |
|-------------|--------------------------------|
| Frontend    | HTML, CSS, Jinja2 Templates, Bootstrap |
| Backend     | Python (Flask Framework)       |
| Database    | MySQL + SQLAlchemy ORM         |
| Cloud Storage | Google Drive API (OAuth2)    |
| Auth        | Flask-Login for session management |
| Others      | Python Libraries: PyMySQL, dotenv |

---

## 🏗️ System Architecture

```text
+----------------+
|   Web Browser  |   ← (HTML, CSS, JS)
+-------+--------+
        |
        v
+----------------+
|  Flask Server  |   ← (Routing, Authentication, API Calls)
+-------+--------+
        |
        v
+----------------+      +----------------+
|  MySQL Database |     | Google Drive API|
| (User + Files)  |     | (File Storage)   |
+----------------+      +----------------+
```

---

## 📂 Folder Structure

```text
cloud-storage-system/
│
├── app/
│   ├── __init__.py
│   ├── config.py
│   ├── models.py
│   ├── services/
│   │   └── google_drive.py
│   └── files/
│       └── routes.py
│
├── tests/
│   └── test_api.py
│
├── templates/
│   ├── index.html
│   └── login.html
│
├── static/
│   ├── style.css
│   └── script.js
│
├── requirements.txt
├── .gitignore
├── .env.example
├── README.md
└── LICENSE
```

---

## ⚙️ Setup Instructions

1. **Clone the Repository**
   ```bash
   git clone https://github.com/memefiele1/Cloud-Based-File-Storage-System.git
   cd Cloud-Based-File-Storage-System
   ```

2. **Create a Virtual Environment**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # For Mac/Linux
   venv\Scripts\activate     # For Windows
   ```

3. **Install Dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set Up Environment Variables**
   - Copy `.env.example` to `.env`
   - Fill in your **MySQL credentials**, **Google OAuth2 Client ID/Secret**, and **Drive Folder ID**

5. **Initialize the Database**
   ```bash
   flask shell
   >>> from app import db
   >>> db.create_all()
   >>> exit()
   ```

6. **Run the App**
   ```bash
   flask run
   ```

7. **Access It**
   - Visit `http://localhost:5000/` in your browser 🚀

---

## 🖥️ Usage Guide

- **Sign Up** → Create a new user account.
- **Login** → Access your private dashboard.
- **Upload Files** → Upload PDFs, Word Docs, Images (up to 10MB).
- **Manage Files** → See a table of your files, download them, or generate share links.
- **Logout** → End your session securely.

All file metadata is automatically synced with the MySQL database.  
Uploaded files are securely stored in your designated **Google Drive** folder.

---

## 📡 API Endpoints

| Route                    | Method | Description                      |
|---------------------------|--------|----------------------------------|
| `/register`               | POST   | Register a new user              |
| `/login`                  | POST   | Authenticate user                |
| `/logout`                 | GET    | Log out user                     |
| `/upload`                 | POST   | Upload a new file                |
| `/files`                  | GET    | List uploaded files              |
| `/download/<file_id>`      | GET    | Download a file                  |
| `/share/<file_id>`         | GET    | Generate a shareable download link |
| `/shared/<token>`          | GET    | Download file via share token    |

---

## 🔐 Environment Variables (.env.example)

```env
# Flask Settings
FLASK_APP=run.py
FLASK_ENV=development
SECRET_KEY=your_flask_secret_key

# MySQL Database Settings
MYSQL_USER=your_mysql_username
MYSQL_PASSWORD=your_mysql_password
MYSQL_HOST=localhost
MYSQL_DATABASE=your_database_name

# Google OAuth2 Settings
GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret
GOOGLE_DRIVE_FOLDER_ID=your_google_drive_folder_id
```

---

## 👥 Contributors

| Name              | Role                  |
|-------------------|------------------------|
| Miracle Emefiele  | Frontend Developer, GitHub Management |
| Morewa Omolabi    | Backend Developer, API Integrations  |
| Gunn Madan        | Testing and QA Lead     |
| Ethan Munji       | Documentation and Reporting Lead |

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).

---

