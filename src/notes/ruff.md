`ruff check .` - Check all Python files in current directory for linting issues.
`ruff check --fix .` - Check and automatically fix linting issues.
`ruff format .` - Format all Python files in current directory.
`ruff format --check .` - Check formatting without modifying files.
`ruff check script.py` - Check a specific file for issues.
`ruff format script.py` - Format a specific file.
`ruff rule E501` - Show details about a specific rule.
`ruff rule` - List all available rules.
`ruff config` - Display current configuration.
`ruff version` - Show ruff version.

# Details
## Linting
`ruff check .` - Check all files in current directory.
`ruff check script.py` - Check a specific file.
`ruff check src/` - Check all files in a directory recursively.
`ruff check --fix .` - Fix all fixable linting issues automatically.
`ruff check --fix --unsafe .` - Fix all issues including unsafe fixes.
`ruff check --select E501` - Check only specific rule (E501: line too long).
`ruff check --ignore E501 .` - Ignore specific rule during check.
`ruff check --show-settings` - Display active linting rules.
`ruff check --show-files` - List files being checked.

## Formatting
`ruff format .` - Format all files in current directory.
`ruff format script.py` - Format a specific file.
`ruff format src/` - Format all files in a directory recursively.
`ruff format --check .` - Check if formatting is needed without changing files.
`ruff format --diff .` - Show what formatting changes would be made.
`ruff format --line-length 100 .` - Format with custom line length.

## Rules & Configuration
`ruff rule` - List all available rules with descriptions.
`ruff rule E` - List all rules in a category (E = errors).
`ruff rule W` - List warning rules.
`ruff show-settings` - Display active configuration.
`ruff config` - Show resolved configuration from pyproject.toml or ruff.toml.

## Workflow
`ruff check . && ruff format .` - Check for issues, then format code.
`ruff check --fix . && ruff format .` - Fix issues, then format code.

## Configuration File (ruff.toml or pyproject.toml)
```toml
[tool.ruff]
line-length = 100
target-version = "py311"
select = ["E", "W", "F", "I"]
ignore = ["E501"]
exclude = ["tests/", ".venv/"]
```
