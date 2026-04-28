# Session 2 — Design, Prototype, Collaborate [WIP]
**Duration:** ~1.5 hours (within a 2-hour session — extra time is buffer)
**Prerequisite:** Session 1 completed and `03-pre-work-session-2/checklist.md`
done (MCP integrations set up, prototype starter cloned)

In this session you'll create a design from a real PRD, build a prototype
based on that design, and collaborate with others on a shared GitHub project.

> **For facilitators:**
> - Confirm everyone completed `03-pre-work-session-2/checklist.md` before the session
> - Have the PRD Jira ticket URL ready to share
> - Have the shared GitHub project repo created and participants added as collaborators
> - Verify your own MCP connections work end-to-end before the session

---

## 0:00–0:30 — Create a design from a PRD

Now you'll have CC create a Figma design based on a real PRD, using design
system components.

Open your copy of the Figma project template:
https://www.figma.com/design/zVeRVzeF5J0sOq7ZjhdKQN/-PDUX-------Project-template

The PRD: https://perforce.atlassian.net/browse/PUPCLD-3339

In VSCode: `File → Open Folder` → `~/Code/my-prototype` (the project you
cloned in pre-work). Open the CC sidebar:

```
Read the PRD at PUPCLD-3339. 
Then search the design system libraries [library URL] & [library URL] for relevant components.
Create a design for the Finance Dashboard feature in my Figma file at [frame URL], using design system
components where possible.
```

CC will use the Figma MCP to read the PRD, search the linked libraries, and
write into your file. Watch it work — you'll see CC reading the requirements,
searching the libraries, then creating the design directly in your Figma file.

When CC finishes, review the design in Figma.

> **The design loop:** requirements live in Jira, components live in Figma, CC
> connects them. You review and refine — CC does the assembly. Expect to
> iterate: tell CC what to fix or add, and let it adjust.

> **Tip — Figma generation is slow.** Creating Figma content via MCP is
> noticeably slower than CC writing code. A first pass can take several
> minutes. Be patient and let CC finish before sending follow-up prompts —
> interrupting mid-generation usually makes things worse.

---

## 0:30–1:00 — Build a prototype from your design

Now you'll turn the Figma design into a working web prototype.

### Start the dev server

First, see what the starter looks like by default. In the CC sidebar:

```
Start the dev server for this project.
```

CC will run the right command (you can see it does `pnpm dev`) and give you
a localhost URL. Open it in a browser — this is your starting point.

> **Tip — running the dev server yourself.** Anything CC does, you can do
> manually. The Terminal version is two commands:
>
> ```bash
> cd ~/Code/my-prototype
> pnpm dev
> ```
>
> The first moves into the project folder, the second starts the dev server.
> You can also chain them with `&&` to run both at once:
> `cd ~/Code/my-prototype && pnpm dev`.
>
> If you're juggling multiple projects, **DevBar** (from pre-work) is the
> easiest way — click the DevBar icon in the menu bar, find your project,
> hit start.

### Apply the design to the prototype

In the CC sidebar:

```
Look at my Figma design at [file URL]. Apply this design to the
prototype in this project. The project is already set up — just modify
the existing files to match the design.
```

CC will update the files to match your design. When it's done, refresh the
browser to see the result.

**If something breaks:**

```
The prototype shows [describe what happened]. Fix it.
```

> **The loop:** CC writes, you test in the browser, CC fixes. Same pattern as
> Session 1 — just with a real prototype this time.

> **Tip — port already in use?** If you stop and restart the dev server, you
> might see an error like "port 3000 already in use". The previous server is
> still running somewhere. In DevBar, click "stop" on the project. In Terminal,
> press `Ctrl + C` in whichever window started it.

---

## 1:00–1:10 — Commit and push

Same git workflow as Session 1. Your GitHub repo already exists (it was
created from the template in pre-work), so you just need to commit and push.

In the CC sidebar:

