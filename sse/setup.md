# Development Environment Setup

This guide walks you through everything you need to install and configure before the first class.

## 1. VS Code

Download and install [Visual Studio Code](https://code.visualstudio.com/) for your operating system (Windows, macOS, or Linux).

After installing, open VS Code and verify it launches correctly.

### Recommended Extensions

Install these extensions from the VS Code Extensions panel (`Ctrl+Shift+X` / `Cmd+Shift+X`):

| Extension                  | Purpose                                     |
|----------------------------|---------------------------------------------|
| **Claude** (by Anthropic)  | AI coding agent integrated into VS Code     |
| **Python** (by Microsoft)  | Python language support, debugging, linting |
| **Jupyter** (by Microsoft) | Run and edit Jupyter notebooks in VS Code   |

To install an extension: open the Extensions panel, search by name, and click **Install**.

## 2. Python

You need Python 3.10 or newer.

**Check if Python is installed:**

```bash
python --version
```

If not installed or too old:
- **macOS**: `brew install python` (requires [Homebrew](https://brew.sh)) or download from [python.org](https://www.python.org/downloads/)
- **Windows**: Download from [python.org](https://www.python.org/downloads/). During installation, **check "Add Python to PATH"**.
- **Linux**: `sudo apt install python3 python3-pip` (Ubuntu/Debian) or use your package manager

**Verify pip is available:**

```bash
pip --version
```

## 3. Terminal Access

You need access to a terminal (command line) for this course.

- **macOS**: Terminal.app (built-in) or iTerm2
- **Windows**: Use one of these options:
  - **Git Bash** (installed with Git, see below) — recommended
  - **Windows Terminal** from the Microsoft Store
  - **WSL** (Windows Subsystem for Linux) for a full Linux environment
- **Linux**: Your default terminal application

**VS Code has a built-in terminal.** Open it with `` Ctrl+` `` (backtick). This is the terminal you will use most often in this course.

## 4. Git

Git is required for version control throughout the course.

**Check if Git is installed:**

```bash
git --version
```

If not installed:
- **macOS**: `xcode-select --install` (installs Git with Xcode tools) or `brew install git`
- **Windows**: Download from [git-scm.com](https://git-scm.com/download/win). This also installs **Git Bash**.
- **Linux**: `sudo apt install git` (Ubuntu/Debian)

**Configure Git with your identity:**

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

## 5. GitHub Account

Create a free account at [github.com](https://github.com) if you don't have one.

**Apply for the GitHub Student Developer Pack** at [education.github.com/pack](https://education.github.com/pack) — this gives you free access to GitHub Copilot, Codespaces, and other tools.

**Install the GitHub CLI** (optional but useful):

```bash
# macOS
brew install gh

# Windows (with winget)
winget install GitHub.cli

# Linux
sudo apt install gh
```

Then authenticate: `gh auth login`

## 6. Claude Code (Terminal)

Claude Code is the AI coding agent we will use extensively in this course. It runs in your terminal and can read/write files, run commands, and help you build software.

**Install Node.js first** (required for Claude Code):

```bash
# Check if Node.js is installed
node --version
```

If not installed:
- **macOS**: `brew install node`
- **Windows**: Download from [nodejs.org](https://nodejs.org/) (LTS version)
- **Linux**: `sudo apt install nodejs npm`

**Install Claude Code:**

```bash
npm install -g @anthropic-ai/claude-code
```

**Authenticate:**

```bash
claude
```

This will open a browser window to log in. You need a Claude account — sign up at [claude.ai](https://claude.ai) if you don't have one. A free tier is available; Pro is recommended for heavier usage.

**Verify it works:**

```bash
# Start Claude Code in any directory
claude

# You should see a prompt. Type:
> What directory am I in?

# Claude should respond with your current directory.
# Type /exit to quit.
```

## 7. Claude Extension for VS Code

The Claude extension lets you use Claude directly inside VS Code.

1. Open VS Code
2. Go to Extensions (`Ctrl+Shift+X` / `Cmd+Shift+X`)
3. Search for **"Claude"** by Anthropic
4. Click **Install**
5. Sign in with your Claude account when prompted

Once installed, you can open the Claude panel from the sidebar and chat with Claude while you work.

## Verification Checklist

Run these commands in your terminal (or VS Code's built-in terminal) to verify everything is set up:

```bash
# Each command should print a version number or path
python --version        # Python 3.10+
git --version           # Git 2.x+
node --version          # Node.js 18+
claude --version        # Claude Code
code --version          # VS Code (may need to add to PATH on macOS)
```

If any command fails, revisit the corresponding section above.

## Getting the Course Materials

### Option A: Clone from VS Code (Recommended)

1. Open VS Code
2. Press `Ctrl+Shift+P` (or `Cmd+Shift+P` on macOS) to open the Command Palette
3. Type **"Git: Clone"** and select it
4. Paste this URL: `https://github.com/jkitchin/s26-06643.git`
5. Choose a location to save the repository (e.g., your home directory or a `courses` folder)
6. When prompted, click **Open** to open the cloned repository in VS Code

### Option B: Clone from the Terminal

```bash
git clone https://github.com/jkitchin/s26-06643.git
cd s26-06643/sse
code .
```

### Option C: GitHub Codespaces (No Local Setup)

If you prefer a cloud-based environment or are having trouble with local installation, you can use GitHub Codespaces:

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/jkitchin/s26-06643)

This gives you a full VS Code environment in your browser with everything pre-configured. The free tier provides 60 hours/month (more with GitHub Education).

### After Cloning

Open a terminal in VS Code (`` Ctrl+` ``) and set up your working branch:

```bash
# Install notebook merge tool
pip install nbdime
nbdime config-git --enable --global

# Create your working branch (keeps main clean for updates)
git checkout -b my-work
```

### Getting Course Updates

When the instructor announces updates:

```bash
git checkout main
git pull origin main
git checkout my-work
git merge main
```

## Troubleshooting

**"python" not found on Windows**: Make sure you checked "Add Python to PATH" during installation. Alternatively, try `python3` or `py` instead.

**"code" command not found on macOS**: Open VS Code, press `Cmd+Shift+P`, type "shell command", and select **"Install 'code' command in PATH"**.

**Claude Code authentication fails**: Make sure you have a Claude account at [claude.ai](https://claude.ai). Try `claude logout` then `claude` again.

**Git push asks for password**: Set up SSH keys or a personal access token. Run `gh auth login` if you installed the GitHub CLI.

**Still stuck?** Ask your AI agent: describe the error message and your operating system. AI is great at debugging setup issues.
