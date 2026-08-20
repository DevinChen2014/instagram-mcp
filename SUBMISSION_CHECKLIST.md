# MCP Directory Submission Checklist

Use this checklist before syncing this listing to the public Instagram MCP repository, submitting it to MCP directories, or updating a directory entry.

## Public Repository

- Primary repository name: `instagram-mcp`
- Fallback repository name if unavailable: `instagram-socialdatax-mcp`
- Repository URL after creation: `https://github.com/DevinChen2014/instagram-mcp`
- Repository description: `Instagram MCP by SocialDataX for public post search, post details, comments, comment replies, user info, and user posts.`
- Suggested repository topics: `mcp`, `mcp-server`, `instagram`, `instagram-mcp`, `instagram-posts`, `socialdatax`, `social-insights`, `marketing-research`, `comment-analysis`
- Root README title: `Instagram MCP`
- Product: `SocialDataX` / `社媒数据助手`
- Website: `https://socialdatax.com`
- Registry name: `com.52choujiang/instagram-insights`
- Future registry name: `com.socialdatax/instagram-insights`
- Hosted MCP endpoint: `https://mcp.socialdatax.com/instagram/mcp`
- Hosted auth: `Authorization: Bearer <SOCIALDATAX_API_KEY>`
- Default client transport: hosted `streamable-http`
- Command/stdio fallback: `npx -y mcp-remote https://mcp.socialdatax.com/instagram/mcp --header "Authorization: Bearer <SOCIALDATAX_API_KEY>"`
- License: MIT for the public documentation and examples only

## Safety Checks

- No real API Key values are present.
- No private backend implementation is included.
- No production configuration is included.
- No internal samples are included.
- No account data or credentials are included.
- No generated build output is included.
- Public text uses neutral product wording.
- Public docs do not expose internal business code.

## Required Files

- `README.md`
- `LICENSE`
- `server-card.json`
- `mcp.json`
- `glama.json`
- `examples/streamable_http_config.json`
- `examples/claude_desktop_config.json`
- `examples/cursor_mcp.json`
- `examples/codex_config.toml`
- `assets/logo.png`

## Directory Checks

- Hosted streamable HTTP clients can connect directly to `https://mcp.socialdatax.com/instagram/mcp` with `Authorization: Bearer <SOCIALDATAX_API_KEY>`.
- With a valid key, hosted MCP `initialize` succeeds.
- With a valid key, hosted MCP `tools/list` returns the current 10 public tools.
- `socialdatax_get_points_balance` is present in `tools/list`.
- `instagram_search_posts` is present in `tools/list`; if it is missing, deploy the latest service before publishing.
- `instagram_get_post_detail_by_post_id` and `instagram_get_post_detail_by_post_url` are present in `tools/list`; if either is missing, deploy the latest service before publishing.
- `instagram_get_post_comments_by_post_url` and `instagram_get_post_comment_replies_by_comment_id` are present in `tools/list`; if either is missing, deploy the latest service before publishing.
- `instagram_get_user_info_by_username` and `instagram_get_user_info_by_profile_url` are present in `tools/list`; if either is missing, deploy the latest service before publishing.
- `instagram_get_user_posts_by_username` and `instagram_get_user_posts_by_profile_url` are present in `tools/list`; if either is missing, deploy the latest service before publishing.
- `examples/codex_config.toml` uses remote HTTP URL and `bearer_token_env_var`, not `mcp-remote`.
- `examples/cursor_mcp.json` uses remote HTTP URL and `headers` with `${env:SOCIALDATAX_API_KEY}`, not `mcp-remote`.
- `mcp.json` is explicitly command/stdio fallback and uses `mcp-remote`.
- Before submitting to directories, verify `https://mcp.socialdatax.com/instagram/.well-known/mcp/server-card.json` returns the Instagram server card, not the root XHS server card.

## Directory Submission Order

1. Official MCP Registry
2. GitHub public repository
3. Glama
4. ModelScope MCP 广场
5. MCP.Directory
6. MCP.so
7. mcpservers.org
8. MCP Market
9. Cline MCP Marketplace
10. awesome-mcp-servers / awesome-remote-mcp-servers

## Search Keywords To Verify After Approval

- `Instagram`
- `Instagram MCP`
- `Instagram data MCP`
- `Instagram post MCP`
- `Instagram comments MCP`
- `Instagram comment replies MCP`
- `Instagram user info MCP`
- `Instagram user posts MCP`
- `SocialDataX`
- `社媒数据助手`
