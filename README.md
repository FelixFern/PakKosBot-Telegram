# PakKosBot-Telegram

**PakKosBot** is an intelligent Telegram bot designed to manage boarding house (Kost-kosan) operations. It acts as a virtual "Bapak Kos" (Landlord), assisting tenants and prospective residents with information, complaints, and transactions.

The bot utilizes Large Language Models (LLMs) to provide natural language interactions and integrates with various services for a seamless management experience.

## Features

- **Intelligent Q&A**: Answers questions about boarding house rules, facilities, and FAQs using AI (RAG with LangChain & OpenAI).
- **Room Availability**: Checks real-time availability of rooms.
- **Complaint Handling**: Allows tenants to submit complaints regarding facilities or services.
- **Transaction Management**: Handles payments for rent, deposits, and bills via **Midtrans** integration.
- **Data Management**: Uses **Google Sheets** and **PostgreSQL/SQLite** for managing guest and room data.

## Tech Stack

- **Language**: Python 3.10+
- **Framework**: [FastAPI](https://fastapi.tiangolo.com/) (API) & [python-telegram-bot](https://python-telegram-bot.org/)
- **AI & LLM**: [LangChain](https://langchain.com/) & [OpenAI GPT-4](https://openai.com/)
- **Vector Database**: [ChromaDB](https://www.trychroma.com/) (for RAG)
- **Database**: SQLite / PostgreSQL (via AsyncPG)
- **Integrations**:
  - [Midtrans](https://midtrans.com/) (Payment Gateway)
  - Google Sheets API (Data Sync)

## Getting Started

### Prerequisites

- Python 3.10 or higher
- A Telegram Bot Token (from [@BotFather](https://t.me/BotFather))
- OpenAI API Key
- Midtrans Server Key (Sandbox/Production)
- Google Service Account Credentials (JSON)

### Installation

1.  **Clone the repository**

    ```bash
    git clone https://github.com/yourusername/PakKosBot-Telegram.git
    cd PakKosBot-Telegram
    ```

2.  **Create a virtual environment**

    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```

3.  **Install dependencies**
    ```bash
    pip install -r requirements.txt
    ```

### Configuration

1.  Copy the example environment file:

    ```bash
    cp .env.example .env
    ```

2.  Fill in the required environment variables in `.env`:

    ```env
    # AI Configuration
    OPENAI_API_KEY=your_openai_api_key

    # Database
    DATABASE_URL=sqlite:///./database/guest_rooms.db # or your postgres url

    # Telegram
    TELEGRAM_BOT_TOKEN=your_telegram_bot_token

    # API Server
    API_PORT=8000
    API_HOST=0.0.0.0

    # Google Sheets Integration
    SHEETS_SERVICE_ACCOUNT_PROJECT_ID=...
    SHEETS_SERVICE_ACCOUNT_PRIVATE_KEY_ID=...
    SHEETS_SERVICE_ACCOUNT_PRIVATE_KEY=...
    SHEETS_SERVICE_ACCOUNT_CLIENT_ID=...
    SHEETS_SERVICE_ACCOUNT_CLIENT_EMAIL=...

    # Payment Gateway
    MIDTRANS_SERVER_KEY=your_midtrans_server_key
    ```

### ▶️ Running the Bot

The application runs both a FastAPI server and the Telegram Bot poller concurrently.

```bash
python app.py
```

The bot should now be online on Telegram, and the API accessible at `http://localhost:8000`.

## Project Structure

- `agents/`: Logic for different AI agents (Complaint, DB, QA, Transaction).
- `bot/`: Telegram bot handlers and configuration.
- `database/`: Database connection and schema handling.
- `midtrans/`: Payment gateway integration logic.
- `tools/`: Helper tools used by the agents.
- `utils/`: General utility functions and loggers.
- `app.py`: Main entry point for the application.

## License

[MIT](LICENSE)
