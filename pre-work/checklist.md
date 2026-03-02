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

## 3. Install Claude Code CLI

Open Terminal (press `Cmd + Space`, type "Terminal", press Enter).

Paste this command and press Enter:

```
npm install -g @anthropic-ai/claude-code
```

Then verify it worked:

```
claude --version
```

You should see a version number. If you see an error, message [facilitator].

---

## 4. Install Node.js (required for Claude Code CLI above)

If step 3 gave you an error about `npm not found`, install Node.js first:

1. Go to: https://nodejs.org
2. Download the **LTS** version (the left button)
3. Run the installer
4. Restart Terminal, then retry step 3

---

## 5. Install GitHub CLI

In Terminal:

```
brew install gh
```

If `brew` is not found, install Homebrew first:

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Then retry `brew install gh`.

Verify:

```
gh --version
```

---

## 6. Create a GitHub account

Go to https://github.com and sign up if you don't have an account.
Remember your username and the email you used.

---

## 7. Authenticate GitHub CLI

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

## 8. Configure git identity

In Terminal (replace with your actual name and GitHub email):

```
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

---

## 9. Figma: prepare your design file

You'll need a Figma file with a simple plugin UI design. It should have:

- A frame named `Plugin UI` (392 × 200px)
- Inside: a title text ("Icon to Component"), a one-line description, and a button labeled "Create Component"

Keep it simple — this is just a reference for the workshop. Style it however you like.

**Enable Dev Mode** on the file:
1. Open the file in Figma
2. Click the grid icon in the top-right toolbar
3. Switch to Dev Mode

---

## Verify everything works

Run these in Terminal — each should return a version number, not an error:

```
node --version
npm --version
claude --version
gh --version
git --version
```

If all five work, you're ready. See you at the workshop.
