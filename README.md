# Starter

A simple starter template for Python projects.

## Requirements

- Python >= 3.13

## Quick Start

### Installation

```bash
# Install dependencies and set up the project
uv sync
uv run poe setup
source .venv/bin/activate
```

### Running the Project

```bash
# Run the main application
poe dev

# Or use the installed command
starter
```

## Development

### Available Tasks

Use `poe` (poethepoet) to run predefined tasks:

```bash
# Format code with ruff
poe format

# Run linter with auto-fix
poe lint

# Run type checking
poe type

# Run all checks (format, lint, type)
poe check

# Build the package
poe build

# Create a new version tag
poe tag
```

### Development Dependencies

- **commitizen**: Semantic versioning and changelog management
- **poethepoet**: Task runner for predefined scripts
- **pre-commit**: Git hooks framework
- **ruff**: Fast Python linter and formatter
- **ty**: Type checker for Python

### Project Structure

```
starter-python/
├── src/
│   └── starter/
│       ├── __init__.py
│       └── main.py
├── pyproject.toml
├── README.md
└── uv.lock
```

## Configuration

### Type Checking

Type checking is configured in `pyproject.toml`:

```toml
[tool.ty.src]
include = ["src"]
```

### Code Style

- **Line Length**: 99 characters
- **Linter Rules**: Includes pyflakes, pycodestyle, isort, pep8-naming, and more
- **Formatter**: ruff format

### Commit Convention

Uses Conventional Commits with commitizen:
- Format: `type(scope): message`
- Examples: `feat(core): add new feature`, `fix(api): resolve issue`

## Building

```bash
poe build
```

This creates a wheel file in the `dist/` directory.
