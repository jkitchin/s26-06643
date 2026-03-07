# Creating Scientific Software with AI Coding Agents

Welcome to 06-643: Creating Scientific Software with AI Coding Agents.

## Course Overview

Software development has been transformed by AI coding agents like Claude Code, GitHub Copilot, and Cursor. This course teaches you to leverage these tools effectively while building a strong foundation in software engineering fundamentals.

You will learn to:
- Collaborate effectively with AI coding agents
- Build, test, and distribute Python packages
- Apply code quality practices and CI/CD pipelines
- Critically evaluate AI-generated code
- Configure and extend AI capabilities with custom tools

## Philosophy

**The modern developer workflow is collaborative with AI.** You must still understand *what* you're building and *why*, but *how* you implement it increasingly involves AI assistance.

This course emphasizes:
1. **Concept-first**: Understand the fundamentals before automating
2. **AI as pair programmer**: Every module includes AI-assisted exercises
3. **Critical evaluation**: Always review and validate AI output
4. **Meta-learning**: Reflect on when AI helps vs. when it hinders

## Prerequisites

- Basic Python programming experience
- Willingness to experiment with new tools
- A computer with internet access

## Getting Started

### 1. Set Up Your Environment

Follow the {doc}`setup` guide to install everything you need:
- VS Code with the Claude and Python extensions
- Python 3.10+, Git, and a terminal
- Claude Code in the terminal
- A GitHub account

### 2. Get the Course Materials

**Option A: One-Click Clone (Recommended)**

Click this link to clone the course repository directly in VS Code:

[Open in VS Code](vscode://vscode.git/clone?url=https://github.com/jkitchin/s26-06643.git)

**Option B: Clone from the Terminal**

```bash
git clone https://github.com/jkitchin/s26-06643.git
cd s26-06643/sse
code .
```

**Option C: GitHub Codespaces (No Local Setup Needed)**

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/jkitchin/s26-06643)

### 3. Create Your Working Branch

After cloning, open a terminal in VS Code (`` Ctrl+` ``) and run:

```bash
# Install notebook merge tool
pip install nbdime
nbdime config-git --enable --global

# Create your working branch (keeps main clean for updates)
git checkout -b my-work
```

### 4. Getting Course Updates

When the instructor announces updates:

```bash
git checkout main
git pull origin main
git checkout my-work
git merge main
```

### 5. Start Learning

1. Review the {doc}`syllabus`
2. Complete Module 00 exercises
3. Try `/trivia` to test your knowledge as you learn!

## Interactive Learning

This course includes an interactive learning system to help reinforce concepts:

### Software Forge Honors
Earn badges and ranks as you progress:
- **5 Badges**: Toolsmith, Packager, Tester, Collaborator, Documenter
- **4 Ranks**: Code Apprentice → Software Crafter → Software Engineer → Master Craftsperson

See [Software Forge Honors](software-forge-honors/README.md) for details.

### Games & Activities
- **Trivia** (`/trivia`): Test your knowledge with character-hosted questions
- **Adventure** (`/adventure`): "The Software Forge: Crisis Mode" - solve real coding crises
- **Flashcards** (`/flashcards`): Spaced repetition for commands and concepts
- **Puzzles** (`/puzzle`): Git graphs, bug hunts, code completion challenges
- **Scavenger Hunts** (`/hunt`): Explore documentation and open source projects

### Course Characters
Meet your guides including Gina Git, Tessa Test, Doc Douglas, and more! See [characters.md](characters.md).

### Quick Reference
The [reference sheet](reference-sheet.md) provides concise summaries of terminal commands, git, testing, and more.
