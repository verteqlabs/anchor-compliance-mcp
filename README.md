# Anchor Compliance MCP Server

> AI-discoverable advertising and marketing compliance for Australian businesses (ACCC, TGA, ASIC, AHPRA, ACMA).

[![smithery badge](https://smithery.ai/badge/anchor-compliance)](https://smithery.ai/server/anchor-compliance)

The **Anchor Compliance MCP Server** lets AI assistants like Claude, Cursor, and ChatGPT scan websites, analyse ad copy, and pull jurisdiction-specific marketing rules — all on demand.

Built for marketers, agencies, and compliance teams operating under Australian advertising law.

---

## Tools

### `scan_website_compliance`
Scans a public URL for advertising and marketing compliance issues. Returns an indicative risk score (0–100), top issues, and a link to a full report.

**Input:** `url` (required), `industry` (optional)

### `check_ad_copy`
Analyses ad, social, or email copy against Australian regulatory frameworks. Returns risk level, flagged phrases, and indicative suggested edits.

**Input:** `content` (required), `industry` (optional), `jurisdiction` (optional, defaults to `AU`)

### `get_compliance_guidelines`
Returns a summary of compliance guidelines for an industry × jurisdiction combination (e.g. healthcare in AU, gambling in NSW).

**Input:** `industry` (required), `jurisdiction` (optional), `platform` (optional)

---

## Quickstart

### Cursor / MCP Inspector (native HTTP)

```json
{
  "mcpServers": {
    "anchor-compliance": {
      "url": "https://jrzfwnayhbkmyzieglmb.supabase.co/functions/v1/mcp-server",
      "transport": "streamable-http"
    }
  }
}
```

### Claude Desktop (via mcp-remote shim)

```json
{
  "mcpServers": {
    "anchor-compliance": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://jrzfwnayhbkmyzieglmb.supabase.co/functions/v1/mcp-server"
      ]
    }
  }
}
```

Restart your client and ask:
> *"Use anchor-compliance to scan https://example.com.au"*

---

## Try it

- **MCP Inspector:** `npx @modelcontextprotocol/inspector` → enter the URL above
- **Live endpoint:** https://jrzfwnayhbkmyzieglmb.supabase.co/functions/v1/mcp-server
- **Manifest:** https://anchorcompliance.io/mcp-manifest.json
- **Web app:** https://anchorcompliance.io/mcp

---

## Limits

The public MCP is free and rate-limited per IP per hour:
- `scan_website_compliance`: 20/hr
- `check_ad_copy`: 40/hr
- `get_compliance_guidelines`: 60/hr

For higher limits, sign up at [anchorcompliance.io](https://anchorcompliance.io).

---

## About

Built and maintained by [Anchor Compliance](https://anchorcompliance.io) — an Australian platform for ad and marketing compliance scanning, automated rewrites, and certification.

**Indicative results only — not legal advice.** Always consult a qualified compliance professional for binding guidance.

## License

MIT