```
Commit all the changes and push to GitHub.
```

Open your repo on GitHub and confirm the new commits are there.

---

## 1:10–1:30 — Collaborate on a shared project

Now you'll work on a shared project alongside others — using branches so
everyone's work stays separate until it's time to merge.

> **Working alone?** This section assumes a group, but you can practice the
> branch/merge flow on your own. Use the `my-prototype` project you set up
> in pre-work — create two or three branches there with different small
> changes, then merge them in. The steps below work the same way.

The facilitator will share the URL of the shared GitHub project.

### Clone the shared project

In the CC sidebar:

```
Clone [repo URL] into my ~/Code folder, install dependencies, and start the
dev server.
```

CC will clone, run `pnpm install`, and start the server. Open the localhost
URL — this is the shared project's current state.

> **Tip — under the hood:**
>
> ```bash
> cd ~/Code
> git clone [repo URL]
> cd [repo name]
> pnpm install
> pnpm dev
> ```
>
> If you'd rather use DevBar to manage the dev server, you can ask CC to clone
> and install only, then start the server from DevBar.

Open the cloned folder in a **new VSCode window** (`File → New Window`, then
`File → Open Folder`) so it doesn't take over your prototype window.

### Create a branch

In the CC sidebar:

```
Create a new git branch called [your-name]-edits
```

Under the hood, CC runs: `git checkout -b [your-name]-edits`

> **What's a branch?** It's your own copy of the project where you can make
> changes without affecting anyone else. When you're ready, your branch gets
> merged back into the main branch.

### Make some edits

In the CC sidebar, ask CC to make a small change. The facilitator will give
each person a different task — for example:

- "Change the page title to [something]"
- "Add a footer with [text]"
- "Change the primary button color to [color]"

Review the result in the browser.

### Push your branch

In the CC sidebar:

```
Commit my changes with the message "[your-name]: [what you changed]"
and push to the remote.
```

Under the hood, CC runs:

```bash
git add .
git commit -m "[your-name]: [what you changed]"
git push -u origin [your-name]-edits
```

### Look at someone else's work

First, fetch all remote branches. In the CC sidebar:

```
Fetch all remote branches
```

Now look at the **branch name in the bottom-left corner of VSCode**. Click it
— a list of branches appears. Pick someone else's branch (e.g.
`origin/[other-person]-edits`).

Check the browser — you should see their changes instead of yours.

> **Tip:** Each branch is independent. The bottom-left branch picker is the
> easiest way to jump between them — useful for reviewing a colleague's work
> without touching your own.

When you're done looking, click the branch name again and switch back to your
own branch.

### Merge everything to main

Once all branches are pushed, the facilitator will merge them one at a time
on screen share so you can watch.

> **Working alone or want to do it yourself?** Run the steps below in your
> own Terminal. Same commands, just done by you instead of the facilitator.

```bash
git checkout main
git pull
git merge person-a-edits
git push
git merge person-b-edits
git push
git merge person-c-edits
git push
```

> **Merge conflicts** can happen if two branches changed the same lines. If
> you hit one, ask CC to help resolve it — that's a great use of CC inside the
> git workflow.

### Pull the combined result

Once all merges are done, everyone updates their copy. In the CC sidebar:

```
Switch to main and pull the latest changes.
```

You should now see all the changes combined in your project — the payoff
moment of the workshop.

---

## 1:30–1:35 — Wrap-up

You connected CC to Figma and Jira, created a design from a PRD, built a
prototype from that design, and collaborated on code with your team. That's
the full workflow — requirements → design → code → collaboration.

You leave with:
- Two GitHub repos: your personal prototype and the shared project
- The CC docs (https://docs.claude.com/en/docs/claude-code) for going deeper
- A real example you can rerun on your own project

> **Try it on something real.** The fastest way to get comfortable with this
> loop is to use it on a small project of your own — even a quick HTML page
> or a script. The patterns are exactly the same.
