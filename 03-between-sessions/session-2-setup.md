# Session 2 Setup [WIP]

Complete this before Session 2. It takes about 15–20 minutes.
If anything doesn't work, message [facilitator] — don't leave it for the day.

---

## 1. Prepare your Figma design file

You'll need a Figma file with a simple plugin UI design. It should have:

- A frame named `Plugin UI` (392 x 200px)
- Inside: a title text ("Icon to Component"), a one-line description, and a button labeled "Create Component"

Keep it simple — this is just a reference for the workshop. Style it however you like.

**Enable Dev Mode** on the file:
1. Open the file in Figma
2. Click the grid icon in the top-right toolbar
3. Switch to Dev Mode

---

## 2. Set up Figma MCP Server

This connects Claude Code to your Figma files so it can read your designs.

In Terminal, run:

```
claude mcp add --transport http --scope user figma https://mcp.figma.com/mcp
```

Then start a new Claude Code session:

```
claude
```

Inside Claude Code, type `/mcp` and select "figma". Click **Authenticate** and allow access through the browser prompt.

You should see: "Authentication successful. Connected to figma"

---

## 3. Test the connection

Still in Claude Code, ask it:

```
Describe the "Plugin UI" frame in my Figma file
```

If it can describe your design, the connection works. You're ready for Session 2.

If you get an error, message [facilitator].
