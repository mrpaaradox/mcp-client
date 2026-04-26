# MCP Client

A client that connects to an MCP server (in a separate repo) and uses Groq's LLM to process queries with tool calls.

## Prerequisites

- Node.js 18+
- pnpm (recommended) or npm

## Setup

1. Install dependencies:

```bash
pnpm install
```

2. Create a `.env` file based on `.env.example`:

```bash
cp .env.example .env
```

3. Add your Groq API key to `.env`:

```
GROQ_API_KEY=your_api_key_here
```

## Building

```bash
pnpm build
```

## Important: Server Path

Before running the client, you need to ensure the server path in the start command points to your server's compiled `dist/index.js`.

The default path is:
```
/Users/aditya/Desktop/Work/Adi/personals/cgs/playground/mcp/server/dist/index.js
```

If your server is in a different location, update the path in `package.json` under the `start` script.

This is required because relative paths are resolved against the current working directory, not the script's location.

### Before You Start

Make sure both repos are built:
1. Build the server: `pnpm build` in the server repo
2. Build the client: `pnpm build` in the client repo

## Running

```bash
pnpm start
```

## Usage

Once running, you'll see the prompt:

```
MCP Client Started!
Type your queries or '/bye' to exit.

Query:
```

Enter your queries. The client will connect to the MCP server, list available tools, and process your queries using Groq's LLM. Type `/bye` to exit.

## Troubleshooting

- **"GROQ_API_KEY is not set"**: Ensure your `.env` file has the `GROQ_API_KEY` variable set
- **"Failed to connect to MCP server"**: Make sure the server repo is built (run `pnpm build` in the server repo first)
- **Path issues**: The server path in `package.json` uses an absolute path — if you move either repo, update the path in the start command