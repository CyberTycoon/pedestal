# 🪨 Plinth

> A high-performance, developer-first CLI scaffolding tool for FastAPI

## Overview

Plinth is a dynamic CLI scaffolding engine for FastAPI that provides a rock-solid foundation for modern web APIs. Unlike static boilerplates, Plinth generates code based on your specific needs and allows you to evolve your project over time.

## Features

- 🚀 **Fast Project Initialization** - Create a new FastAPI project in seconds
- 🔧 **Modular Architecture** - Add features (Auth, Redis, Database) as needed
- 📝 **Type-Safe** - Built with Pydantic and Typer
- 🎨 **Beautiful CLI** - Rich terminal output with progress bars
- 🔒 **Safe Code Injection** - LibCST ensures safe AST modifications
- 📦 **uv Integration** - Native support for fast Python package management

## Installation

### From Source

```bash
# Clone the repository
git clone <repository-url>
cd plinth

# Install dependencies
pip install -r requirements.txt

# Install in development mode
pip install -e .
```

### Using pip

```bash
pip install plinth
```

## Quick Start

### Create a Basic Project

```bash
plinth init my-app
cd my-app
uv run uvicorn src.main:app --reload
```

### Create with Database

```bash
plinth init my-api --db postgres --auth jwt --redis
```

### Add Features Later

```bash
cd my-api

# Add Redis caching
plinth add redis

# Add JWT authentication
plinth add auth-jwt
```

## Commands

| Command                  | Description                          |
| ------------------------ | ------------------------------------ |
| `plinth init <name>`     | Initialize a new FastAPI project     |
| `plinth add <module>`    | Add a feature module                 |
| `plinth remove <module>` | Remove a feature module              |
| `plinth list`            | List installed and available modules |
| `plinth doctor`          | Run diagnostics on the project       |

## Available Modules

- **postgres** - PostgreSQL database with asyncpg driver
- **mysql** - MySQL database with aiomysql driver
- **sqlite** - SQLite database with aiosqlite driver
- **redis** - Redis caching and session storage
- **auth-jwt** - JWT-based authentication
- **auth-session** - Session-based authentication

## Project Structure

```
my-app/
├── .plinth.json          # State tracking
├── pyproject.toml        # Dependencies
├── src/
│   ├── main.py          # FastAPI entry point
│   ├── core/
│   │   ├── config.py    # Settings
│   │   └── registry.py  # Router registry
│   └── api/
│       └── v1/
│           └── health.py
└── tests/
```

## Development

### Running Tests

```bash
pytest
```

### Code Quality

```bash
# Format code
ruff format .

# Lint code
ruff check .

# Type check
mypy src/
```

## Documentation

See the [complete guide](docs/plinth-complete-guide.md) for detailed documentation.

## License

MIT License
