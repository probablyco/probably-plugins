# Probably plugins

[Probably](https://studio.probably.co) makes AI UGC videos (TikTok, Reels and
Shorts ads) with a crew of researchers, writers, producers, editors and
critics. This repository is its marketplace for Claude Code, and its skills for
Codex.

The `probably` plugin adds Probably's MCP server and five skills: `probably`
(how to use the tools, and the rule that every paid step waits for your yes),
`test-hooks`, `ad-to-brief`, `research-then-script` and `check-videos`.

## Claude Code

```sh
claude plugin marketplace add probablyco/probably-plugins
claude plugin install probably@probably
```

Then run `/mcp` in Claude Code, choose the plugin's **probably** server and
sign in.

## Codex

```sh
git clone https://github.com/probablyco/probably-plugins ~/.probably-plugins
mkdir -p ~/.agents/skills
ln -s ~/.probably-plugins/probably/skills/* ~/.agents/skills/
```

Add the MCP server to `~/.codex/config.toml` and sign in with
`codex mcp login probably`:

```toml
[mcp_servers.probably]
url = "https://studio.probably.co/api/mcp"
```

The full guide, with API keys and what each recipe does, is at
https://studio.probably.co/docs/plugin.
