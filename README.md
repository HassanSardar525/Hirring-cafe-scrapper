# Hiring Cafe Automate Scraper (2026 Engine)

A hardened, automated Python job scraper built specifically for **Hiring Cafe**. It bypasses rigid Next.js backend schema rotations and Cloudflare Turnstile challenges using a real-world synchronized desktop signature. It extracts listings seamlessly and appends them cleanly into an Excel tracker grid.

## Core Features

- **Bypass-Ready Architecture:** Emulates a 2026 Chrome footprint to bypass deep TLS inspection checks.
- **Smart Filter Matrix:** Isolates remote-only roles, targets rapid-fill applications (Greenhouse, Ashby, Lever), and skips account-creation boards like Workday or Taleo.
- **Persistent Tracker Memory:** Automatically checks existing Excel spreadsheet indices and appends datasets cleanly with spacing rules.

---

## 1. Prerequisites & Local Environment Setup

Make sure you have Python installed on your machine. Open your project terminal directory and execute the following deployment chain:

```bash
# 1. Clone the repository locally
git clone <your-repository-url>
cd HirringCafeScrapper

# 2. Spin up a clean virtual sandbox environment
python -m venv .venv

# 3. Activate the virtual environment

# On Windows (Command Prompt / PowerShell)
.venv\Scripts\activate

# On Mac / Linux
source .venv/bin/activate

# 4. Install production dependencies
pip install -r requirements.txt
```

---

## 2. Setting Up Your Security Clearance Token

Because Hiring Cafe is heavily protected by Cloudflare walls, the script needs an active browser token from your manual session to run.

1. Open **Google Chrome** and log in to `https://hiring.cafe`.
2. Press **F12** (or right-click → **Inspect**) to open DevTools.
3. Open the **Application** tab.
4. Expand **Cookies** from the left sidebar and select `https://hiring.cafe`.
5. Locate the key named **cf_clearance**.
6. Copy its value.
7. Open `scrapper.py` and paste the value into the cookie variable near the bottom of the file:

```python
MY_CF_COOKIE = "PASTE_YOUR_COPIED_CF_CLEARANCE_STRING_HERE"
```

> **Note:** Cloudflare clearance tokens expire periodically. If the scraper begins returning **403 Forbidden** responses, refresh the Hiring Cafe website, obtain a new `cf_clearance` value, and replace the old token.

---

## 3. Running the Engine

Before starting the scraper, ensure that the output spreadsheet (`Master_Job_Tracker.xlsx`) is **completely closed**.

Run:

```bash
python scrapper.py
```

The runtime manager will:

- Process your configured search stack (e.g., Python, React, JavaScript).
- Identify quick-apply platforms such as Greenhouse, Ashby, and Lever.
- Exclude lengthy application workflows.
- Write clean, structured results directly into your Excel tracker.

---

## Output

Successful runs append job listings into:

```text
Master_Job_Tracker.xlsx
```

with duplicate-safe tracking and structured row insertion logic.
