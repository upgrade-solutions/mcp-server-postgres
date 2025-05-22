# mcp-postgres
An example application for connecting to a Postgres database using MCP.

## Quick Start

```bash
# Install dependencies
npm install
```

Note: This example is slightly adapted from the public [MCP Postgres docs](https://github.com/modelcontextprotocol/servers/tree/main/src/postgres). 

> A Model Context Protocol server that provides read-only access to PostgreSQL databases. This server enables LLMs to inspect database schemas and execute read-only queries.

## Tools
* query
  * Execute read-only SQL queries against the connected database
  * Input: `sql (string)`: The SQL query to execute
  * All queries are executed within a READ ONLY transaction

## Resources
The server provides schema information for each table in the database:

* Table Schemas (`postgres://<host>/<table>/schema`)
  * JSON schema information for each table
  * Includes column names and data types
  * Automatically discovered from database metadata

## Usage with Claude Desktop
To use this server with the Claude Desktop app, add the following configuration to the "mcpServers" section of your `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "postgres": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-postgres",
        "postgres://<host>/<table>/schema"
      ]
    }
  }
}
```

## License
This MCP server is licensed under the MIT License. This means you are free to use, modify, and distribute the software, subject to the terms and conditions of the MIT License. For more details, please see the LICENSE file in the project repository.