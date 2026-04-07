# Session 1 Facilitator Guide
**Duration:** 2 hours | **Group:** 3 people | **Room setup:** everyone on their own Mac

---

## Before they arrive

- [ ] Confirm everyone completed `01-pre-work/checklist.md`
- [ ] Have a GitHub repo ready to use as a demo (your own is fine)
- [ ] Have VSCode open on your machine, screen share ready

---

## 0:00–0:10 — Check-in (10 min)

Go around. Ask each person:
> "Run `claude --version` in Terminal. What do you see?"

If anyone has a broken setup — fix it now, don't wait. The other two can watch.
Common issues:
- `npm not found` → Node.js not installed
- `claude not found` → npm install didn't complete, or new shell session needed
- `gh auth` not done → run `gh auth login` together

---

## 0:10–0:35 — VSCode Tour (25 min)

**Goal:** Everyone comfortable navigating VSCode without hesitation.

Walk through, have them follow along on their machines:

1. **Open a folder**
   - `File → Open Folder` → navigate to Desktop for now
   - Point out: left sidebar = file explorer

2. **The panels**
   - Left sidebar icons: Explorer, Search, Source Control (git), Extensions
   - Bottom panel: Terminal (open with `` Ctrl+` ``)
   - Right panel: comes to life with extensions

3. **Command Palette** — the most important thing in VSCode
   - `Cmd + Shift + P` → type anything
   - Demo: type "terminal" → "Create New Terminal"
   - Demo: type "theme" → "Color Theme" → let them pick one

4. **Split view**
   - Drag a file tab to the right half of the editor
   - Useful when reading CC output while editing code

5. **The Claude Code sidebar**
   - Click the Claude icon in the left sidebar
   - Show it, but don't start a chat yet

**Pause:** Any questions about VSCode? Let them explore for 2 minutes.

---

## 0:35–0:50 — Create ~/Code and Connect GitHub (15 min)

**Goal:** Project home folder exists, GitHub is authenticated.

In VSCode terminal, everyone runs:

```bash
mkdir ~/Code
cd ~/Code
```

Verify GitHub CLI auth:

```bash
gh auth status
```

Should show their username. If not:

```bash
gh auth login
```

Walk them through: GitHub.com → HTTPS → Y → follow browser.

Then configure git identity if not done in pre-work:

```bash
git config --global user.name "Their Name"
git config --global user.email "their@email.com"
```

---

## 0:50–1:15 — First Claude Code Run (25 min)

**Goal:** Everyone has talked to CC, understands the basic interaction model.

In terminal:

```bash
cd ~/Code
claude
```

CC starts. Ask them to type (not paste — makes it more hands-on):

```
What is Claude Code and how is it different from using Claude in a browser?
```

Read the answer together. Point out:
- CC is in their terminal, in their project
- It can read and write files on their machine
- It's not just chat — it's an agent

Now ask them to type:

```
What does "context window" mean and why does it matter?
```

After the answer, explain in your own words:
> "Think of CC's context window as its working memory for the conversation.
> It can only hold so much at once. This is why we'll use CLAUDE.md — to keep
> important instructions available without eating context."

Type `/exit` or `Ctrl+C` to quit CC.

---

## 1:15–1:40 — CC Concepts (25 min)

**Goal:** They understand the 3 types of memory/context in CC.

Open a browser, navigate to Claude Code docs or explain verbally with examples:

### 1. Conversations (chat sessions)
- Each `claude` run is a session
- Resume a previous session: `claude --continue` (last session) or `claude --resume` (pick one)
- Sessions are stored in `~/.claude/projects/`
- Demo: quit CC, run `claude --continue` — it picks up where you left off

**Chats are tied to the folder path.** CC links conversations to the exact folder
location on your Mac. If you move or rename a project folder, CC won't find
the old chats — it'll start fresh. Your code and git history are fine (see below),
but the chat history stays linked to the original path.

**You can continue chats across tools.** A chat started in the VSCode sidebar
can be resumed in Terminal with `claude --resume`, and vice versa. The Claude
desktop app can also continue these same chats. They all share the same history
— pick whichever interface feels right in the moment.

### 2. Git — your project's real memory

While CC chats can break if you move a folder, git doesn't care where the folder
lives. Your entire project history — every commit, every change — travels with
the folder. Move it, rename it, put it on a USB stick — `git log` still works.
GitHub is just a remote copy. This is why we commit often: git is the durable
record, CC chats are the working conversation.

### 3. CLAUDE.md — Project memory
- A markdown file that CC reads automatically at the start of every session
- Use it for: project conventions, tech stack, things CC should always know

**CLAUDE.md works at multiple levels.** CC reads every CLAUDE.md it finds
from your home folder down to the project folder. This lets you layer instructions:

| Level | Path | What goes here |
|-------|------|----------------|
| Root | `~/CLAUDE.md` | Machine-level preferences — your name, language, general style |
| Code folder | `~/Code/CLAUDE.md` | Rules for all coding projects — commit style, formatting |
| Project | `~/Code/my-project/CLAUDE.md` | Project-specific conventions and context |

CC merges them — root-level rules apply everywhere, project-level rules add on top.

- Demo: create a `CLAUDE.md` in `~/Code` with one line:
  ```
  Always write commit messages in lowercase.
  ```
  Start a new CC session in `~/Code/my-first-project`, ask:
  "What are your instructions for this project?"
  CC should mention the lowercase rule — even though the file is one level up.

### 4. Context files (@ mentions)
- You can pull any file into context with `@filename`
- Example: `@README.md summarize this project`
- Useful for: sharing a design spec, pointing CC at a specific file to edit

### Summarize:
| Type | What it is | When to use |
|------|-----------|-------------|
| Session chat | The current conversation | Everything — it's the main loop |
| Git | Permanent project history | Every meaningful change — your durable record |
| CLAUDE.md | Persistent project instructions | Rules and conventions that never change |
| @ files | Pull a specific file into context | When CC needs to see or edit something |

---

## 1:40–2:00 — Git Setup with CC (20 min)

**Goal:** First real project, first commit, pushed to GitHub.

Everyone runs in terminal:

```bash
cd ~/Code
mkdir my-first-project
cd my-first-project
claude
```

Now they instruct CC (have them type it themselves):

```
Help me set up this folder as a new project. Initialize git, create a README.md
and a CLAUDE.md, make a first commit, and create a GitHub repo for it.
```

CC will guide them through it. Let it. Your job is to narrate what CC is doing:
- "See how it's writing the README? You didn't write a single line."
- "Now it's running `git init` — you could have typed that, but you didn't have to."
- "Watch the commit message — CC writes it for you."

If CC asks to run `gh repo create` — approve it.

At the end, have everyone open their GitHub profile in a browser and show their new repo.

**Close:**
> "This is the loop. You describe what you want, CC does it, you review and approve.
> In Session 2 we'll use this same loop to build a Figma plugin from a design."

---

## Send before they leave

Hand them (or Slack):
- `03-between-sessions/solo-task.md` — 10-minute CC + git task
- `03-between-sessions/session-2-setup.md` — Figma design prep + MCP setup (15–20 min)

Remind them: do both before Session 2.
