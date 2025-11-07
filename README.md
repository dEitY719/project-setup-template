# Project Setup Template

**[Project Name]**: Edit this with your project name (see `.project-info`)

This is a template repository for rapid project setup with pre-configured development workflows and development infrastructure.

---

## 🚀 Quick Start

### 1. Prerequisites

- **Claude Code CLI**: Install from https://docs.claude.com/en/docs/claude-code/getting-started
- **Python 3.11+**: Required for development
- **uv**: Python package manager (automatically installed via dev.sh)

### 2. Project Setup

```bash
# Clone the repository
git clone <repo-url>
cd <project-name>

# Configure project metadata (REQUIRED)
# Edit .project-info with your project details:
nano .project-info

# Key settings to customize:
# - PROJECT_NAME: Your project name
# - PROJECT_DESCRIPTION: Project description
# - DATABASE_TYPE: PostgreSQL / MySQL / SQLite
# - PYTHON_VERSION: 3.11 (or your target version)
```

### 3. Start Development

```bash
# First run - install dependencies + start dev server
./tools/dev.sh up              # Start dev server (localhost:8000)

# In another terminal
./tools/dev.sh test            # Run tests
./tools/dev.sh format          # Format + lint code
```

### 4. REQ-Based Development (Recommended Workflow)

**1-line feature requests using Claude Code:**

```bash
# Start Claude Code CLI
claude

# At the prompt, request a feature:
> REQ-A1-Login 기능 구현해

# Automatic workflow:
# Phase 1: Specification (spec review) → Your approval
# Phase 2: Test Design (test review) → Your approval
# Phase 3: Implementation (code) + validation
# Phase 4: Summary (report) + git commit
```

See `CLAUDE.md` → "REQ-Based Development Workflow" for details.

---

## 📋 Development Process

### REQ-Based Development

All features are developed using Requirement IDs (REQ) defined in `docs/FEATURE_REQUIREMENTS.md`.

**Request Format:**
```
REQ-[Domain]-[Feature] 기능 구현해
```

**Examples:**
```
REQ-A1-Login 기능 구현해           # Login feature
REQ-A2-Dashboard 기능 구현해       # Dashboard feature
REQ-B1-DataModel 기능 구현해       # Data model feature
```

### Development Progress Tracking

Each REQ development is tracked in `docs/progress/` automatically:

```
docs/
└── progress/
    ├── REQ-A1-Login.md           # In progress
    ├── REQ-A2-Dashboard.md       # Completed
    └── ...
```

Overall team progress is tracked in `docs/DEV-PROGRESS.md`.

---

## 📚 Project Features

Edit this section with your project's main features:

**Core Components** (TBD):
- [Feature 1]: Description
- [Feature 2]: Description
- [Feature 3]: Description

---

## 📖 Documentation

- **Development Guide**: [`CLAUDE.md`](CLAUDE.md) - Development rules, conventions, REQ workflow
- **Feature Requirements**: [`docs/FEATURE_REQUIREMENTS.md`](docs/FEATURE_REQUIREMENTS.md) - Edit with your feature specs
- **Architecture**: [`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md) - Edit with your system design
- **Development Progress**: [`docs/DEV-PROGRESS.md`](docs/DEV-PROGRESS.md) - Team progress tracking
- **Project Info**: [`.project-info`](.project-info) - Project metadata configuration

---

## 🛠️ Tech Stack

**Core Stack** (configure in `.project-info`):

- **Backend Framework**: FastAPI (customizable)
- **Python Version**: 3.11+ (customizable)
- **Database**: PostgreSQL / MySQL / SQLite (customizable)
- **Package Manager**: uv
- **Testing**: pytest
- **Code Quality**: ruff, black, mypy (strict mode), pylint
- **Migrations**: Alembic (if using SQL database)

---

## 💬 Development Guidelines

All development follows conventions defined in `CLAUDE.md`:

- **Type Hints**: Required on all public functions
- **Docstrings**: Google-style docstrings
- **Line Length**: ≤ 120 characters
- **Testing**: TDD (Test-Driven Development) - Phase 2 before Phase 3
- **Commits**: Conventional Commits format (`feat:`, `fix:`, `test:`, etc.)
- **Code Quality**: Pass `tox -e style` before commit

---

## 🤝 Contributing

Contributions are welcome! Follow this workflow:

**How to Contribute:**
1. Clone or fork the repository
2. Edit `.project-info` with your project metadata (REQUIRED)
3. Configure `docs/FEATURE_REQUIREMENTS.md` with your feature specs
4. Implement features using: `claude` → `REQ-<ID> 기능 구현해`
5. Follow the 4-phase workflow: Spec → Test Design → Implementation → Summary
6. Push and open a Pull Request

See `CLAUDE.md` for detailed REQ workflow.

---

## 📝 License

[MIT License](LICENSE)
