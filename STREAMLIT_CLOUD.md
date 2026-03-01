# Deploy PlayBook on Streamlit Cloud

## 1. Create the app

1. Go to **[share.streamlit.io](https://share.streamlit.io)** and sign in with GitHub.
2. Click **"New app"**.
3. Fill in:
   - **Repository:** `mbarlo10-web/playbook`
   - **Branch:** `main`
   - **Main file path:** `app.py`
4. Under **"Advanced settings"** (if shown), set **App URL** to one of:
   - `playbook` → **playbook.streamlit.app**
   - `playbook-demo` → **playbook-demo.streamlit.app**
   - `playbook-asu` → **playbook-asu.streamlit.app**  
   (Use whatever is still available.)
5. Click **"Deploy!"**.

## 2. Add secrets (required for OpenAI and Stripe)

After the app is created, open it in the Streamlit Cloud dashboard and go to **Settings → Secrets**.

Paste TOML in this format (replace with your real values):

```toml
[openai]
api_key = "sk-your-openai-api-key"

[stripe]
payment_link = "https://buy.stripe.com/your-payment-link"
```

Or set environment variables in **Settings → General**:

- `OPENAI_API_KEY` = your OpenAI key  
- `PLAYBOOK_STRIPE_PAYMENT_LINK` = your Stripe payment link (optional if you use secrets)

Save; the app will redeploy with the new secrets.

## 3. Repo requirements (already in place)

- `requirements.txt` with `streamlit`, `openai`, `python-dotenv`, `requests`
- Main file: `app.py`
- Secrets read via `st.secrets` and env vars (no local `.streamlit/secrets.toml` needed on Cloud)

Your app URL will be something like **https://playbook.streamlit.app** (depending on the slug you chose).
