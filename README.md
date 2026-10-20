# SkillBot — Flask + HTML (Vercel-ready)

This project includes the SkillBot interview-preparation knowledge base and a simple HTML chat interface.

## Project files

- `app.py` — Flask app, knowledge base, chatbot matching logic, and API endpoints.
- `templates/index.html` — HTML/CSS/JavaScript chat interface.
- `requirements.txt` — Python dependencies.
- `.python-version` — Python version for Vercel.
- `.gitignore` — excludes local environment and secret files.

## Deploy to Vercel through GitHub

1. Extract this ZIP.
2. Put the files and folders inside the repository root (the folder that contains `app.py`).
3. Commit and push to GitHub.
4. In Vercel, import the GitHub repository or open your existing project and ensure **Root Directory** points to the folder containing `app.py`.
5. Use the default automatic framework detection. Do not add a custom build command or old `@vercel/python` routing config unless Vercel logs specifically require it.
6. Deploy/redeploy.

Vercel detects the top-level Flask variable named `app`. No `vercel.json` is required for this standard Flask setup.

## Test after deployment

Replace `Skillbot` with your Vercel deployment name:

- `https://Skillbot.vercel.app/` — HTML interface
- `https://Skillbot.vercel.app/api/health` — API health check
- `https://Skillbot.vercel.app/api/categories` — category list
- `https://Skillbot.vercel.app/api/random-question` — random interview question

To test chat from a terminal:

```bash
curl -X POST "https://Skillbot.vercel.app/api/chat" ^
  -H "Content-Type: application/json" ^
  -d "{\"message\":\"TCS interview questions\"}"
```

On Windows PowerShell, `curl` may be an alias. You can use `curl.exe` or test through the website's chat interface.

## Run locally

```bash
python -m venv .venv
```

Windows:
```bat
.venv\Scripts\activate
pip install -r requirements.txt
python app.py
```

Open `http://127.0.0.1:5000`.

## Important notes

- The frontend calls `/api/chat` on the same domain, so it does not need CORS for this deployment.
- Do not add a `debug=True` setting to production.
- If the API still fails, inspect Vercel's runtime logs and check the HTTP status from `/api/health`.
- This chatbot uses the built-in knowledge base; it does not call an external AI model or require API keys.
