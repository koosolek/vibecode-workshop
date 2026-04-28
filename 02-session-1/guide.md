# Session 1 — Setup and Claude Code Basics
**Duration:** 2 hours

This session takes you from a fresh setup to your first real project, committed
to GitHub — with Claude Code (CC) doing most of the work. You'll learn the
basic interaction model and the few concepts you need to know to use CC well.

> **For facilitators:** Confirm everyone completed `01-pre-work/checklist.md`
> before the session. Have a GitHub repo ready as a demo, and VSCode open with
> screen share ready.

---

## 0:00–0:10 — Check that everything's installed

In Terminal (the Mac app), run:

```bash
claude --version
```

You should see a version number.

> **If something's wrong:**
> - `npm not found` → Node.js isn't installed (revisit pre-work step 4)
> - `claude not found` → the npm install didn't complete, or you need a new
>   Terminal window
> - `gh auth status` shows you're not logged in → run `gh auth login`

---

## 0:10–0:35 — VSCode tour

The goal here is to get comfortable with VSCode before using it for real work.

1. **Open a folder.** `File → Open Folder` → pick your Desktop for now. The
   left sidebar shows your files.

2. **The panels:**
   - **Left sidebar icons:** Explorer (files), Search, Source Control (git),
     Extensions
   - **Right panel:** comes to life with extensions

3. **Command Palette — the most important thing in VSCode.** Press
   `Cmd + Shift + P` and type anything. Try it now: type "theme" → "Color
   Theme" → pick one you like.

4. **Split view.** Drag a file tab to the right half of the editor. Useful
   when reading CC output while editing code.

5. **The Claude Code sidebar.** Click the Claude icon in the left sidebar —
   this is where you'll talk to CC. Don't start a chat yet, just see it's there.

> **Tip — the two-app setup:** From now on, you'll always have two apps open
> side by side: **VSCode** for chatting with CC and viewing files, and
> **Terminal** for running commands. VSCode is where you talk, Terminal is
> where you do.

Take a couple of minutes to click around and explore.

---

## 0:35–0:50 — Create ~/Code and connect GitHub

You'll keep all your coding projects in one folder: `~/Code`. In Terminal:

```bash
mkdir ~/Code
cd ~/Code
```

Now check that GitHub CLI is authenticated:

```bash
gh auth status
```

You should see your username. If not, run:

```bash
gh auth login
```

Pick `GitHub.com` → `HTTPS` → `Y` → follow the browser prompts.

