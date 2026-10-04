# Prompt Prospect for ChatGPT, Claude and other assistants

Find who is going to any conference, expo or trade show. Prompt Prospect builds the attendee list for an event (speakers, exhibitors, sponsors, organizers, companies and the people engaging with it online), shows the evidence behind each name, and judges everyone against your ideal customer so you know who to meet before you go. This plugin connects an assistant to your Prompt Prospect workspace through the Prompt Prospect MCP server and teaches it four workflows:

- **Plan a conference**: find events near a place or in an industry from the curated catalog, save one, and start its research.
- **Find people at an event**: who is going and why, filtered by role, company, fit or relationship (speakers, sponsors, exhibitors, engaged attendees), with the evidence behind each name.
- **Check fit**: judge everyone at an event against your target customer so the matches sort to the top. This is the one paid step; it always shows an estimate and asks before spending credits.
- **Target customer**: read or edit the profile that Check fit judges against.

## What it connects to

One remote MCP server, `https://www.promptprospect.ai/api/mcp`, over Streamable HTTP with OAuth 2.1 (dynamic client registration and PKCE). There is no API key to paste: the assistant sends you to Prompt Prospect to sign in, choose a workspace and approve the scopes it asks for. Read scopes list events, people, companies and the target customer; write scopes add events, run Check fit, save people, keep notes and edit the target customer. Everything goes through the same code and limits as the Prompt Prospect app.

The plugin runs no local code, installs nothing and reads nothing from your machine. It contains only these skill files, the manifests and the icons.

## Install

**Claude Code**

```
claude plugin marketplace add AdamScholes/prompt-prospect-plugins
claude plugin install prompt-prospect@prompt-prospect-plugins
```

Then run `/mcp` once to sign in to Prompt Prospect.

**Claude (claude.ai and desktop)**: add Prompt Prospect from the directory, or Settings → Connectors → Add custom connector with the URL above.

**ChatGPT**: add Prompt Prospect from the plugin directory. Or, with developer mode on, add the MCP server URL above as a connection.

## Privacy

The server returns only data from your own workspace and the public event catalog: event details, people connected with an event (name, headline, company, LinkedIn profile URL and the evidence that puts them there), companies, fit verdicts and your target customer. It never returns email addresses, phone numbers or payment details. The full policy is at https://www.promptprospect.ai/privacy and the terms at https://www.promptprospect.ai/terms. Support: chris@promptprospect.ai.

## Documentation

This README is the documentation. Product help and answers to common questions: https://www.promptprospect.ai/faq
