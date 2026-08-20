# Instagram MCP

This public repository provides public connection docs and MCP metadata for a hosted Instagram MCP service by SocialDataX.

If you are looking for an Instagram MCP for social media research workflows, this repository includes:

- public MCP metadata and client configuration examples
- the hosted `streamable-http` endpoint for clients that support remote MCP
- an `mcp-remote` fallback example for command/stdio-only MCP clients

The business implementation is privately hosted. This repository exposes only the public connection surface for social media content intelligence workflows.

## Search Aliases

Common search phrases for this MCP service:

- `Instagram MCP`
- `Instagram 数据 MCP`
- `Instagram data MCP`
- `Instagram 帖子 MCP`
- `Instagram 评论 MCP`
- `Instagram 回复 MCP`
- `Instagram 用户信息 MCP`
- `Instagram 用户帖子 MCP`
- `Instagram post MCP`
- `Instagram post research MCP`
- `Instagram comments MCP`
- `Instagram comment replies MCP`
- `Instagram user info MCP`
- `Instagram user posts MCP`

## Service

- Hosted MCP endpoint: `https://mcp.socialdatax.com/instagram/mcp`
- Hosted transport: `streamable-http`
- Authentication: `Authorization: Bearer <SOCIALDATAX_API_KEY>`
- Product: `SocialDataX` / `社媒数据助手`
- Website and API Key access: <https://socialdatax.com/ai?from=github>
- Registry name: `com.52choujiang/instagram-insights`
- Future registry name: `com.socialdatax/instagram-insights`
- Current public capability version: `0.1.4`

## Platform MCP

Use the hosted `streamable-http` endpoint directly from clients that support authenticated remote MCP. For clients that only support command/stdio MCP servers, use `mcp-remote` as a local compatibility proxy.

## Workflow Scope

This MCP service is designed for social media content intelligence workflows. It does not provide account login, posting, editing, liking, commenting, following, live streaming, or other account actions.

Supported workflows include:

- Query the current API Key account's SocialDataX points balance.
- Search public Instagram posts by keyword; continue with the returned `next_page_token` as `page_token`.
- Read post details when the caller already has a `post_id`.
- Resolve an Instagram post share URL into structured post details.
- Fetch paginated first-level comments directly from an Instagram post share URL.
- Fetch paginated replies under a first-level comment by `post_id` and first-level `comment_id`.
- Fetch public Instagram user info by `username` or profile URL.
- Fetch paginated public posts published by an Instagram user by `username` or profile URL.

## Tools

| Tool | Public purpose |
| --- | --- |
| `socialdatax_get_points_balance` | Query the current API Key account's SocialDataX points balance. |
| `instagram_search_posts` | Search public Instagram posts by search term. Use this tool when the user needs posts found by a search term; when a post link is already available, use the corresponding detail or comment tool; when only a `post_id` is available, use the detail-by-ID tool, then use the returned `share_url` for comments; when a profile link or username is available, use the corresponding user info or user posts tool. Supports `page_token` continuation. |
| `instagram_get_post_detail_by_post_id` | Fetch structured post details when the caller already has a `post_id`. |
| `instagram_get_post_detail_by_post_url` | Resolve an Instagram post share URL into structured post details. |
| `instagram_get_post_comments_by_post_url` | Fetch paginated first-level comments directly from an Instagram post share URL. |
| `instagram_get_post_comment_replies_by_comment_id` | Fetch paginated replies under a first-level comment by `post_id` and first-level `comment_id`. |
| `instagram_get_user_info_by_username` | Fetch public Instagram user info by username. |
| `instagram_get_user_info_by_profile_url` | Fetch public Instagram user info by profile URL. |
| `instagram_get_user_posts_by_username` | Fetch paginated public posts published by an Instagram user by username. |
| `instagram_get_user_posts_by_profile_url` | Fetch paginated public posts published by an Instagram user by profile URL. |

## Quick Start

For clients that support authenticated `streamable-http`, use the hosted endpoint directly:

```json
{
  "mcpServers": {
    "socialdatax-instagram": {
      "type": "streamable_http",
      "url": "https://mcp.socialdatax.com/instagram/mcp",
      "headers": {
        "Authorization": "Bearer <SOCIALDATAX_API_KEY>"
      }
    }
  }
}
```

A configuration template is available in [`examples/streamable_http_config.json`](examples/streamable_http_config.json). Replace `<SOCIALDATAX_API_KEY>` with your API Key before use.

For command/stdio-only MCP clients, use `mcp-remote`:

```json
{
  "mcpServers": {
    "socialdatax-instagram": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote",
        "https://mcp.socialdatax.com/instagram/mcp",
        "--header",
        "Authorization: Bearer <SOCIALDATAX_API_KEY>"
      ]
    }
  }
}
```

Claude Code can use remote HTTP directly:

```bash
claude mcp add --transport http socialdatax-instagram https://mcp.socialdatax.com/instagram/mcp --header 'Authorization: Bearer ${SOCIALDATAX_API_KEY}'
```

Persist `SOCIALDATAX_API_KEY` in the runtime environment or client Secret before restarting Claude Code.

Claude Desktop should use its remote MCP / Connectors UI when available. If a local configuration file in your version only supports command/stdio servers, use the `mcp-remote` fallback.

## Client Examples

Configuration examples are available in [examples](examples/):

- [Command/stdio fallback config](mcp.json)
- [Claude Desktop fallback config](examples/claude_desktop_config.json)
- [Cursor remote HTTP config](examples/cursor_mcp.json)
- [Codex remote HTTP config](examples/codex_config.toml)
- [Direct streamable HTTP config](examples/streamable_http_config.json)

## API Key

Request or manage API access from the product website:

<https://socialdatax.com/ai?from=github>

Use the key as a Bearer token in the `Authorization` request header. Do not commit real API Key values to code, docs, issues, or screenshots.

## Directory Metadata

Public metadata files in this repository:

- [server-card.json](server-card.json): directory-oriented metadata for the hosted service. Official MCP Registry publishing uses the private source repo's `registry/instagram/server.json` for the current `com.52choujiang/instagram-insights` entry.
- [mcp.json](mcp.json): generic command/stdio fallback config using `mcp-remote`.
- [glama.json](glama.json): Glama repository ownership metadata.
- [SUBMISSION_CHECKLIST.md](SUBMISSION_CHECKLIST.md): checklist for MCP directory submissions.

## License

The files in this public repository are released under the MIT License. The license covers the public documentation and configuration examples in this repository only. It does not cover the managed service implementation, hosted infrastructure, or any private backend code outside this repository.
