# WhatsApp-Driven Google Drive Assistant (n8n workflow)

This project connects WhatsApp (via Twilio) to Google Drive using n8n and enables you to list, move, delete, and summarize files using simple WhatsApp messages.

## 🧩 Features
- LIST /folder → Lists files in folder
- DELETE /folder/file → Deletes file
- MOVE /from/file /to/ → Moves file
- SUMMARY /folder → Uses OpenAI to summarize documents

## 🛠 Prerequisites
1. Twilio Sandbox for WhatsApp
2. Google Drive API (OAuth2) credentials
3. OpenAI API key
4. Docker installed

## ⚙️ Setup Steps

### 1. Clone this repository

### 2. Add `.env` file (based on `.env.sample`)
Fill in all credentials: Twilio, Google, OpenAI.

### 3. Run n8n in Docker:
```bash
docker run -it --rm   -p 5678:5678   --env-file .env   -v ~/.n8n:/home/node/.n8n   n8nio/n8n
```

### 4. Import the workflow.json in n8n UI (http://localhost:5678)

### 5. Set up credentials inside n8n:
- Google OAuth2: Use your Google credentials
- OpenAI: API key
- Twilio: Create a webhook endpoint using HTTP Request Node

### 6. Start Testing via WhatsApp:
Send commands like:
- `LIST /TestFolder`
- `DELETE /TestFolder/file.pdf`
- `SUMMARY /TestFolder`

## 📦 Files
- `workflow.json` → Import into n8n
- `.env.sample` → Template for environment variables
- `README.md` → Setup documentation

## 🔐 Notes
- Safety is ensured via audit logs
- Deletion requires confirmation (optional)