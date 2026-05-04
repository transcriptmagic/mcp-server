# TranscriptMagic MCP Server

Remote [Model Context Protocol](https://modelcontextprotocol.io) server that lets AI assistants generate transcripts from **YouTube, TikTok, Instagram, and Facebook** videos.

- **Hosted:** `https://mcp.transcriptmagic.com/mcp`
- **Transport:** Streamable HTTP (and legacy SSE)
- **Auth:** OAuth 2.0 (Sign in with Google)
- **Pricing:** 1 credit per transcript. New accounts get free credits — see [transcriptmagic.com](https://transcriptmagic.com).

No installation required. Connect it to Claude Desktop, Cursor, Windsurf, Cline, or any MCP-compatible client using the URL above.

---

## What it does

| Tool | Description | Cost |
|------|-------------|------|
| `transcribe_youtube` | Transcript from a YouTube URL (watch, youtu.be, or Shorts). | 1 credit |
| `transcribe_tiktok` | Transcript from a TikTok URL (`tiktok.com/@user/video/...` or `vm.tiktok.com`). | 1 credit |
| `transcribe_instagram` | Transcript from an Instagram URL (`/reel/`, `/p/`, `/tv/`). | 1 credit |
| `transcribe_facebook` | Transcript from a Facebook URL (`facebook.com/watch`, `fb.watch`, Reels). | 1 credit |
| `get_credit_balance` | Returns remaining credits and current plan. | Free |
| `list_recent_transcripts` | Lists recent transcripts saved to your account, with previews. | Free |

Public videos only. Does not work on private, age-restricted, or login-walled videos.

---

## Quickstart

### Claude Desktop

Add to `~/Library/Application Support/Claude/claude_desktop_config.json` (macOS) or `%APPDATA%\Claude\claude_desktop_config.json` (Windows):

```json
{
  "mcpServers": {
    "transcript-magic": {
      "url": "https://mcp.transcriptmagic.com/mcp"
    }
  }
}
```

Restart Claude Desktop. The first tool call will open a browser window to sign in with Google.

### Cursor

Settings → MCP → **Add new MCP Server** → paste `https://mcp.transcriptmagic.com/mcp`. Cursor will prompt for OAuth on first use.

### Windsurf

Settings → Cascade → MCP Servers → Add. Use the same URL.

### Cline (VS Code)

Open the Cline panel → MCP Servers → **Add Remote Server** → paste the URL above.

### Any other MCP client

Point it at `https://mcp.transcriptmagic.com/mcp` (streamable HTTP). For older clients that only support SSE, use `https://mcp.transcriptmagic.com/sse`.

---

## Example prompts

> "Transcribe this video and pull out the three main takeaways: https://www.youtube.com/watch?v=…"

> "Get the TikTok transcript at vm.tiktok.com/… and turn it into a Twitter thread."

> "List my last 10 transcripts and summarize the Instagram ones."

> "How many credits do I have left?"

---

## Pricing & credits

Credits are tied to your TranscriptMagic account. Sign in once via OAuth from your MCP client, then top up at [transcriptmagic.com/dashboard/account](https://transcriptmagic.com/dashboard/account) when you run low. New accounts come with free credits to try the server.

`get_credit_balance` and `list_recent_transcripts` are free and never consume credits.

---

## Privacy

- The server only accesses videos you explicitly send via tool calls.
- We store transcripts in your account history so you can list them later. Delete from the dashboard at any time.
- OAuth scope is limited to identifying your TranscriptMagic account — no Google Drive, Gmail, or other Google data is read.

Full policy: [transcriptmagic.com/privacy](https://transcriptmagic.com/privacy)

---

## Links

- **Website:** [transcriptmagic.com](https://transcriptmagic.com)
- **Web app:** [transcriptmagic.com/youtube](https://transcriptmagic.com/youtube), [/tiktok](https://transcriptmagic.com/tiktok), [/instagram](https://transcriptmagic.com/instagram), [/facebook](https://transcriptmagic.com/facebook)
- **REST API:** [docs.transcriptmagic.com](https://docs.transcriptmagic.com)
- **MCP per-platform pages:** [/youtube-transcript-mcp](https://transcriptmagic.com/youtube-transcript-mcp), [/tiktok-transcript-mcp](https://transcriptmagic.com/tiktok-transcript-mcp), [/instagram-transcript-mcp](https://transcriptmagic.com/instagram-transcript-mcp), [/facebook-transcript-mcp](https://transcriptmagic.com/facebook-transcript-mcp)

---

## License

[MIT](LICENSE)
