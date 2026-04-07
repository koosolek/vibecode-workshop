# Session 2 Facilitator Guide [WIP]
**Duration:** 2 hours | **Group:** 3 people
**Prerequisite:** Between-sessions solo task and Session 2 setup completed

---

## Before they arrive

- [ ] Copy `workshop-plugin/` into each person's project repo (or have them do it as step 0)
- [ ] Test Figma MCP on your own machine end-to-end
- [ ] Confirm everyone completed `03-between-sessions/session-2-setup.md` (Figma MCP connected)
- [ ] Have the reference Figma design file open (the Plugin UI frame)
- [ ] Know the Figma file URL (you'll share it)
- [ ] Have `manifest.json` docs URL bookmarked (in case questions come up)

---

## 0:00–0:10 — Solo task debrief (10 min)

Ask each person:
> "Show me your README.md commit on GitHub."

Three outcomes:
- ✓ Done → great, move on
- Commit exists but push failed → fix it now (`git push`)
- Didn't do it → that's okay, but note who — they'll need more support today

---

## 0:10–0:20 — Verify Figma MCP (10 min)

**Goal:** Confirm everyone's Figma MCP connection works.

This was set up in the Session 2 pre-work (`03-between-sessions/session-2-setup.md`).

Ask each person to start CC and test:

```
Describe the "Plugin UI" frame in my Figma file
```

Three outcomes:
- ✓ CC describes the design → move on
- Auth expired → re-authenticate: type `/mcp` in CC, select "figma", click Authenticate
- Not set up → do it now: `claude mcp add --transport http --scope user figma https://mcp.figma.com/mcp`, restart CC, authenticate

This should be quick since they did it as pre-work. Budget extra time only if someone didn't.

---

## 0:20–0:45 — Planning the Plugin (25 min)

**Goal:** A written, CC-approved plan before a single line of code is written.

Share the PRD with everyone — it's in `workshop-plugin/PRD.md`. Give them a minute to read it.

Then, in CC:

```
Read @workshop-plugin/PRD.md and the Figma design at [URL].
Use plan mode to create an implementation plan for this plugin.
```

CC will enter plan mode. It will:
- Ask clarifying questions (answer them, narrate why)
- Propose a file structure
- Outline what each file will do

Review the plan together. Ask the group:
- "Does this match what we described in the PRD?"
- "Anything missing?"

Approve the plan when it looks right. CC will ask for confirmation before writing any code.

**Why this matters to explain:**
> "Plan mode is how you stay in control. CC is very capable and will happily write
> 500 lines of code in the wrong direction. Planning first is 5 minutes that saves
> an hour of cleanup."

---

## 0:45–1:30 — Building the Plugin (45 min)

**Goal:** Working plugin, tested in Figma.

CC will now implement the plan. Let it work. Your role is to narrate and check in.

**Expected files CC will create/modify:**
- `manifest.json`
- `code.ts` (or `code.js`)
- `ui.html`
- `package.json` (if needed for TypeScript compile)

When CC finishes writing, run in terminal:

```bash
npm install
npm run build
```

(If no build script — CC may use plain JS and `code.js` directly, skip build.)

### Test in Figma

1. Open Figma desktop
2. `Plugins → Development → Import plugin from manifest`
3. Navigate to their project folder, select `manifest.json`
4. In Figma, select an icon frame
5. `Plugins → Development → [plugin name]` → run it
6. Check result: frame should become a component named correctly

**If something breaks:**

Go back to CC:

```
The plugin ran but [describe what happened]. Fix it.
```

Let CC debug. This is a key teaching moment:
> "This is normal. CC writes, you test, CC fixes. You're the tester."

Budget up to 15 minutes for debugging.

---

## 1:30–1:40 — Commit and Push (10 min)

Everyone commits their working plugin:

```bash
git add .
git commit -m "add icon-to-component plugin"
git push
```

Or have CC write the commit message:

```
Write a commit message for the changes we just made.
```

---

## 1:40–1:55 — Publish to Figma (15 min)

**Goal:** Plugin is published to your org (private) or their personal account.

1. In Figma desktop: `Plugins → Development → Publish`
2. Add a name, short description, and cover image (screenshot works)
3. Choose "Share with [org]" or "Publish publicly"
4. Submit

If time is short, skip and do async — publishing is mechanical and doesn't require CC.

---

## 1:55–2:00 — Wrap-up (5 min)

> "You built a real, published Figma plugin. You used CC to write all the code.
> You used git and GitHub to track your work. You used Figma MCP to share a design.
> That's the whole loop."

Leave them with:
- Their GitHub repo URL with the plugin code
- The CC docs link for going deeper
- The suggestion to try modifying the plugin on their own — change the component name format, add a notification, etc.
