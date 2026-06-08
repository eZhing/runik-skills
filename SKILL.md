---
name: runik-business-management
description: Manage business data through natural language. Query clients, create records, view dashboards, generate reports, and automate tasks using 40+ MCP tools across 26 industry templates.
---

# Runik AI — Business Management Skill

## Purpose
Manage business data through natural language. Query clients, create records, view dashboards, generate reports, and automate tasks using Runik AI's MCP tools.

## Available Operations

### Query Data
- **List records**: `tables_list`, `{table}_list` — List all tables or records in a specific table with filters, search, sort, and pagination.
- **Get record**: `{table}_get` — Retrieve a single record by ID.
- **Table schema**: `table_schema` — View the structure and columns of any table.
- **Table relations**: `table_relations` — Get 1-to-many relationships between tables.

### Create & Modify Data
- **Create record**: `{table}_create` — Create a new record with provided data.
- **Update record**: `{table}_update` — Update an existing record by ID.
- **Delete record**: `{table}_delete` — Delete a record. Supports cascade for related records.

### System Management
- **Create table**: `table_create` — Create a new table with columns.
- **Add/remove columns**: `table_add_column`, `table_remove_column` — Modify table structure.
- **Install template**: `template_install` — Install an industry template (CRM, restaurant, hotel, clinic, etc.).
- **Views**: `view_create`, `view_update`, `view_delete` — Manage saved views (kanban, calendar, pipeline, etc.).
- **Modules**: `module_assign`, `modules_meta_set` — Organize tables into modules.

### Automations
- **Manage automations**: `automations_create`, `automations_update`, `automations_delete` — Create and manage Pilo automations.
- **Run automation**: `automations_run` — Execute an automation (preview by default).
- **View history**: `automations_log` — See execution history.

## Usage Examples

### Business Overview
```
User: "How is my business doing this month?"
Claude: Uses tables_list to discover tables, then queries sales, clients,
        and tasks to provide a comprehensive business summary.
```

### Query with Filters
```
User: "Show me clients from Santiago with deals over $100,000"
Claude: Calls clients_list with search/filter parameters to find matching records.
```

### Create a Record
```
User: "Create a new client: Acme Corp, contact@acme.com, Santiago"
Claude: Calls clients_create with {data: {name: "Acme Corp", email: "contact@acme.com", city: "Santiago"}}
```

### Setup a New Business
```
User: "I run a dental clinic and need to manage patients and appointments"
Claude: Calls template_install with {id: "crm_salud"} to install the healthcare template
        with patients, appointments, treatments, and sample data.
```

### Generate Reports
```
User: "Sales report for Q1 grouped by salesperson"
Claude: Queries deals/sales data, aggregates by salesperson, and presents a formatted report.
```

## Parameters

### Common list parameters
| Parameter | Type | Description |
|-----------|------|-------------|
| `filters` | object | Key-value filters (e.g., `{status: "active"}`) |
| `search` | string | Full-text search across all columns |
| `sort` | string | Column name to sort by |
| `sort_dir` | string | `asc` or `desc` |
| `limit` | number | Max records to return |
| `offset` | number | Pagination offset |

### Create/Update parameters
| Parameter | Type | Description |
|-----------|------|-------------|
| `data` | object | Key-value pairs matching table columns |
| `id` | number | Record ID (required for update/delete) |
| `cascade` | boolean | Delete related child records (for delete) |

## Best Practices

1. **Always call `tables_list` first** to discover what tables exist in the user's business.
2. **Use `table_schema`** to understand column names and types before querying.
3. **Use filters and search** instead of listing all records — keep responses relevant.
4. **For new users**, suggest `template_install` to get started quickly with sample data.
5. **When creating records**, ask for confirmation before writing data.
6. **For delete operations**, warn the user about cascade effects on related records.

## Available Templates (24)
CRM Services, Sales/Billing, Inventory, Projects, HR, Restaurant, Hotel, Clinic, Real Estate, Retail, Workshop, Gym, Purchasing, Tutoring, Event Venue, Coworking, Parking, Personal Tasks, Personal Finance, and more.

## Notes
- Each company has its own isolated database — data never crosses between companies.
- Tables are dynamic — users can create custom tables for any business type.
- All tools support English, Spanish, and French.
