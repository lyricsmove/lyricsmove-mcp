# LyricsMove MCP server and agent skill

[LyricsMove](https://lyricsmove.com) turns an MP3, WAV, M4A, or public Suno song link into an animated lyric video (rendered locally in the browser) or an 8–32 scene Cinema V2 AI music video. This repository holds the connection details for its public read-only MCP server and an [Agent Skill](skills/lyricsmove/SKILL.md) that teaches AI assistants to use it. Nothing needs to be installed locally.

- **MCP endpoint:** `https://lyricsmove.com/mcp` (Streamable HTTP)
- **Auth:** none. Public read-only catalog and setup recommender — no API key or signup required.
- **Registry name:** `com.lyricsmove/lyricsmove` in the [official MCP Registry](https://registry.modelcontextprotocol.io/v0/servers?search=com.lyricsmove/lyricsmove)
- **Docs:** [lyricsmove.com/docs/mcp](https://lyricsmove.com/docs/mcp) · [llms.txt](https://lyricsmove.com/llms.txt)

## Try in browser

Start without an API key or account at [lyricsmove.com](https://lyricsmove.com/?utm_source=claude_skill#make) — free full-song 720p lyric video exports work immediately in the browser, or explore the [9 AI Music Video looks](https://lyricsmove.com/ai-music-video-generator?utm_source=claude_skill).

## Connect

**Claude Code**

```bash
claude mcp add --transport http lyricsmove https://lyricsmove.com/mcp
```

**Cursor** (`~/.cursor/mcp.json`)

```json
{
  "mcpServers": {
    "lyricsmove": {
      "type": "http",
      "url": "https://lyricsmove.com/mcp"
    }
  }
}
```

**Codex** (`~/.codex/config.toml`)

```toml
[mcp_servers.lyricsmove]
url = "https://lyricsmove.com/mcp"
```

In Claude Desktop or ChatGPT, add `https://lyricsmove.com/mcp` as a custom connector.

## Tools

| Tool | What it does |
| --- | --- |
| `list_lyric_styles_and_tools` | Return animated lyric styles, shader/video backgrounds, formats (`16:9`, `9:16`), and browser audio/subtitle tools (`/bpm-finder`, `/mp3-to-mp4`, `/mp3-cutter`, `/mp3-to-srt`) |
| `list_ai_mv_styles` | Browse all 9 selectable AI music video looks (Cinema V2, 8–32 beat-snapped scenes) with mood guidance and YouTube sample links |
| `recommend_video_setup` | Match mood, genre, language (`en` or `ja`), Suno link, or character photo to curated styles and a direct studio URL |
| `get_pricing_and_limits` | Exact pricing (free 720p tier, $3.90 Pro 1080p song, $9.90 AI MV, monthly Pro/Ultra plans), upload limits, and retention policy |

## Endpoints & LLMs

- `https://lyricsmove.com/llms.txt`
- `https://lyricsmove.com/pricing`

## Agent skill

[`skills/lyricsmove/SKILL.md`](skills/lyricsmove/SKILL.md) follows the [Agent Skills](https://agentskills.io) format. Install it with:

```bash
npx skills add lyricsmove/lyricsmove-mcp
```

or copy `skills/lyricsmove/` into your agent's skills directory (for Claude Code, `~/.claude/skills/lyricsmove/`).

### One-line prompt for any AI agent

Paste into Claude Code, Cursor, Codex, or Gemini CLI:

```text
Read https://raw.githubusercontent.com/lyricsmove/lyricsmove-mcp/main/skills/lyricsmove/SKILL.md and recommend a LyricsMove style and direct link for my song.
```

## Support

support@lyricsmove.com

## License

The files in this repository are MIT licensed. Media generation and paid plans on lyricsmove.com are covered by [lyricsmove.com/terms](https://lyricsmove.com/terms).
