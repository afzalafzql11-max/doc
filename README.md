# DocuVault AI

A lightweight Streamlit document-management prototype designed for Render free-tier deployment.

## Features

- Sign up and login
- Upload PDF, DOCX, TXT and image documents
- Lightweight OCR/text extraction
- English translation attempt
- Automatic document type/name/date detection
- Validity and expiry tracking
- Website notifications for upcoming/expired documents
- Search bar
- Calendar view for validity dates
- 6-month "not opened" reminders
- Download original files
- Lightweight metadata knowledge graph
- SQLite local database
- No large local AI model

## Render deployment

Use a Python Web Service.

Build command:

```text
pip install -r requirements.txt
```

Start command:

```text
streamlit run app.py --server.port $PORT --server.address 0.0.0.0
```

Do not add a `PYTHON_VERSION=3.13.5` environment variable unless you specifically configure Render to use that Python version. The requirements are intentionally kept lightweight.

## Important Render free-tier note

The app uses local SQLite and local uploads. Render's free service filesystem is ephemeral, so files/database can be lost after service replacement/redeploy/restart. For a production DigiLocker-like system, use persistent external storage/database.

Image OCR depends on Tesseract being installed on the host. The Python package alone does not install the Tesseract system executable. PDF text extraction works for text-based PDFs. This prototype intentionally avoids heavyweight OCR/translation models to reduce memory usage.

## Security note

This is a final-year-project prototype, not a production secure document vault. Before real deployment, add encrypted object storage, secure password hashing such as Argon2/bcrypt, HTTPS-only sessions, CSRF protection, file scanning, authorization hardening, rate limits and persistent database/storage.
