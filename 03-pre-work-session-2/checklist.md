# Session 2 Pre-Work

Complete this before Session 2. It takes about 25–30 minutes.
If anything doesn't work, message [facilitator] — don't leave it for the day.

You'll: connect Claude Code (CC) to Figma and Jira via MCP, then clone the
prototype starter and confirm it runs locally.

---

## 1. Start CC in Terminal

In Terminal (the Mac app):

```bash
claude
```

Keep this CC session open — you'll do all the MCP setup inside it.

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

---

## 4. Verify both connections

In the same CC session, test that Figma works:

```
Describe my Figma project template file at [your file URL]
```

Then test that Atlassian works:

```
Summarize PUPCLD-3339
```

(That's https://perforce.atlassian.net/browse/PUPCLD-3339 — the PRD you'll use
in Session 2.)

If both come back with sensible answers, the connections work.

When you're done, exit CC with `/exit`.

---

## 5. Create your prototype project

You'll create your own GitHub repo from the Perforce prototype starter
template. This is the project CC will work in during Session 2.

In Terminal:

```bash
cd ~/Code
gh repo create my-prototype --template koosolek/pd-perforce-prototype-starter --clone --public
cd my-prototype
pnpm install
```

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

---

## You're ready for Session 2

If all four checks worked — Figma MCP, Atlassian plugin, the GitHub repo, and
the running prototype — you're set. See you at the workshop.

If anything failed, message [facilitator] before the session.