Finally, set your git identity (if you didn't already in pre-work):

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

---

## 0:50–1:15 — Your first Claude Code chat

In VSCode: `File → Open Folder` → pick `~/Code`. Then click the Claude icon in
the left sidebar to open CC.

Type this question (don't paste — typing makes it stick better):

```
What is Claude Code and how is it different from using Claude in a browser?
```

Read the answer. The key points:
- CC is right here in your editor, inside your project
- It can read and write files on your machine
- It's not just chat — it's an agent that can take actions

Now ask:

```
What does "context window" mean and why does it matter?
```

> **Tip:** Think of CC's context window as its working memory for the
> conversation. It can only hold so much at once. That's why we'll use
> `CLAUDE.md` files (covered next) — to keep important instructions available
> without eating up that context.

---

## 1:15–1:40 — Concepts you need to know

A few core concepts will explain almost everything CC does. Skim this section
now — you'll come back to it.

### 1. Conversations (chat sessions)

- Each chat in the CC sidebar is a **session**.
- You can start new sessions or pick up old ones from the sidebar.
- In Terminal, you can also resume sessions: `claude --continue` (last session)
  or `claude --resume` (pick from a list).
- Sessions are stored in `~/.claude/projects/`.

> **Tip — chats are tied to the folder path.** CC links conversations to the
> exact folder location on your Mac. If you move or rename a project folder,
> CC won't find the old chats — it'll start fresh. Your code and git history
> are fine (see below), but the chat history stays linked to the original path.

> **Tip — chats are shared across all CC interfaces.** A chat started in the
> VSCode sidebar shows up in Terminal (`claude --resume`) and in the Claude
> desktop app. Pick whichever interface feels right in the moment.

### 2. Git vs GitHub — your project's real memory

**Git** is a tool that runs on your Mac. It tracks every change you make to
your project — like an unlimited undo history. All of that history lives inside
your project folder (in a hidden `.git` folder). It doesn't need the internet.
Move the folder, rename it, put it on a USB stick — `git log` still works.

**GitHub** is a website where you can upload a copy of your git project. It's
useful when you want to share code, back it up online, or collaborate. But
it's optional — if you're working alone on a quick prototype, you can just
use git locally and never push to GitHub. The project still has full history.

We'll use both in this workshop to practice the full workflow, but remember:
git is the durable record, GitHub is the optional sharing layer.

### 3. CLAUDE.md — Project memory

A markdown file that CC reads automatically at the start of every session. Use
it for: project conventions, tech stack, things CC should always know.

**CLAUDE.md works at multiple levels.** CC reads every `CLAUDE.md` it finds
from your home folder down to the project folder. This lets you layer
instructions:

| Level | Path | What goes here |
|-------|------|----------------|
| Root | `~/CLAUDE.md` | Machine-level preferences — your name, language, general style |
| Code folder | `~/Code/CLAUDE.md` | Rules for all coding projects — commit style, formatting |
| Project | `~/Code/my-project/CLAUDE.md` | Project-specific conventions and context |

CC merges them — root-level rules apply everywhere, project-level rules stack
on top.

**Try it:** in VSCode, create a new file called `CLAUDE.md` in `~/Code` with
this single line:

```
Always write commit messages in lowercase.
```

Save it. Then in the CC sidebar, start a new chat and ask:

```
What are your instructions for this project?
```

CC should mention the lowercase rule — even though the file is one level up.

### 4. Context files (@ mentions)

- Pull any file into context with `@filename` — e.g. `@README.md summarize this project`.
- Useful for sharing a design spec or pointing CC at a specific file to edit.
- In VSCode, CC also sees files you have open in the editor — so just opening
  a file is often enough, no `@` needed.

### 5. Slash commands

Type `/` in CC to see all available commands. Key ones to know:

- `/help` — see what's available
- `/mcp` — manage MCP connections (you'll use this in Session 2 for Figma)
- `/compact` — compress the conversation when context gets long
- `/clear` — start a fresh conversation

You don't have to memorize these — just know the `/` menu exists.

### The big picture

| Type | What it is | When to use |
|------|-----------|-------------|
| Session chat | The current conversation | Everything — it's the main loop |
| Git | Permanent project history | Every meaningful change — your durable record |
| CLAUDE.md | Persistent project instructions | Rules and conventions that never change |
| @ files | Pull a specific file into context | When CC needs to see or edit something |
| / commands | Built-in shortcuts | Quick actions without leaving the chat |

---

## 1:40–2:00 — Your first project, committed and pushed

Time to put it all together. You'll create a real project, commit it with git,
and push it to GitHub — and CC will do most of the work.

In Terminal, create the project folder:

```bash
cd ~/Code
mkdir my-first-project
```

In VSCode: `File → Open Folder` → navigate to `~/Code/my-first-project`. Open
the CC sidebar and type:

```
Help me set up this folder as a new project. Initialize git, create a README.md
and a CLAUDE.md, make a first commit, and create a GitHub repo for it.
```

CC will guide you through it. When it asks to run `gh repo create` — approve it.

> **What's happening here:**
> - CC writes the README and CLAUDE.md without you typing a single line of content
> - It runs `git init` for you — you could have typed that yourself, but you
>   don't have to
> - It writes a commit message for you
> - The files appear in the VSCode file explorer on the left as CC creates them

When it's done, open your GitHub profile in a browser. Your new repo should
be there.

> **This is the loop:** you describe what you want, CC does it, you review and
> approve. In Session 2 you'll connect CC to Figma and Jira, create a design,
> and build a prototype — same loop, bigger project.

