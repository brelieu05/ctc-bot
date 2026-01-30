# ctc-bot ⚡️ Bolt for Python

> Slack bot for UCI campus: share where you're studying and see who else is studying for a set duration.

## Overview

This is a Slack app built with [Bolt for Python](https://docs.slack.dev/tools/bolt-python/) that lets users:

- **Share their study location** — `/study` opens a modal to pick a UCI location (Langson, Science Library, Gateway, etc.) and specific spot. The bot announces it to a channel for that duration.

Sessions are stored in memory and expire automatically after the chosen duration.

## Running locally

### 1. Setup environment variables

Use a `.env` file or export:

```zsh
# Required: from your Slack app (OAuth & Permissions → Bot User OAuth Token, Basic Information → App-Level Tokens)
SLACK_BOT_TOKEN=xoxb-...
SLACK_APP_TOKEN=xapp-...

# Optional: channel where study announcements are posted (channel ID, e.g. C01234ABCD). If unset, the bot DMs you to confirm and asks you to set it.
STUDY_CHANNEL_ID=C01234ABCD
```

To get a channel ID: right-click the channel in Slack → "View channel details" → copy the ID at the bottom.

### 2. Setup your local project

```zsh
# Clone this project onto your machine
git clone <your-repo-url>

# Change into this project
cd ctc-bot/

# Setup virtual environment
python3 -m venv .venv
source .venv/bin/activate

# Install the dependencies
pip install -r requirements.txt
```

### 3. Register slash commands in Slack

In [Slack API](https://api.slack.com/apps) → your app → **Slash Commands**:

| Command   | Short Description        |
|----------|---------------------------|
| `/study` | Share where you're studying |

Use **Request URL** only if you're on HTTP (not Socket Mode); with Socket Mode you can leave it blank for these.

### 4. Start the app

```zsh
python3 app.py
```

**Run with auto-reload (restarts on code changes):**

```zsh
pip install -r requirements.txt   # installs watchdog
watchmedo auto-restart --directory . --patterns "*.py" --recursive -- python3 app.py
```

Or use the helper script:

```zsh
./run_dev.sh
```

## Usage

- **`/study`** — Opens a modal: choose a UCI location, optional specific spot, and duration. Submitting posts an announcement to `STUDY_CHANNEL_ID` (or DMs you if not set) and adds you to the active list until the duration ends.

## More examples

Looking for more examples of Bolt for Python? Browse to [bolt-python/examples/](https://github.com/slackapi/bolt-python/tree/main/examples) for a long list of usage, server, and deployment code samples!

## Contributing

### Issues and questions

Found a bug or have a question about this project? We'd love to hear from you!

1. Browse to [slackapi/bolt-python/issues](https://github.com/slackapi/bolt-python/issues/new/choose)
1. Create a new issue
1. Mention that you're using this example app

See you there and thanks for helping to improve Bolt for everyone!
