# Music Bot

This bot helps you discover new music from your favorite singers and manage your listening history.

## Commands

- `/start`: Starts the bot and displays a welcome message.
- `/cancel`: Cancels the current operation.
- `/delete_history`: Deletes your listening history.

## Features

### Manage Preferred Singers

- **Add Singer**: Add a singer to your preferred list.
- **Delete Singer**: Remove a singer from your preferred list.
- **View Singers**: See your list of preferred singers.
- **Clear Singers**: Remove all singers from your preferred list.

The bot uses the `thefuzz` library for flexible singer name matching, so you don't have to worry about exact spelling.

### Fetch New Music

- Get notified about new releases from your preferred singers.

### Manage Listening History

- Keep track of the music you've listened to.
- Delete your listening history if needed.

## Running the Bot

### 1. Local Setup (Python Virtual Environment)

1.  **Create and activate a virtual environment:**
    ```bash
    python3 -m venv venv && source venv/bin/activate
    ```
    *(On Windows, use `venv\Scripts\activate`)*

2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Install Playwright browsers:**
    ```bash
    python -m playwright install --with-deps chromium
    ```

4.  **Set Environment Variables:**
    Set the `PORT` for the application:
    ```bash
    export PORT=8080
    ```
    Set your Telegram Bot Token. **Note:** The actual environment variable name for the token (e.g., `TELEGRAM_BOT_TOKEN`, `BOT_TOKEN`) might be different. Please check your bot's configuration file (e.g., `config.py`, `main.py`, or `.env` file instructions) for the correct variable name.
    ```bash
    export TELEGRAM_BOT_TOKEN='YOUR_TOKEN_HERE'
    ```

5.  **Run the bot:**
    The bot is typically run using Uvicorn.
    ```bash
    uvicorn main:create_starlette_app --host 0.0.0.0 --port $PORT --factory --workers 1
    ```

### 2. Docker Setup

1.  **Build the Docker image:**
    ```bash
    docker build -t music_bot .
    ```

2.  **Run the Docker container:**
    Remember to replace `8080` if you are using a different port and `'YOUR_TOKEN_HERE'` with your actual Telegram Bot Token. **Note:** The actual environment variable name for the token (e.g., `TELEGRAM_BOT_TOKEN`, `BOT_TOKEN`) might be different. Please check your bot's configuration file (e.g., `config.py`, `main.py`, or Dockerfile instructions) for the correct variable name.
    ```bash
    docker run -e PORT=8080 -e TELEGRAM_BOT_TOKEN='YOUR_TOKEN_HERE' -p 8080:8080 music_bot
    ```
