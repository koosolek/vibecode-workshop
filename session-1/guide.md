# Session 1 Facilitator Guide
**Duration:** 2 hours | **Group:** 3 people | **Room setup:** everyone on their own Mac

---

## Before they arrive

- [ ] Confirm everyone completed `pre-work/checklist.md`
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

### 2. CLAUDE.md — Project memory
- A markdown file in your project root
- CC reads it automatically at the start of every session
- Use it for: project conventions, tech stack, things CC should always know
- Demo: create a `CLAUDE.md` in `~/Code` with one line:
  ```
  Always write commit messages in lowercase.
  ```
  Start a new CC session, ask: "What are your instructions for this project?"
  CC should mention the lowercase rule.

### 3. Context files (@ mentions)
- You can pull any file into context with `@filename`
- Example: `@README.md summarize this project`
- Useful for: sharing a design spec, pointing CC at a specific file to edit

### Summarize the three:
| Type | What it is | When to use |
|------|-----------|-------------|
| Session chat | The current conversation | Everything — it's the main loop |
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

Hand them (or Slack): `between-sessions/solo-task.md`

Remind them: do it before Session 2. It's 10 minutes.
