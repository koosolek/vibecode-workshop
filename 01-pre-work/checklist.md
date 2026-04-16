# Pre-Workshop Setup

Complete all of this before Session 1. It takes about 30–45 minutes.
If anything doesn't work, message [facilitator] — don't leave it for the day.

---

## 1. Install VSCode

Download and install from: https://code.visualstudio.com

Open it once to confirm it launches. That's it for now.

---

## 2. Install Claude Code extension for VSCode

1. Open VSCode
2. Click the Extensions icon in the left sidebar (looks like 4 squares)
3. Search: `Claude Code`
4. Install the one published by Anthropic
5. You'll see a Claude icon appear in the sidebar — that's it

---

## 3. Install Command Line Tools

> Skip this step if already installed. To check, open Terminal
> (press `Cmd + Space`, type "Terminal", press Enter) and run `xcode-select -p`.
> If you see a path like `/Library/Developer/CommandLineTools`, skip to step 4.

In Terminal, paste this and press Enter:

```
xcode-select --install
```

A popup will appear asking to install Command Line Tools — click **Install**, then agree to the license. This can take a few minutes.

---

## 4. Install Node.js

> Skip this step if you already have Node.js installed. To check, open Terminal
> (press `Cmd + Space`, type "Terminal", press Enter) and run `node --version`.
> If you see a version number, skip to step 5.

1. Go to: https://nodejs.org
2. Download the **LTS** version (the left button)
3. Run the installer
4. Open Terminal (or restart it if it was already open)
5. Verify it worked:

```
node --version
```

You should see a version number like `v22.x.x`.

---

## 5. Install Claude Code CLI

In Terminal, paste this command and press Enter:

```
sudo npm install -g @anthropic-ai/claude-code
```

You'll be asked for your Mac password — this is normal. Type it and press Enter.
The password won't show as you type — that's also normal, just type it blind.

Then verify it worked:

```
claude --version
```

You should see a version number. If you see an error, message [facilitator].

---

## 6. Install pnpm

In Terminal:

```
sudo npm install -g pnpm
```

Verify it worked:

```
pnpm --version
```

You should see a version number like `9.x.x`.

---

## 7. Install Homebrew

> Skip this step if already installed. To check, run `brew --version` in Terminal.
> If you see a version number, skip to step 8.

In Terminal, paste this and press Enter:

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Follow the prompts. You may be asked for your Mac password again.

Verify it worked:

```
brew --version
```

---

## 8. Install GitHub CLI

In Terminal:

```
brew install gh
```

Verify:

```
gh --version
```

---

## 9. Create a GitHub account

Go to https://github.com and sign up if you don't have an account.
Remember your username and the email you used.

---

## 10. Authenticate GitHub CLI

In Terminal:

```
gh auth login
```

- Choose `GitHub.com`
- Choose `HTTPS`
- Type `Y` when asked to authenticate with browser
- Follow the prompts in your browser

When it says "Logged in as [your username]" — you're done.

---

## 11. Configure git identity

In Terminal (replace with your actual name and GitHub email):

```
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

---

## Verify everything works

Run these in Terminal — each should return a version number, not an error:

```
node --version
npm --version
pnpm --version
claude --version
gh --version
git --version
```

If all six work, you're ready. See you at the workshop.
