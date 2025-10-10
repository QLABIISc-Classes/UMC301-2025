# ADK Agent MCP Server

This project demonstrates an Agent Development Kit (ADK) agent that interacts with a local SQLite database. The interaction is facilitated by a Model Context Protocol (MCP) server that exposes tools to query and modify the database.

## Project Structure

```
adk-mcp/
├── local_mcp/
│   ├── agent.py             # The ADK agent for the local SQLite DB
│   ├── server.py            # The MCP server exposing database tools
│   ├── create_db.py         # Script to initialize the SQLite database
│   ├── database.db          # The SQLite database file
│   └── __init__.py
├── remote_mcp_agent/        # Example agent for connecting to a remote MCP server
│   ├── agent.py             # The ADK agent configured for a remote MCP
│   └── __init__.py
├── .env                   # For GOOGLE_API_KEY (ensure it's in .gitignore if repo is public)
├── requirements.txt       # Python dependencies
└── readme.md              # This file
```

## Setup Instructions

### 1. Prerequisites
- Python 3.8 or newer
- Access to a terminal or command prompt

### 2. Create and Activate Virtual Environment

It's highly recommended to use a virtual environment to manage project dependencies.

```bash
# Create a virtual environment (e.g., named .venv)
python3 -m venv .venv
```

Activate the virtual environment:

On macOS/Linux:
```bash
# Activate virtual environment
source .venv/bin/activate
```

On Windows:
```bash
# Activate virtual environment
.venv\Scripts\activate
```

### 3. Install Dependencies

Install all required Python packages using pip:

```bash
# Install all dependencies from requirements.txt
pip install -r requirements.txt
```

### 4. Set Up Gemini API Key (for the ADK Agent)

The ADK agent in this project uses a Gemini model. You'll need a Gemini API key.

1.  Create or use an existing [Google AI Studio](https://aistudio.google.com/) account.
2.  Get your Gemini API key from the [API Keys section](https://aistudio.google.com/app/apikeys).
3.  Set the API key as an environment variable. Create a `.env` file in the **root of the `adk-mcp` project** (i.e., next to the `local_mcp` folder and `readme.md`):

    ```env
    # .env
    GOOGLE_API_KEY=your_gemini_api_key_here
    ```
    The `server.py` and `agent.py` will load this key.

### 5. Create the SQLite Database and Tables

The project includes a script to create and populate the SQLite database (`database.db`) with some initial tables (`users`, `todos`) and dummy data.

Navigate to the `local_mcp` directory and run the script:
```bash
cd local_mcp
python3 create_db.py
cd ..
```
This will create `local_mcp/database.db` if it doesn't already exist.

## Running the Agent and MCP Server

The ADK agent (`local_mcp/agent.py`) is configured to automatically start the MCP server (`local_mcp/server.py`) when it initializes its MCP toolset.

To run the agent:

1.  Ensure your virtual environment is active and you are in the root directory of the `adk-mcp` project.
2.  Execute the agent script:

    ```bash
    python3 local_mcp/agent.py
    ```

This will:
- Start the `agent.py` script.
- The agent, upon initializing the `MCPToolset`, will execute the `python3 local_mcp/server.py` command.
- The `server.py` (MCP server) will start and listen for tool calls from the agent via stdio.
- The agent will then be ready to process your instructions (which you would typically provide in a client application or test environment that uses this agent).

You should see log output from both the agent (if any) and the MCP server (in `local_mcp/mcp_server_activity.log`, and potentially to the console if you uncommented the stream handler in `server.py`).
