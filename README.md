<p align="center">
  <img src="https://runikapp.com/runik-mascot.svg" width="80" alt="Runik AI" />
</p>

<h1 align="center">Runik AI - MCP Skills</h1>

<p align="center">
  <strong>Connect ChatGPT, Claude, or any AI assistant to your business data</strong>
</p>

<p align="center">
  <a href="https://runikapp.com">Website</a> |
  <a href="https://runikapp.com/app">Web App</a> |
  <a href="https://github.com/eZhing/runik-desktop">Desktop App</a> |
  <a href="https://smithery.ai/servers/shabit/runik-ai">Smithery</a>
</p>

---

## What is this?

This repository contains the **MCP skill definition** for Runik AI - a remote MCP server that lets AI assistants manage business data through natural language.

Runik AI implements the [Model Context Protocol](https://modelcontextprotocol.io/) (MCP), exposing 40+ tools for creating tables, managing records, building views, running automations, and more.

## Quick Start

### Option 1: Streamable HTTP (recommended)

Connect any MCP client to:

```
https://runikapp.com/mcp
```

Authentication: OAuth 2.1 with PKCE (S256). The server handles Dynamic Client Registration automatically.

### Option 2: SSE (legacy clients)

```
https://runikapp.com/mcp/sse
```

### Option 3: Claude Desktop / Cline

Add to your MCP config:

```json
{
  "mcpServers": {
    "runik-ai": {
      "url": "https://runikapp.com/mcp",
      "transport": "streamable-http"
    }
  }
}
```

### Option 4: Smithery

Install via [Smithery](https://smithery.ai/servers/shabit/runik-ai):

```bash
npx @smithery/cli install @shabit/runik-ai
```

## Available Tools (40+)

### Data Management
| Tool | Description |
|------|-------------|
| `tables_list` | List all tables in your system |
| `table_schema` | Get table structure (columns, types, relations) |
| `table_create` | Create a new table with columns |
| `{table}_list` | List records with filters, search, pagination |
| `{table}_get` | Get a single record by ID |
| `{table}_create` | Create a new record |
| `{table}_update` | Update a record |
| `{table}_delete` | Delete a record |

### Views and Reports
| Tool | Description |
|------|-------------|
| `views_list` | List configured views (kanban, calendar, chart...) |
| `view_create` | Create a new view |

### Templates
| Tool | Description |
|------|-------------|
| `template_list` | List 26 industry templates |
| `template_install` | Install a template with tables, views, and sample data |

### Automations
| Tool | Description |
|------|-------------|
| `automations_list` | List automations |
| `automations_create` | Create an automation (source, process, destination) |
| `automations_run` | Run an automation |

### Integrations
| Tool | Description |
|------|-------------|
| `whatsapp_send` | Send WhatsApp message |
| `telegram_send` | Send Telegram message |
| `discord_send` | Send Discord message |

## Industry Templates

26 ready-to-use templates with tables, views, relations, and sample data:

| Template | Tables | Views | Description |
|----------|--------|-------|-------------|
| CRM Services | 7 | 7 | Clients, opportunities, quotes |
| Real Estate | 9 | 12 | Properties, showings, offers |
| Healthcare | 9 | 7 | Patients, appointments, treatments |
| Dental Clinic | 11 | 11 | Patients, odontogram, treatments |
| Restaurant | 12 | 12 | Tables, orders, menu, inventory |
| Hotel | 9 | 11 | Rooms, bookings, guests |
| School | 16 | 15 | Students, grades, attendance |
| HR | 12 | 13 | Employees, contracts, payroll |
| Dairy Farm | 10 | 8 | Herd, production, breeding, health |
| Beef Cattle | 11 | 8 | Herd, weighing, sales, paddocks |
| Inventory | 5 | 8 | Products, stock, movements |
| Projects | 6 | 8 | Tasks, sprints, team |
| Sales | 11 | 13 | Clients, quotes, invoices |
| Gym / Spa | 8 | 8 | Members, classes, payments |
| And 12 more... | | | |

## Example Conversation

```
User: "I have a restaurant with 15 tables"

Runik: Creates tables for menu items, orders, reservations,
       inventory, suppliers, staff, and cash register.
       Includes sample data and 12 views (floor plan,
       kanban orders, daily sales chart).

User: "What were my sales today?"

Runik: $847,000 CLP across 23 orders. Top item: Lomo saltado (8).
       Average ticket: $36,826.
```

## Security

- OAuth 2.1 with PKCE (S256) - no client secrets
- Per-tenant data isolation (each company has its own database)
- Rate limiting (100 req/min per user)
- Input sanitization and injection detection
- Tool annotations: readOnlyHint, destructiveHint, openWorldHint

## Links

- **Website:** [runikapp.com](https://runikapp.com)
- **Desktop App:** [github.com/eZhing/runik-desktop](https://github.com/eZhing/runik-desktop)
- **Smithery:** [smithery.ai/servers/shabit/runik-ai](https://smithery.ai/servers/shabit/runik-ai)
- **Developers:** [runikapp.com/developers](https://runikapp.com/developers)

## License

[BSL-1.1](../LICENSE) - Business Source License 1.1

---

<p align="center">
  Made from Chile with AI<br/>
  <a href="https://runikapp.com">runikapp.com</a> | <a href="https://allware.cl">Allware SpA</a>
</p>
