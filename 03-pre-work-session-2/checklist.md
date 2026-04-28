# Session 2 Pre-Work

Complete this before Session 2. It takes about 25–30 minutes.
If anything doesn't work, message [facilitator] — don't leave it for the day.

You'll: connect Claude Code (CC) to Figma and Jira via MCP, then clone the
prototype starter and confirm it runs locally.

---

## For facilitators (or solo learners)

Before participants arrive, the facilitator needs to have a few things ready.
**If you're going through this workshop on your own, you'll need to prep these
yourself.**

- A **PRD ticket in Jira** that participants will turn into a design. It
  should be self-contained, scoped, and clear about requirements. If you
  don't already have one, Atlassian's product requirements template is a
  good starting point:
  https://www.atlassian.com/software/confluence/templates/product-requirements
- A **Figma project template** for participants to design in, with relevant
  design system libraries linked (we use the PDUX project template internally)
- A **shared GitHub project repo** for the collaboration section, with all
  participants added as collaborators. Easiest path: another fresh clone of
  the prototype starter, possibly with one small change so there's something
  to merge into
- A few **small edit assignments** — one per participant — for the
  collaboration section (e.g. "Person A: change the page title to X",
  "Person B: change the button color", "Person C: add a footer")

Participants need to be added to the `Perforce-Shared-Services` GitHub org
in advance — pre-work step 5 fails without that access.

Verify your own MCP connections work end-to-end before the session.

---

## 1. Start CC in Terminal

In Terminal (the Mac app):

```bash
claude
```

Keep this CC session open — you'll do all the MCP setup inside it.

> **Tip — slash commands like `/plugin` and `/mcp` only work *inside* CC.**
> Once `claude` is running, your prompt has changed and you're talking to CC.
> That's where slash commands work. If you `/exit` CC, you're back in Terminal
> — typing `/plugin` there won't do anything.

---

## 2. Install the Figma MCP

Read the install instructions and follow them:
https://developers.figma.com/docs/figma-mcp-server/remote-server-installation/

> **Tip:** Reading docs and figuring it out from there is a real-world skill.
> If you get stuck, ask CC for help — it can read the same docs.

---

## 3. Install the Atlassian plugin

In CC, type `/plugin`, go to the **Discover** tab, and search for "atlassian".
Follow the prompts to install it.

> **Alternative — Atlassian Rovo connector.** If you prefer not to use the
> Claude Code plugin, you can connect Atlassian via Rovo instead. In the
> Claude desktop app: Settings → **Connectors** → Atlassian. Rovo also works
> with Claude Code (Terminal + VSCode), so you don't have to choose just one.
>
> When to pick which:
> - **CC plugin** (recommended for this workshop): more Atlassian capabilities
>   — search, create, comment, transition Jira issues, full Confluence editing
> - **Rovo connector**: simpler setup via Atlassian; mostly read/search; works
>   the same in Claude desktop app and even ChatGPT

---

## 4. Verify both connections

In the same CC session, test that Figma works:

```
Describe my Figma project template file at [your file URL]
```

Then test that Atlassian works — the facilitator will share a PRD ticket URL
or key. Ask CC to summarize it:

```
Summarize [PRD ticket key, e.g. ABC-123]
```

If both come back with sensible answers, the connections work.

When you're done, exit CC with `/exit`.

---

## 5. Create your prototype project

You'll create your own GitHub repo from the Perforce prototype starter
template. This is the project CC will work in during Session 2.

In Terminal:

```bash
cd ~/Code
gh repo create my-prototype --template Perforce-Shared-Services/pd-perforce-prototype-starter --clone --public
cd my-prototype
pnpm install
```

> **Heads up — make sure you have access to the `Perforce-Shared-Services`
> GitHub org.** If the `gh repo create` command fails with a permissions or
> "not found" error, message [facilitator] — you may need to be added to the
> org first.

> If `pnpm` isn't installed, install it first: `sudo npm install -g pnpm`

---

## 6. Verify the project runs

In Terminal (still in `~/Code/my-prototype`):

```bash
pnpm dev
```

Open the URL shown in Terminal (usually `http://localhost:...`) in a browser.
You should see the default starter page.

When you've seen it work, stop the server with `Ctrl + C`.

> **Tip — every project's README is the source of truth.** When you open a
> new project, the `README.md` file usually tells you exactly what commands
> to run to install and start it. The two commands above (`pnpm install` and
> `pnpm dev`) come from this project's README.

---

## 7. (Recommended) Install DevBar for managing dev servers

DevBar is a free Mac menu bar app that helps you start, stop, and monitor
local dev servers without juggling Terminal windows. Strongly recommended
for Session 2 — without it, you'll be hunting for Terminal windows, killing
servers manually, and dealing with port conflicts.

Follow the install instructions and prerequisites in the project's README:
https://github.com/koosolek/devbar

Once installed, DevBar lives in your menu bar (top-right of the screen).
Click it to see your projects, start/stop their dev servers, and open them
in VSCode.

---

## You're ready for Session 2

If everything worked — Figma MCP, Atlassian plugin, the GitHub repo, the
running prototype, and (optionally) DevBar — you're set. See you at the
workshop.

If anything failed, message [facilitator] before the session.
