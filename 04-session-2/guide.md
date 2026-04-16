# Session 2 Facilitator Guide [WIP]
**Duration:** 2 hours | **Group:** 3 people
**Prerequisite:** Session 1 completed

---

## Before they arrive

- [ ] Test Figma MCP + Atlassian plugin on your own machine end-to-end
- [ ] Have each participant duplicate the Figma project template (see link below)
- [ ] Have the PRD Jira ticket URL ready to share
- [ ] Have the shared GitHub project repo created and participants added as collaborators

---

## 0:00–0:20 — MCP Setup (20 min)

**Goal:** CC can read Figma designs and Jira tickets.

Share the Figma MCP docs:
- https://developers.figma.com/docs/figma-mcp-server/remote-server-installation/

For Atlassian, have them discover it themselves:
- In the CC sidebar, type `/plugin`, go to the **Discover** tab, search for "atlassian"

Ask them to read the instructions and set up both. They can ask CC for help if
they get stuck — that's part of the exercise.

### Verify

Once everyone's done, test both connections:
- Ask CC to describe their Figma project template file
- Share the PRD ticket → ask CC to summarize `PUPCLD-3339` (https://perforce.atlassian.net/browse/PUPCLD-3339)

If both work, move on. Help anyone who's stuck.

---

## 0:20–0:25 — Set Up the Prototype Project (5 min)

**Goal:** Everyone has the starter template cloned and open in VSCode, ready for work.

In Terminal, everyone clones the starter template:

```bash
cd ~/Code
git clone https://github.com/koosolek/pd-perforce-prototype-starter my-prototype
cd my-prototype
npm install
```

In VSCode: `File → Open Folder` → `~/Code/my-prototype`.

> "This is the project CC will work in for the rest of the session.
> The design work and the coding will all happen here."

---

## 0:25–0:55 — Design from a PRD (30 min)

**Goal:** A Figma design created by CC, based on the PRD and the design system libraries.

Everyone opens their copy of the Figma project template:
https://www.figma.com/design/zVeRVzeF5J0sOq7ZjhdKQN/-PDUX-------Project-template

PRD ticket: https://perforce.atlassian.net/browse/PUPCLD-3339

In the CC sidebar (already in `my-prototype`):

```
Read the PRD at PUPCLD-3339. Then search the design system libraries available
in my Figma file for relevant components. Create a design for the Finance
Dashboard feature in my Figma file at [their file URL], using design system
components where possible.
```

CC will use the Figma MCP to read the PRD, search the linked libraries, and
write into their file. Let it work. Narrate:
- "CC is reading the requirements from Jira"
- "Now it's searching the design system libraries for components it can use"
- "It's creating the design directly in your Figma file"

When CC finishes, have everyone review their design in Figma.

**Why this matters to explain:**
> "This is the design loop: requirements in Jira, components in Figma, CC connects
> them. You review and refine — CC does the assembly."

---

## 0:55–1:25 — Build a Prototype (30 min)

**Goal:** A working prototype built from the design, using the Perforce prototype starter.

First, run the starter to see the default state. In Terminal:

```bash
cd ~/Code/my-prototype
npm run dev
```

Open the URL shown in Terminal (usually `http://localhost:...`) in a browser.
This is the default starter state — everyone should see the same thing.

> "This is your starting point. Now we'll ask CC to transform it into
> the design you just created."

In the CC sidebar (still in `my-prototype`):

```
Look at my Figma design at [their file URL]. Apply this design to the
prototype in this project. The project is already set up — just modify
the existing files to match the design.
```

CC will update the existing files to match their Figma design.
When it's ready, run the dev server and check in a browser.

**If something breaks:**

```
The prototype shows [describe what happened]. Fix it.
```

> "Same loop as always — CC writes, you test, CC fixes."

---

## 1:25–1:35 — Commit and Push (10 min)

**Goal:** Reinforce the git workflow from Session 1.

In the CC sidebar, ask:

```
Set up git for this project, commit everything, and create a GitHub repo for it.
```

Have everyone check their new repo on GitHub.

> "Same thing you did in Session 1 — project folder to GitHub in one prompt."

---

## 1:35–1:55 — Collaborate on a Shared Project (20 min)

**Goal:** Everyone works on the same repo using branches.

Share the URL of the pre-created GitHub project. In Terminal, everyone clones it:

```bash
cd ~/Code
git clone [repo URL]
cd [repo name]
```

Run the project and open in a browser:

```bash
npm install
npm run dev
```

Check the browser — this is the shared project's current state.

Open the folder in a **new VSCode window** (`File → New Window`, then `File → Open Folder`).

### Create a branch

In the CC sidebar:

```
Create a new git branch called [their-name]-edits
```

Under the hood, CC runs: `git checkout -b [their-name]-edits`

Explain:
> "A branch is your own copy of the project. You can make changes without
> affecting anyone else's work. When you're ready, you merge it back."

### Make edits

In the CC sidebar, give each person a different small task. For example:
- Person A: "Change the page title to [something]"
- Person B: "Add a footer with [text]"
- Person C: "Change the primary button color to [color]"

Let CC make the changes. Review in the browser.

### Push

Everyone pushes their branch. In the CC sidebar:

```
Commit my changes with the message "[their-name]: [what they changed]"
and push to the remote.
```

Under the hood, CC runs:
```bash
git add .
git commit -m "[their-name]: [what they changed]"
git push -u origin [their-name]-edits
```

### View each other's branches

First, everyone fetches the remote branches. In the CC sidebar:

```
Fetch all remote branches
```

Now point out the **branch name in the bottom-left corner of VSCode**. Click it
— a list of branches appears. Have everyone pick someone else's branch
(e.g., `origin/[other-person]-edits`).

Check the browser — they should see the other person's changes instead of their own.

> "This is how you look at a colleague's work without affecting yours.
> Each branch is independent — click the bottom-left to switch between them."

Have them click the branch name again and switch back to their own branch.

### Merge (facilitator does this on screen share)

Once all three branches are pushed, you merge them one at a time while everyone
watches. Narrate what's happening at each step.

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

If a merge conflict happens (likely on the 2nd or 3rd merge):
> "This is what happens when two people edit the same thing.
> Git doesn't know which version to keep — you have to decide."

Resolve it live with CC's help, or walk through the conflict markers manually.

### Everyone pulls the result

After all merges, everyone runs in the CC sidebar:

```
Switch to main and pull the latest changes.
```

Everyone should now see all three changes combined in their project.

---

## 1:55–2:00 — Wrap-up (5 min)

> "Today you connected CC to Figma and Jira. You created a design from a PRD,
> built a prototype from that design, and collaborated on code with your team.
> That's the full workflow — requirements to design to code to collaboration."

Leave them with:
- Their GitHub repos (personal prototype + shared project)
- The CC docs link for going deeper
- Encouragement to try this loop on a real project
