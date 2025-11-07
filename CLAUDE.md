# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

**Project Setup**: See `.project-info` for project metadata configuration.

Edit `.project-info` to customize:
- `PROJECT_NAME`: Your project name
- `PROJECT_DESCRIPTION`: Project description
- `PROJECT_VERSION`: Semantic version
- `BACKEND_FRAMEWORK`: Backend framework (FastAPI, Django, etc.)
- `PYTHON_VERSION`: Python version (3.11+)
- `DATABASE_TYPE`: Database (PostgreSQL, MySQL, SQLite, etc.)

## Tech Stack

- **Backend**: FastAPI (Python 3.11+)
- **Database**: PostgreSQL + Alembic (migrations)
- **Package Manager**: uv
- **Testing**: pytest
- **Code Quality**: ruff, black, mypy (strict), pylint

## Development

### Quick Start (3 Commands)

```bash
./tools/dev.sh up              # Start dev server (localhost:8000)
./tools/dev.sh test            # Run tests
./tools/dev.sh format          # Format + lint code
```

### Common Commands

```bash
./tools/dev.sh shell           # Enter project shell
./tools/dev.sh help            # Show all commands

tox -e py311                   # Test on Python 3.11
tox -e style                   # Full format/lint pipeline
```

## Testing

```bash
pytest                         # Run all tests
pytest -k <name>              # Run specific test
pytest -v                      # Verbose output
tox -e py310 py311 py312      # Test multiple versions
```

## Code Quality (Before Commit)

- [ ] `./tools/dev.sh format` passes (ruff, black, mypy, pylint)
- [ ] `./tools/dev.sh test` passes
- [ ] Type hints on all functions (mypy strict mode)
- [ ] Docstrings on public functions
- [ ] Line length ≤ 120 chars

## Git Workflow

```bash
./tools/commit.sh              # Interactive commit (Conventional Commits)
./tools/release.sh patch|minor|major  # Release & tag
```

**Commit types**: feat, fix, chore, refactor, test, docs
**Branch format**: `feature/name`, `fix/name`, `hotfix/name`

## Architecture

Update this section in CLAUDE.md with your project architecture:

```text
[Example]
Frontend ↔ Backend (FastAPI) ↔ PostgreSQL

Key Components:
- Authentication: TBD
- Core Features: TBD
- External Services: TBD
```

**See `docs/ARCHITECTURE.md` for detailed design.**

### Key Files

| Path | Purpose |
|------|---------|
| `src/backend/` | Backend application code (TBD) |
| `src/frontend/` | Frontend application code (TBD) |
| `tests/` | pytest test suite |
| `docs/` | Documentation and architecture |
| `alembic/` | Database migrations (if using SQL) |

## Data Schema

Update this section with your project's data model:

**Key Entities** (TBD):

```sql
-- Define your database schema here
-- Use alembic for migrations
```

**See `docs/FEATURE_REQUIREMENTS.md` for detailed requirements.**

## Conventions

**Variable Naming**: snake_case (Python)
**Constants**: UPPER_SNAKE_CASE
**Functions**: verb_noun (e.g., `get_user`, `create_session`)
**Classes**: PascalCase
**Async**: Prefix with `a_` if async function

## Troubleshooting

**Type errors?** Run `tox -e mypy` (strict mode enforced)
**Import errors?** Run `tox -e ruff` then `./tools/dev.sh format`
**DB issues?** Check `alembic/versions/` for migrations, then `./tools/dev.sh up`

## Further Reading

- **Feature Requirements**: `docs/FEATURE_REQUIREMENTS.md` (edit with your project specs)
- **Architecture**: `docs/ARCHITECTURE.md` (edit with your project design)
- **Development Progress**: `docs/DEV-PROGRESS.md` (auto-updated by team)
- **Contributing**: See git flow above + code quality rules

---

## REQ-Based Development Workflow

**When to use**: Each feature request follows format: `"REQ-<ID> <description>"` (implement REQ with ID)

### Command Format
```
User: "REQ-A1-Login 기능 구현해"
Assistant: (Automatically follows 4-phase workflow below)
```

### Phase 1️⃣: SPECIFICATION (Parse & Pause for Review)
```
- Extract REQ ID, requirement, priority, acceptance criteria from docs/FEATURE_REQUIREMENTS.md
- Summarize: intent, constraints, performance goals
- Define: Location (module path), Signature (types, I/O, side effects),
  Behavior (logic, validation), Dependencies, Non-functional (perf/security)
- 🛑 PAUSE: Present spec, ask "Approved? Continue to Phase 2?"
```

### Phase 2️⃣: TEST DESIGN (TDD Before Code)
```
- Create: tests/<domain>/test_<feature>.py
- Design 4-5 test cases:
  ✓ Happy path (valid inputs)
  ✓ Input validation errors
  ✓ Edge cases (DB, timeout, concurrency)
  ✓ Acceptance criteria verification
- Include REQ ID in docstrings: # REQ: REQ-A1-Login
- 🛑 PAUSE: Present test list, ask "Tests approved? Continue to Phase 3?"
```

### Phase 3️⃣: IMPLEMENTATION (Code to Spec)
```
- Write minimal code satisfying spec + tests
- Follow SOLID + conventions from above
- Run: tox -e style && pytest tests/<domain>/test_<feature>.py
- 🛑 STOP if validation fails; report errors
```

### Phase 4️⃣: SUMMARY (Report & Commit)
```
- Modified files + rationale
- Test results (all pass)
- Traceability: REQ → Spec → Tests → Code
- Create git commit: ./tools/commit.sh
```

**Key Principle**: Phase 1-2 pause for review = prevent rework. Spec must be approved before coding.

---

**Forcing Function Principle**: 3-4 intuitive commands (dev.sh, commit.sh, tox) reduce learning curve & execution variance.
