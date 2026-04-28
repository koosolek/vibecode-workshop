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

## 3. Meet your Terminal

The rest of the steps use Terminal — Mac's built-in command-line app. You'll
see it referenced a lot in this workshop, so it's worth a 60-second tour.

Open Terminal: press `Cmd + Space`, type "Terminal", press Enter.

You'll see a prompt like this:

```
yourname@your-mac ~ %
```

That's:
- `yourname` — your Mac user
- `your-mac` — your computer's name
- `~` — the folder you're currently in (here it's your **home folder** — the
  one named with your username. In Finder you can open it from the sidebar
  or with `Cmd + Shift + H`)
- `%` — where you type your command

**How commands work:** type or paste a command after the `%`, then press Enter
to run it. The output appears below.

**Password prompts:** some commands (the ones starting with `sudo`) ask for
your Mac password. **The password won't appear as you type it — not even
asterisks.** That's normal. Just type it blind and press Enter.

> **Tip:** Whenever this checklist shows a code block like `claude --version`,
> just paste it into Terminal and press Enter.

---

## 4. Install Command Line Tools

> Skip this step if already installed. To check, run `xcode-select -p` in
> Terminal. If you see a path like `/Library/Developer/CommandLineTools`,
> skip to step 5.

In Terminal:

```
xcode-select --install
```

A popup will appear asking to install Command Line Tools — click **Install**,
then agree to the license. This can take a few minutes.

---

## 5. Install Node.js

> Skip this step if you already have Node.js installed. To check, run
> `node --version` in Terminal. If you see a version number, skip to step 6.

1. Go to https://nodejs.org/en/download
2. On the download page, set these dropdowns:
   - **Version:** Latest LTS Version
   - **Operating System:** macOS
   - **Architecture:** **ARM64** for Apple Silicon Macs (M1/M2/M3/M4 — most
     Macs from 2020 onward) or **x64** for older Intel Macs. Not sure?
     Click the Apple menu → **About This Mac**. The "Chip" or "Processor"
     line tells you.
   - **Installer:** Prebuilt Installer
3. Click the download button
4. Run the `.pkg` file that downloads
5. Open a fresh Terminal window and verify it worked:

```
node --version
```

You should see a version number like `v22.x.x`.

---

## 6. Install Claude Code CLI

You installed the VSCode extension in step 2, but it only works inside VSCode.
This step installs the standalone `claude` command so you can also use Claude
Code in any Terminal window. You need both.

In Terminal:

```
sudo npm install -g @anthropic-ai/claude-code
```

You'll be asked for your Mac password (silent typing — see step 3).

Verify it worked:

```
claude --version
```

You should see a version number. If you see an error, message [facilitator].

---

## 7. Log in to Claude

Now log in to your Claude account from the CLI. In Terminal:

```
claude
```

This starts Claude Code. The first time you run it, it asks you to log in.

1. Pick the option that uses your Anthropic account with subscription access
2. Pick **Continue with SSO** and use your Perforce email (`@perforce.com`)
3. A browser window opens — log in there
4. The browser shows a code or a URL — copy it back into Terminal and press Enter
5. Terminal shows "Logged in as ..." when it's done

Type `/exit` and press Enter to close CC for now.

> **Tip:** If the browser doesn't open or login fails, run `claude` again
> and retry. If you keep getting stuck, message [facilitator].

---

## 8. Install pnpm

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

## 9. Install Homebrew

> Skip this step if already installed. To check, run `brew --version` in Terminal.
> If you see a version number, skip to step 10.

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

## 10. Install GitHub CLI

In Terminal:

```
brew install gh
```

Verify:

```
gh --version
```

---

## 11. Create a GitHub account

Go to https://github.com and sign up if you don't have an account.
Remember your username and the email you used.

---

## 12. Authenticate GitHub CLI

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

## 13. Configure git identity

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
