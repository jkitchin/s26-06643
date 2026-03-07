# Software Engineering Quick Reference Sheet

A concise reference for essential commands, patterns, and best practices.

---

## 1. Terminal Commands (Terry Terminal)

### Navigation
```bash
pwd                     # Print working directory
ls                      # List files
ls -la                  # List all files with details
cd <path>               # Change directory
cd ..                   # Go up one level
cd ~                    # Go to home directory
```

### File Operations
```bash
cat <file>              # Display file contents
less <file>             # View file with scrolling
head -n 10 <file>       # First 10 lines
tail -n 10 <file>       # Last 10 lines
cp <src> <dst>          # Copy file
mv <src> <dst>          # Move/rename file
rm <file>               # Delete file
rm -r <dir>             # Delete directory (careful!)
mkdir <name>            # Create directory
touch <file>            # Create empty file
```

### Pipes and Redirects
```bash
cmd1 | cmd2             # Pipe: output of cmd1 → input of cmd2
cmd > file              # Redirect output to file (overwrite)
cmd >> file             # Append output to file
cmd 2>&1                # Redirect stderr to stdout
```

### Useful Commands
```bash
grep "pattern" file     # Search for pattern
find . -name "*.py"     # Find files by name
which python            # Show path to executable
echo $PATH              # Show PATH variable
export VAR=value        # Set environment variable
```

---

## 2. Git Commands (Gina Git)

### Daily Workflow
```bash
git status              # See what's changed
git add <file>          # Stage specific file
git add .               # Stage all changes
git commit -m "msg"     # Commit with message
git push                # Push to remote
git pull                # Fetch and merge from remote
```

### Branching
```bash
git branch              # List branches
git branch <name>       # Create branch
git checkout <branch>   # Switch to branch
git checkout -b <name>  # Create and switch
git merge <branch>      # Merge branch into current
git branch -d <name>    # Delete branch
```

### History and Inspection
```bash
git log                 # Commit history
git log --oneline       # Compact history
git log --graph         # Visual branch history
git diff                # Show unstaged changes
git diff --staged       # Show staged changes
git show <hash>         # Show specific commit
```

### Recovery and Undo
```bash
git reflog              # All HEAD movements (safety net!)
git checkout -- <file>  # Discard changes to file
git reset HEAD <file>   # Unstage file
git reset --soft HEAD~1 # Undo commit, keep changes staged
git reset --hard HEAD~1 # Undo commit, discard changes
git revert <hash>       # Create undo commit
git stash               # Temporarily save changes
git stash pop           # Restore stashed changes
```

### Collaboration
```bash
git clone <url>         # Clone repository
git remote -v           # Show remotes
git fetch               # Download without merging
git pull origin main    # Pull specific branch
git push -u origin <br> # Push and set upstream
```

---

## 3. Python Virtual Environments (Vinny Virtual)

### Creating and Activating
```bash
# Create
python -m venv env

# Activate (Unix/Mac)
source env/bin/activate

# Activate (Windows)
env\Scripts\activate

# Deactivate
deactivate
```

### Package Management
```bash
pip install <package>           # Install package
pip install -r requirements.txt # Install from file
pip freeze > requirements.txt   # Export installed packages
pip list                        # List installed packages
pip show <package>              # Package details
pip install -e .                # Install in editable mode
```

---

## 4. Python Packaging

### pyproject.toml Structure
```toml
[build-system]
requires = ["setuptools>=61.0"]
build-backend = "setuptools.build_meta"

[project]
name = "mypackage"
version = "0.1.0"
description = "My package description"
readme = "README.md"
requires-python = ">=3.9"
dependencies = [
    "numpy>=1.20",
    "pandas>=1.3",
]

[project.optional-dependencies]
dev = ["pytest", "black", "ruff"]

[project.scripts]
mycommand = "mypackage.cli:main"
```

### Building and Publishing
```bash
pip install build twine
python -m build                  # Create distribution
twine upload dist/*              # Upload to PyPI
twine upload --repository testpypi dist/*  # Test first
```

---

## 5. Testing with pytest (Tessa Test)

### Running Tests
```bash
pytest                          # Run all tests
pytest -v                       # Verbose output
pytest test_file.py             # Specific file
pytest -k "test_name"           # Match test name
pytest --cov=mypackage          # With coverage
pytest -x                       # Stop on first failure
pytest --pdb                    # Debug on failure
```

### Writing Tests
```python
import pytest

def test_basic():
    assert 1 + 1 == 2

def test_exception():
    with pytest.raises(ValueError):
        raise ValueError("expected")

@pytest.fixture
def sample_data():
    return {"key": "value"}

def test_with_fixture(sample_data):
    assert sample_data["key"] == "value"

@pytest.mark.parametrize("input,expected", [
    (1, 2),
    (2, 4),
    (3, 6),
])
def test_double(input, expected):
    assert input * 2 == expected
```

---

## 6. Code Quality Tools (Rita Readable)

