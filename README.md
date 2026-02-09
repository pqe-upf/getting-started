# Getting Started with PQE

This short guide covers the basics you need to join the PQE GitHub community and start contributing.

---

## 1. Membership

PQE is open to students taking or planning to take the Advanced Quantitative Methods Program (MQA) at UPF.

**Not yet a member?** [Request membership here](https://github.com/pqe-upf/getting-started/issues/new?template=membership_application.yml).

---

## 2. GitHub Profile

Your GitHub profile is your technical identity. I recommend taking five minutes to set it up properly.

### Essential Setup

1. **Profile photo** — Use a clear headshot. 

2. **Name** — Your full name.

3. **Email** — Email address where you wish to be contacted. 

4. **Bio** — Brief description of who you are, where you study, your interests.

5. **Location** — Barcelona, Spain (or your actual location).

6. **Social accounts** — I recommend linking your LinkedIn profile, and any other you want to share.

7. **Organizations** — PQE once you're a member (automatic).

### Profile README (Very optional)

You can create a repository named exactly after your username (e.g., `username/username`) with a `README.md`. This appears on your profile page:

```markdown
## About Me

Student at Universitat Pompeu Fabra. 

**Interests:** Derivatives, machine learning, tennis, olive oil, ...

**Currently working on:** [Brief description]

**Contact:** [email or LinkedIn]
```

### Repository Hygiene

When you create repositories:
- Write a README explaining what the project does
- Add a `.gitignore` appropriate for your language
- Use clear, descriptive names (`volatility-forecasting` not `project1`)

---

## 3. How Git and GitHub Work

Git is version control. GitHub is where you host and collaborate on Git repositories.

### Core Concepts

| Concept | What It Means |
|---------|---------------|
| Repository | A project folder tracked by Git |
| Commit | A saved snapshot of changes |
| Branch | A parallel version of the code |
| Pull Request | A proposal to merge changes |
| Fork | Your personal copy of someone else's repository |
| Clone | Download a repository to your computer |

### Learning Resources

GitHub's own documentation is excellent. You can read these to gain familiarity:

1. **[Git Handbook](https://docs.github.com/en/get-started/using-git/about-git)** — Core concepts

2. **[Hello World Tutorial](https://docs.github.com/en/get-started/quickstart/hello-world)** — Create your first repository

3. **[GitHub Flow](https://docs.github.com/en/get-started/quickstart/github-flow)** — The branch > commit > PR > merge workflow

4. **[Forking Projects](https://docs.github.com/en/get-started/quickstart/fork-a-repo)** — How to contribute to others' code

5. **[About Pull Requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)** — The collaboration mechanism

### Quick Reference (Example)

```bash
# Clone a repository
git clone https://github.com/pqe-upf/repo-name.git

# Create a branch for your work
git checkout -b feature-name

# Stage and commit changes
git add .
git commit -m "Brief description of changes"

# Push to GitHub
git push origin feature-name

# Then open a Pull Request on GitHub
```

---

## 4. Development Environment

### Git Installation

**macOS:**
```bash
xcode-select --install
```

**Windows:**  
Download from [git-scm.com](https://git-scm.com/download/win). Use default settings.

**Linux:**
```bash
sudo apt install git
```

**Verify installation:**
```bash
git --version
```

### Git Configuration

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
git config --global init.defaultBranch main
```

Use the same email as your GitHub account.

### SSH Key (Recommended)

SSH keys let you push to GitHub without entering your password each time.

```bash
# Generate key
ssh-keygen -t ed25519 -C "your.email@example.com"

# Start SSH agent and add key
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

# Copy public key
cat ~/.ssh/id_ed25519.pub
```

Add the key to GitHub: **Settings > SSH and GPG keys > New SSH key**

Test it:
```bash
ssh -T git@github.com
```

### IDE (Integrated Development Environment)

I recommend **Visual Studio Code**, or **Cursor** for AI-assisted coding:

1. Download from [code.visualstudio.com](https://code.visualstudio.com/)

2. Install these extensions:
   - **Python**
   - **Pylance**
   - **GitLens**
   - **Jupyter**

### Python Environment

**Install Python+** from [python.org](https://www.python.org/downloads/) or via your package manager.

**Create virtual environments for each project:**
```bash
cd your-project
python -m venv .venv

# Activate (macOS/Linux)
source .venv/bin/activate

# Activate (Windows)
.venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

Always work in a virtual environment. Never install packages globally.

---

## 5. Engage with the Community

### Discussions

Questions, ideas, and conversations are encouraged to happen in [GitHub Discussions](https://github.com/orgs/pqe-upf/discussions).

- **Q&A**
- **Ideas** — Propose new projects, events, or improvements
- **General** — Everything else

Before posting, search to see if your question has been answered.

---

**Questions?** Open a thread in [Discussions](https://github.com/orgs/pqe-upf/discussions) or reach out to any organization member.
