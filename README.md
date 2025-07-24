# Twitter MCP Server

A Model Context Protocol (MCP) server for Twitter integration using cookie-based authentication. Allows AI assistants to interact with Twitter through a standardized protocol.

## ⚠️ Disclaimer

This uses an **unofficial Twitter API** via the `twikit` library. Not endorsed by Twitter/X and may break without notice. Use for educational/experimental purposes only. Account restrictions possible.

## Quick Setup

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

```json
// Post a tweet
{
  "tool": "tweet",
  "arguments": {
    "text": "Hello from MCP! 🚀"
  }
}

// Search tweets
{
  "tool": "search_tweets", 
  "arguments": {
    "query": "artificial intelligence",
    "count": 10
  }
}

// Send DM
{
  "tool": "send_dm",
  "arguments": {
    "recipient_username": "username",
    "text": "Hello!"
  }
}
```

That's it! All tools require the cookies to be set in your environment variables.