### Formatting and Linting
```bash
# Black (formatter)
black .                         # Format all files
black --check .                 # Check without changing

# Ruff (linter + formatter)
ruff check .                    # Check for issues
ruff check --fix .              # Auto-fix issues
ruff format .                   # Format code

# isort (import sorter)
isort .                         # Sort imports

# mypy (type checker)
mypy mypackage/                 # Check types
```

### Pre-commit Configuration
```yaml
# .pre-commit-config.yaml
repos:
  - repo: https://github.com/astral-sh/ruff-pre-commit
    rev: v0.1.6
    hooks:
      - id: ruff
        args: [--fix]
      - id: ruff-format
  - repo: https://github.com/pre-commit/mirrors-mypy
    rev: v1.7.0
    hooks:
      - id: mypy
```

```bash
pre-commit install              # Set up hooks
pre-commit run --all-files      # Run manually
```

---

## 7. Python Classes (Paula Pattern)

### Basic Class Structure
```python
class Molecule:
    """A chemical molecule."""

    def __init__(self, name: str, formula: str):
        self.name = name
        self.formula = formula

    def __str__(self) -> str:
        return f"{self.name}: {self.formula}"

    def __repr__(self) -> str:
        return f"Molecule({self.name!r}, {self.formula!r})"

    @property
    def mass(self) -> float:
        """Calculate molecular mass."""
        return self._calculate_mass()

    @classmethod
    def from_smiles(cls, smiles: str) -> "Molecule":
        """Create from SMILES string."""
        return cls(smiles, smiles)

    @staticmethod
    def is_valid_formula(formula: str) -> bool:
        """Check if formula is valid."""
        return bool(formula)
```

### Inheritance vs Composition
```python
# Inheritance ("is-a")
class Water(Molecule):
    def __init__(self):
        super().__init__("Water", "H2O")

# Composition ("has-a") - often preferred
class Reaction:
    def __init__(self):
        self.reactants: list[Molecule] = []
        self.products: list[Molecule] = []
```

---

## 8. GitHub Actions (Wendy Workflow)

### Basic Workflow
```yaml
# .github/workflows/tests.yml
name: Tests

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.11'

      - name: Install dependencies
        run: |
          pip install -e ".[dev]"

      - name: Run tests
        run: pytest --cov
```

### Matrix Testing
```yaml
jobs:
  test:
    runs-on: ${{ matrix.os }}
    strategy:
      matrix:
        os: [ubuntu-latest, macos-latest]
        python-version: ['3.9', '3.10', '3.11']

    steps:
      - uses: actions/setup-python@v5
        with:
          python-version: ${{ matrix.python-version }}
```

---

## 9. Documentation (Doc Douglas)

### Docstring Format (Google Style)
```python
def calculate_rate(concentration: float, temperature: float) -> float:
    """Calculate reaction rate using Arrhenius equation.

    Args:
        concentration: Reactant concentration in mol/L.
        temperature: Temperature in Kelvin.

    Returns:
        Reaction rate in mol/(L·s).

    Raises:
        ValueError: If temperature is not positive.

    Example:
        >>> calculate_rate(1.0, 300)
        0.0025
    """
```

### Type Hints
```python
from typing import Optional, Union

def process(
    data: list[float],
    threshold: Optional[float] = None,
) -> dict[str, Union[float, list[float]]]:
    ...
```

---

## 10. API Basics

### HTTP Methods
| Method | Purpose | Example |
|--------|---------|---------|
| GET | Retrieve data | Fetch user info |
| POST | Create resource | Submit new data |
| PUT | Update resource | Modify existing |
| DELETE | Remove resource | Delete item |

### Status Codes
| Code | Meaning |
|------|---------|
| 200 | OK - Success |
| 201 | Created |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 500 | Server Error |

### Python Requests
```python
import requests

# GET
response = requests.get("https://api.example.com/data")
data = response.json()

# POST
response = requests.post(
    "https://api.example.com/items",
    json={"name": "item"},
    headers={"Authorization": "Bearer token"}
)
```

---

## 11. Best Practices Summary

### Code Quality Checklist
- [ ] Code is formatted (Black/Ruff)
- [ ] Linter passes (Ruff/flake8)
- [ ] Type hints present
- [ ] Tests written and passing
- [ ] Docstrings complete
- [ ] README updated

### Git Commit Messages
```
<type>: <subject>

<body>

<footer>
```

Types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`

### Project Structure
```
myproject/
├── src/
│   └── mypackage/
│       ├── __init__.py
│       └── core.py
├── tests/
│   └── test_core.py
├── docs/
├── pyproject.toml
├── README.md
└── .github/
    └── workflows/
        └── tests.yml
```

---

## 12. Common Mistakes to Avoid

| Mistake | Better Approach |
|---------|-----------------|
| No virtual environment | Always use venv or conda |
| Committing secrets | Use .gitignore, env vars |
| No tests | Write tests as you code |
| Giant commits | Small, focused commits |
| Unclear names | Descriptive variable names |
| Copy-paste code | Extract to functions |
| No documentation | Document as you go |
| Force push to main | Use PRs and reviews |

---

*"Make it work, make it right, make it fast—in that order." - Kent Beck*
