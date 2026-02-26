# Sylvia Insurance — Vercel Deployment

## Files
```
sylvia-vercel/
├── index.html          ← The frontend UI
├── api/
│   └── authorize.js    ← Serverless proxy (keeps API key secure)
├── vercel.json         ← Vercel config
└── README.md
```

## How to Deploy (15 minutes)

### Step 1 — Create a Vercel account
Go to **vercel.com** and sign up. Choose "Continue with GitHub" to link your GitHub account.

### Step 2 — Push this folder to a new GitHub repo
In GitHub Desktop:
1. File → Add Local Repository → select this `sylvia-vercel` folder
2. It will say "not a git repo" — click **Create a Repository Here**
3. Name it `sylvia-vercel`, keep it **Private** this time (your proxy code will be here)
4. Commit all files with message "Initial Vercel deploy"
5. Click **Publish Repository**

### Step 3 — Import to Vercel
1. Go to **vercel.com/new**
2. Click **Import** next to your `sylvia-vercel` repo
3. Leave all settings as default — Vercel auto-detects everything
4. Click **Deploy**

### Step 4 — Add your API key as an Environment Variable
1. Once deployed, go to your project in Vercel dashboard
2. Click **Settings → Environment Variables**
3. Add a new variable:
   - **Name:** `ANTHROPIC_API_KEY`
   - **Value:** your `sk-ant-...` key
   - **Environment:** Production, Preview, Development (check all three)
4. Click **Save**

### Step 5 — Redeploy
Go to **Deployments** tab → click the three dots on your latest deployment → **Redeploy**. This picks up the new environment variable.

### Done!
Vercel gives you a URL like `https://sylvia-vercel.vercel.app` — works on any device, any network, no API key input needed.

## How it works
- Browser calls `/api/authorize` (your own server)
- Vercel serverless function adds the API key and forwards to Anthropic
- API key never touches the browser — it lives only in Vercel's secure environment
