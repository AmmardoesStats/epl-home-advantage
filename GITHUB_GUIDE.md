# How to Publish This Project on GitHub
### A complete guide for first-timers — no experience needed

---

## What you'll end up with
A public GitHub page at `https://github.com/AmmardoesStats/epl-home-advantage` that shows your notebook, README, and code — professional, searchable, and shareable with a single link.

---

## Step 1 — Create a GitHub account (if you haven't already)

1. Go to **[github.com](https://github.com)**
2. Click **Sign up** (top right)
3. Enter your email, create a password, choose a username: **AmmardoesStats**
4. Verify your email and log in

---

## Step 2 — Create a new repository

A repository (repo) is just a folder on GitHub for your project.

1. Once logged in, click the **+** icon (top right) → **New repository**
2. Fill in the form:
   - **Repository name:** `epl-home-advantage`
   - **Description:** `Econometric analysis of 9,380 EPL matches tracing the decline of home advantage (2000–2025)`
   - **Visibility:** ✅ Public
   - **Add a README file:** ❌ Leave unchecked (you already have one)
   - **Add .gitignore:** ❌ Leave unchecked (you already have one)
   - **License:** ❌ Leave unchecked (you already have one)
3. Click **Create repository**

You'll land on an empty repo page. Leave this tab open.

---

## Step 3 — Install Git on your computer

Git is the software that sends your files to GitHub.

**Windows:**
1. Go to [git-scm.com/download/win](https://git-scm.com/download/win)
2. Download and install (click Next through all the defaults)
3. Open **Git Bash** from your Start menu

**Mac:**
1. Open **Terminal** (search for it with Cmd+Space)
2. Type `git --version` and press Enter
3. If it's not installed, macOS will prompt you to install it automatically

---

## Step 4 — Tell Git who you are (one-time setup)

In Git Bash (Windows) or Terminal (Mac), type these two commands, replacing with your details:

```bash
git config --global user.name "Ammar Tyabji"
git config --global user.email "your-email@example.com"
```

Use the same email you signed up to GitHub with.

---

## Step 5 — Put your project files in one folder

Create a folder on your computer called `epl-home-advantage` and put these files inside it:

```
epl-home-advantage/
├── epl_home_advantage.ipynb    ← the notebook (downloaded from Claude)
├── README.md                   ← downloaded from Claude
├── requirements.txt            ← downloaded from Claude
├── LICENSE                     ← downloaded from Claude
└── .gitignore                  ← downloaded from Claude
```

**Do NOT put `epl_final.csv` in this folder** — CSV files are too large for GitHub and the `.gitignore` file will block it anyway.

---

## Step 6 — Upload your files to GitHub

In Git Bash or Terminal, navigate to your folder. For example, if your folder is on your Desktop:

```bash
cd Desktop/epl-home-advantage
```

Then run these commands **one by one** (copy and paste each line, press Enter after each):

```bash
git init
git add .
git commit -m "Initial commit: EPL home advantage analysis"
git branch -M main
git remote add origin https://github.com/AmmardoesStats/epl-home-advantage.git
git push -u origin main
```

When it asks for your username and password:
- **Username:** AmmardoesStats
- **Password:** Use a Personal Access Token (see note below)

> **Note on password:** GitHub no longer accepts your account password here. You need a Personal Access Token instead:
> 1. On GitHub, click your profile photo → **Settings**
> 2. Scroll down to **Developer settings** (bottom of left sidebar)
> 3. **Personal access tokens** → **Tokens (classic)** → **Generate new token (classic)**
> 4. Give it a name, set expiry to 90 days, tick the **repo** checkbox
> 5. Click **Generate token** — copy it immediately (you only see it once)
> 6. Paste this token where Git asks for your password

---

## Step 7 — Check it worked

Go to: **`https://github.com/AmmardoesStats/epl-home-advantage`**

You should see your README displayed, all your files listed, and the notebook file (`.ipynb`) — which GitHub will render as a readable document automatically.

---

## Step 8 — Make it look great (optional but recommended)

**Add a description and link on your repo page:**
1. On your repo page, click the ⚙️ gear icon next to "About" (right side)
2. Description: `Econometric analysis of 9,380 EPL matches tracing the decline of home advantage`
3. Website: paste your blog post URL
4. Topics (tags that help people find you): `python` `data-science` `football` `machine-learning` `econometrics` `premier-league` `jupyter-notebook`
5. Click **Save changes**

---

## What to share with people

Once it's live, you have one link to share everywhere:

```
https://github.com/AmmardoesStats/epl-home-advantage
```

Put this on your CV, LinkedIn, blog post, and anywhere you want people to see your work.

---

## If anything goes wrong

Common issues and fixes:

| Problem | Fix |
|---------|-----|
| `git: command not found` | Git isn't installed — redo Step 3 |
| `Permission denied` | Make sure you're using a Personal Access Token, not your password |
| `remote origin already exists` | Run `git remote remove origin` then redo the `git remote add` line |
| Files not showing on GitHub | Run `git status` — any red files need to be added with `git add .` again |

---

*Good luck — once it's up, it takes about 10 minutes and you have a professional portfolio project live forever.*
