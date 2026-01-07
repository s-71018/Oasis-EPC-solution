This repository contains the AL extension for **Oasis EPC Solutions**, developed for **Microsoft Dynamics 365 Business Central (Sandbox)** using **VS Code + GitHub pull request workflow**.

The project follows a **feature-branch + mandatory review** model.  
Direct changes to `main` are not allowed.

---

## Tech Stack

- Microsoft Dynamics 365 Business Central (Sandbox)
- AL Language (VS Code)
- GitHub (Pull Requests + CODEOWNERS)
- OAuth authentication (BC SaaS)

---

## Repository Workflow (**Important**)

- `main` → **Protected branch**
- Development happens on **feature branches** which will be made by developers each time
- All changes must go through a **Pull Request**
- PRs are merged **only after review approval**

---

## Developer Setup Guide

Follow these steps 

### Required Tools
Install the following:

Visual Studio Code

AL Language Extension (by Microsoft) in VS Code

Git

### Clone the Repository

bash

git clone https://github.com/s-71018/Oasis-EPC-solution.git

cd Oasis-EPC-solution

### Open Project in VS Code
bash

code .

Confirm branch:

bash

git branch

Output should show: * main

### Attach VS Code to Business Central (One-Time)
**IMPORTANT** Do this only once per machine. Once app.json exists, **do not run AL: Go! again**. Use Ctrl + F5 only.

In VS Code:

Ctrl + Shift + P (Command Palette)

Run:- AL: Go!

And make a temporary folder for AL Project

Select: Microsoft cloud sandbox

Sign in

Choose your Sandbox environment

This creates:
app.json
.vscode/launch.json 

In launch.json verify:-  "startupCompany": "Oasis EPC Solutions"

**Open** the repo again using :

bash

code .

**Copy** "app.json" and ".vscode/launch.json" files in the repo and delete the temporary folder

Download symbols : AL: Download symbols

### Create or verify `.gitignore` contains:

.alpackages/
.vscode/.alcache/
*.app

### Create a Feature Branch (Mandatory)
Never work on main.

bash
git checkout main
git pull
git checkout -b feature/<feature-name> 

### Develop & Test
Write AL code in VS Code

Publish to Sandbox: Ctrl + F5
Verify changes in Business Central → Oasis EPC Solutions Company

If publishing succeeds and the Oasis EPC Solutions company opens in Sandbox,
the setup is correct.

### Commit Rules
Before committing, ensure:

  .alpackages is NOT committed
  
  .app files are NOT committed

.gitignore already handles this.

### Commit:

bash
git add .
git commit -m "Meaningful commit message"
git push origin feature/<feature-name>

### Create Pull Request
Go to GitHub

Create Pull Request(PR):

Base: main

Compare: feature/<feature-name>

Reviewer is auto-assigned via CODEOWNERS

Wait for approval

## Review & Merge Policy
All PRs require review approval

Only approved PRs can be merged

Do not bypass review checks

Delete feature branch after merge

## Notes
Always sync with main before starting new work
