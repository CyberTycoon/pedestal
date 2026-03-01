# 🪨 Plinth

> Stop building the "basement" of your FastAPI project.

## The Problem

Every new FastAPI project starts with the same 2-hour slog:

- Wiring up SQLAlchemy with async drivers
- Setting up config management
- Creating folder structures that won't become a mess
- Adding auth... then rewriting it when you change your mind

**Boilerplate burnout is real.**

## The Solution

Plinth scaffolds production-ready FastAPI projects in **2 seconds**, then lets you add features incrementally without breaking your code.

```bash
# Start with exactly what you need
plinth init my-api --db postgres --auth jwt

# Change your mind later? No problem.
plinth add redis
plinth add auth-session
```

## Why Plinth?

| Without Plinth                                | With Plinth                                    |
| --------------------------------------------- | ---------------------------------------------- |
| Copy-paste boilerplate from old projects      | Generate clean, consistent structure instantly |
| Fear of adding features mid-project           | Add/remove modules anytime safely              |
| Hope your code injection doesn't break things | AST-aware code modifications (LibCST)          |
| Spend hours on setup                          | Spend hours on **features**                    |

## Installation

```bash
pip install plinth-cli
```

> **Note:** Package is `plinth-cli` on PyPI, command is `plinth`.

## 10-Seconds to Production

```bash
# Create project
plinth init my-app --db postgres

# Run it
cd my-app
uv run uvicorn src.main:app --reload

# Open http://localhost:8000/docs
```

## Commands

| Command                  | What it does                        |
| ------------------------ | ----------------------------------- |
| `plinth init <name>`     | Scaffold new project with options   |
| `plinth add <module>`    | Add feature (redis, auth-jwt, etc.) |
| `plinth remove <module>` | Remove feature cleanly              |
| `plinth list`            | See installed/available modules     |
| `plinth doctor`          | Check project health                |

## Available Modules

- **postgres/mysql/sqlite** - Database with async drivers
- **redis** - Caching & sessions
- **auth-jwt** - JWT authentication
- **auth-session** - Session-based auth

## How It Works

Plinth doesn't just copy files—it **understands** your Python code using AST manipulation. When you run `plinth add redis`, it:

1. Injects Redis connection code into your main app
2. Updates `.env` with Redis URL
3. Adds dependencies to `pyproject.toml`
4. Registers routes without touching your custom code

Your project stays clean, typed, and maintainable.

## Project Structure

```
my-app/
├── .plinth.json          # Tracks installed modules
├── pyproject.toml        # Dependencies
├── src/
│   ├── main.py          # FastAPI entry
│   ├── core/
│   │   ├── config.py    # Pydantic settings
│   │   └── registry.py  # Auto-router registration
│   └── api/
│       └── v1/
└── tests/
```

## Documentation

- [Complete User Guide](docs/plinth-complete-guide.md)
- [Developer Guide](docs/developer-guide.md)

## License

MIT License
