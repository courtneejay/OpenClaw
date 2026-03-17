---
name: telegram-md-uploader
description: Uploads and sends .md files from your OpenClaw workspace to a specific Telegram chat using the Telegram Bot API. Use when you need to share workspace files (e.g., drafts, code, content) with a Telegram recipient.
---

# Telegram MD Uploader

This skill enables you to send markdown files directly from your workspace to a Telegram chat.

## Prerequisites

1.  **Telegram Bot Token**: You need a bot token from [@BotFather](https://t.me/BotFather).
2.  **Chat ID**: You need the Chat ID for the recipient (the bot must be a member of the chat).

## Setup & Usage

### 1. Configure the Alias (Recommended)
To avoid typing the full file path every time, add this alias to your shell profile (e.g., `.bashrc` or `.zshrc`):

```bash
alias tg-upload='python3 /root/.openclaw/workspace/skills/telegram-md-uploader/scripts/upload.py'
```

*Note: If you move the skill folder, update the path in the alias accordingly.*

### 2. Usage
Once the alias is set, run the following command in your terminal:

```bash
tg-upload <file_path.md> --token <bot_token> --chat-id <chat_id>
```

### Direct Execution
If you prefer not to use an alias, run the script directly:

```bash
python3 scripts/upload.py <file_path.md> --token <bot_token> --chat-id <chat_id>
```

## How It Works

This skill utilizes the Telegram Bot API `sendDocument` method. It takes the file path, validates that it is a `.md` file, wraps it in a POST request with `multipart/form-data`, and sends it to your specified chat.

## Troubleshooting

- **Error 401**: Ensure your Bot Token is correct.
- **Error 400**: The Chat ID might be incorrect or the bot is not in the chat.
- **Error: File not found**: Double-check the file path.
- **Error: Not a valid .md file**: Ensure the file ends with the `.md` extension.
