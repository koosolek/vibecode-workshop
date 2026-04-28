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
claude
```

CC should start without asking you to log in (you logged in during pre-work).
You'll see a prompt where you can type. Don't type anything yet — just
confirm CC opened. Press `Ctrl + C` or type `/exit` to close it.

> **If something's wrong:**
> - CC asks you to log in → revisit pre-work step 7
> - `claude: command not found` → revisit pre-work step 6 (the npm install)
>   or open a fresh Terminal window
> - `npm: command not found` → revisit pre-work step 5 (Node.js install)
> - `gh auth status` shows you're not logged in → revisit pre-work step 12

---

## 0:10–0:25 — Create your Code folder

You'll keep all your coding projects in one place: a folder called `Code` in
your home folder.

There are two ways to do this. **Both work** — you can use either throughout
the workshop. Try them both now to see they do the same thing.

### The Finder way

Open Finder, navigate to your **home folder** (sidebar, or `Cmd + Shift + H`),
right-click → **New Folder** → name it `Code`. Done.

### The Terminal way

In Terminal:

```bash
mkdir ~/Code
```

That command means "make a directory (folder), at the path `~/Code`" — `~`
being your home folder. Same result as the Finder version.

> **Tip:** You'll move between Finder and Terminal a lot. They're showing the
> same folders, just different views. A few common Terminal commands and
> their Finder equivalents:
>
> | Terminal | Finder equivalent |
> |--|--|
> | `mkdir foo` | New Folder → name it `foo` |
> | `cd foo` | Double-click the `foo` folder to open it |
> | `cd ..` | Click the back arrow in Finder |
> | `ls` | Look at the folder contents |
>
> **Jumping to any folder by its full path:** you can `cd` to any folder by
> giving its full path, e.g. `cd /Users/yourname/Documents/some/folder`.
> Shortcut: type `cd ` (with a trailing space), then drag the folder from
> Finder onto the Terminal window — Terminal pastes the full path for you.

Now move into the folder you just made:

```bash
cd ~/Code
```

Your Terminal prompt should change to show `Code` instead of `~`.

### Confirm GitHub is connected

You set this up in pre-work, but let's double-check. In Terminal:

```bash
gh auth status
```

You should see your GitHub username. If not, run `gh auth login` and follow
the prompts.

---

## 0:25–0:50 — Your first Claude Code chat

You'll talk to CC in Terminal first. Later, when you start working on a real
project, we'll move to the VSCode side. CC works the same way in both — it's
the same tool, just a different interface.

In Terminal (still in `~/Code`):

```bash
claude
```

CC starts. Type this question (don't paste — typing makes it stick better):

```
What is Claude Code and how is it different from the Claude desktop app?
```

Press Enter. Read the answer. The key points:
- CC is right here in your terminal, in the folder you opened it from
- It can read and write files on your machine
- It's not just chat — it's an agent that can take actions

Now ask:

```
What does "context window" mean and why does it matter?
```

> **Tip:** Think of CC's context window as its working memory for the
> current conversation. It can only hold so much at once. That's why we'll
> use `CLAUDE.md` files (covered next) — to keep important instructions
> available without eating up that context.

Leave CC running — you'll keep using it in the next section.

---

## 0:50–1:15 — Concepts you need to know

A few core concepts explain almost everything CC does. You're still in CC in
Terminal — try the slash commands as we go.

### 1. Conversations (chat sessions)

- Each time you run `claude`, you're in a **session** (a single conversation).
- To start CC and resume a previous conversation, use these flags in Terminal
  (when CC isn't running yet): `claude --continue` (last conversation) or
  `claude --resume` (pick from a list).
- If CC is already running, the same thing works as slash commands: type
  `/resume` or `/continue` inside CC.
- Sessions are stored in `~/.claude/projects/`.

> **Tip — chats are tied to the folder path.** CC links conversations to the
> exact folder location on your Mac. If you move or rename a project folder,
> CC won't find the old chats — it'll start fresh. Your code and git history
> are fine (see below), but the chat history stays linked to the original path.

> **Tip — chats are shared across CC interfaces.** A chat started in Terminal
> CC shows up in the VSCode extension's chat panel and in the Claude desktop
> app (when you're in the same folder). Pick whichever interface feels right.

### 2. Slash commands

Type `/` in CC right now to see the available commands. Useful ones:

- `/help` — see what's available
- `/resume`, `/continue` — same as the CLI flags above
- `/clear` — start a fresh conversation
- `/compact` — compress the current conversation when it gets long
- `/mcp` — manage MCP connections (you'll use this in Session 2)
- `/plugin` — install or manage plugins (also Session 2)
- `/exit` — quit CC

You don't have to memorize these. Just know the `/` menu exists.

### 3. Git vs GitHub — your project's real memory

**Git** is a tool that runs on your Mac. It tracks every change you make to
your project — like an unlimited undo history. All that history lives inside
your project folder (in a hidden `.git` folder). It doesn't need the internet.
Move the folder, rename it, put it on a USB stick — `git log` still works.

**GitHub** is a website where you can upload a copy of your git project. Useful
when you want to share code, back it up online, or collaborate. But it's
optional — if you're working alone on a quick prototype, you can use git
locally and never push to GitHub. The project still has full history.

> **Branches and merging.** Git lets you have multiple parallel versions of
> your project inside the same folder — called **branches**. You can switch
> between them, try changes on one without affecting the others, and **merge**
> the changes back into the main branch when you're happy. We'll use this in
> Session 2 when we collaborate. For now, just know branches exist.

Bottom line: git is the durable record, GitHub is the optional sharing layer.

### 4. CLAUDE.md — Project memory

A markdown file that CC reads automatically at the start of every session.
Use it for: project conventions, tech stack, things CC should always know.

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

**Try it now.** In CC (still running in `~/Code`), ask it to create the file
for you:

```
Create a CLAUDE.md in this folder with one rule: always write commit messages
in lowercase.
```

CC will create the file. Then type `/clear` to start a fresh chat, and ask:

```
What are your instructions for this project?
```

CC should mention the lowercase rule.

### The big picture

| Type | What it is | When to use |
|------|-----------|-------------|
| Session chat | The current conversation | Everything — it's the main loop |
| Slash commands | Built-in shortcuts | Quick actions without leaving the chat |
| Git | Permanent project history | Every meaningful change — your durable record |
| CLAUDE.md | Persistent project instructions | Rules and conventions that never change |

---

## 1:15–2:00 — Your first project, committed and pushed

Time to put it all together. You'll switch to VSCode, build a tiny web page
with CC, commit it, push it to GitHub, edit it, and commit again — getting
comfortable with the whole loop.

First, exit Terminal CC for now (`/exit`) — you're moving to VSCode.

### Create the project folder

Use whichever you prefer:

- **Finder:** open `~/Code`, right-click → New Folder → name it `my-first-project`.
- **Terminal:** `mkdir ~/Code/my-first-project`

### Open it in VSCode

In VSCode: `File → Open Folder` → pick `~/Code/my-first-project`.

This is your first time really using VSCode in the workshop, so a quick tour
of what you're looking at:

- **Left sidebar icons:** Explorer (files), Search, Source Control (git),
  Extensions, and the Claude icon (the CC extension you installed in pre-work).
- **Command Palette:** press `Cmd + Shift + P` and type anything. Try it now:
  type "theme" → "Color Theme" → pick one you like.
- **Editor area:** where files open when you click them in the Explorer.

### Open CC inside VSCode

Click the **Claude icon** in the left sidebar. The CC chat panel opens — this
is the same Claude Code you used in Terminal, just with a graphical UI.

> **Tip — chat panel vs Terminal CC.** Both share the same chat history; pick
> whichever feels right. The chat panel has nicer diffs and a click-to-approve
> permission UI. Terminal CC starts faster, is better for quick questions or
> small tasks, and supports every slash command (the chat panel is missing a
> few — `/resume`, `/continue`, `/clear`, `/exit`).
>
> If you'll use both interfaces a lot, you can keep things consistent by
> switching the CC extension to its terminal-style mode: VSCode Settings →
> Extensions → Claude Code → check **Use Terminal**.

OK, CC is open inside VSCode. Time to actually build something.

### Build a tiny web page

In the CC chat panel, type:

```
Create a simple index.html that says "Hello, [your name]!" with a heading
and a paragraph. Initialize git, commit the file, and create a GitHub repo
for the project.
```

CC will:
1. Write the `index.html` file
2. Run `git init`
3. Make a first commit
4. Run `gh repo create` to make a GitHub repo and push to it

When CC asks for permission to run `gh repo create` — approve it.

Watch the **Explorer** on the left — files appear as CC creates them. Click
`index.html` to open and read what CC wrote.

> **Open it in a browser too:** in Finder, right-click `index.html` →
> **Open With** → pick a browser. (Double-clicking it doesn't always open in
> a browser — it depends on what app is set as the default for `.html` files.)

### Check it on GitHub

Open https://github.com in a browser, find the new repo on your profile.
You should see your `index.html` and the commit message CC wrote.

> **Reminder — GitHub is optional.** Pushing to GitHub is what made your
> project visible online. For solo prototyping you don't need it — git alone
> on your Mac is enough. We're using GitHub here so you can practice the full
> workflow.

### Commit messages

CC writes commit messages for you, which is great. But it's worth knowing
how to write one yourself:

- VSCode's **Source Control panel** (the third icon in the left sidebar) shows
  changed files and a text box where you can type a commit message
- A good message is one short line that says **what changed and why**, e.g.
  `add hello world page` or `fix typo in heading`
- Past commit messages in the same panel show what's already been done

Click the Source Control icon now — you should see "0 changes" since you
just committed. We'll come back to it after we make an edit.

### Make a change and commit again

Pick something small. In the CC chat panel:

```
Change the heading to "Welcome to my page" and add a current date below it.
Commit and push the change.
```

CC will edit the file, commit, and push.

> **Try @ mentions.** If you want to point CC at a specific file, type
> `@index.html` in your message — that pulls the file into the conversation.
> When you're working in VSCode, just opening or selecting text in a file is
> often enough — CC sees what you have open. The `@` syntax is a more explicit
> way to do the same thing, and it's how you'd do it in Terminal CC too.

### Walk through the source control panel

Click the **Source Control icon** again. Look for the **Graph** section — every
commit is listed with its message. Click a commit to see what changed in it,
side-by-side. This is incredibly useful when you want to revisit what you did
yesterday.

Refresh your repo on GitHub. Both commits should be there.

### Wrap-up

You just:
- Created a project from scratch
- Built a page using CC
- Committed and pushed it
- Edited it and committed again
- Saw your work both in VSCode's source control view and on GitHub

This is the loop. You describe what you want, CC does it, you review and
approve. In Session 2 you'll connect CC to Figma and Jira, create a design,
and build a prototype — same loop, bigger project.

