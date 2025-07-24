# Twitter MCP Server

[![smithery badge](https://smithery.ai/badge/@dewkiks/twitter-mcp-server)](https://smithery.ai/server/@dewkiks/twitter-mcp-server)

A Model Context Protocol (MCP) server for Twitter integration using cookie-based authentication. Allows AI assistants to interact with Twitter through a standardized protocol.

## ⚠️ Disclaimer

This uses an **unofficial Twitter API** via the `twikit` library. Not endorsed by Twitter/X and may break without notice. Use for educational/experimental purposes only. Account restrictions possible.

## Quick Setup

### Installing via Smithery

To install Twitter MCP Server for Claude Desktop automatically via [Smithery](https://smithery.ai/server/@dewkiks/twitter-mcp-server):

```bash
npx -y @smithery/cli install @dewkiks/twitter-mcp-server --client claude
```

### Manual Installation
1. **Install**
```bash
git clone <repository-url>
cd twitter-mcp
pip install -r requirements.txt
```

2. **Get Twitter Cookies**
   - Open Twitter/X in browser and login
   - Open Developer Tools (F12) → Application/Storage → Cookies → twitter.com
   - Copy these values:
     - `ct0` (CSRF token)
     - `auth_token` (Authentication token)

3. **Configure Claude Desktop**
Add to your `claude_desktop_config.json`:
```json
{
  "mcpServers": {
    "twitter": {
      "command": "python",
      "args": ["./path/to/server.py"],
      "env": {
        "TWITTER_CT0": "your_ct0_here",
        "TWITTER_AUTH_TOKEN": "your_auth_token_here"
      }
    }
  }
}
```

## Main Features

- **Tweet Management**: Post, like, retweet, search tweets
- **User Operations**: Get profiles, follow/unfollow users
- **Timeline Access**: Get your timeline and user timelines
- **Direct Messages**: Send DMs, get history, react to messages
- **Trending Topics**: Get trending topics by category

## Key Tools

### Tweet Operations
- `tweet` - Post a new tweet
- `like_tweet` - Like a tweet by ID
- `retweet` - Retweet by ID
- `search_tweets` - Search for tweets

### User Operations  
- `get_user_info` - Get user profile info
- `get_timeline` - Get your timeline

### Direct Messages
- `send_dm` - Send direct message to username
- `get_dm_history` - Get DM history with user
- `add_reaction_to_message` - React with emoji
- `delete_dm` - Delete a message

### Other
- `get_tweet_replies` - Get replies to a tweet
- `get_trends` - Get trending topics

## Example Usage

```
Post a tweet about AI developments

Search for tweets about "artificial intelligence" and show me the top 10

Send a DM to @username saying "Hello from MCP!"

Get my timeline with the latest 20 tweets

Like the tweet with ID 1234567890123456789

Get trending topics in sports

Show me replies to tweet ID 9876543210987654321
```

That's it! All tools require the cookies to be set in your environment variables.
