# KAIROS Prompt Map — plugin for Grok Bot, Cursor, and MCP hosts

**What it does.** Scores how completely a prompt or spec covers the
seven sections every strong prompt needs — role, objective, context,
rules, review, start, ship — and shows the gaps: which sections are
missing, thin, or shallow, with word counts as evidence. Bring a
system prompt, an agent configuration, or a work spec; get back a
spec score and a concrete list of what to strengthen.

The score is structural: it measures coverage under a published
formula (sections filled, word volume, section depth). It does not
judge meaning — a complete score means the structure is covered, not
that the words are right. The plugin is free and needs no account.

**Tools**

| Tool | Label | What it does |
|---|---|---|
| `kairos_prompt_map_score` | Write | Scores the seven sections, returns the spec score, per-section coverage, and the gap list |
| `kairos_prompt_map_cta` | Read | Returns the next-step link (free KAIROS assessment) for a scored prompt map |

**Configure variables.** None. No key, no sign-in, and none of your
credentials are ever requested or stored.

**Privacy.** The scoring server stores nothing. Your section text is
scored in the call and not kept; the report you carry between calls
holds only the score summary inside a signed token.

## Test locally

The package points at the hosted endpoint in `mcp.json` (deployed
with the plugin's marketplace submission). To exercise the tools
before that, run the bundled server and point any MCP client at it:

```bash
python3 server/mcp_server.py --port 8732   # POST JSON-RPC to /mcp
python3 tests/test_flow.py                # full flow test
```

Cursor IDE local load:

```bash
ln -s /path/to/kairos-prompt-map "$HOME/.cursor/plugins/local/kairos-prompt-map"
```

Then reload the window and confirm the `kairos-prompt-map` skill and
MCP server load.

## Submit

- Grok Bot / Cursor marketplace: https://x.ai/bot/marketplace/submit-a-plugin
- License: MIT (see LICENSE) — the plugin package is open; the
  scoring service itself is hosted by KAIROS AI Systems.

Built by KAIROS AI Systems — https://kairosasi.com
