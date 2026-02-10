`vulture .` - Find dead code in all Python files in current directory.
`vulture script.py` - Find dead code in a specific file.
`vulture src/` - Find dead code in a directory recursively.
`vulture --min-confidence 100` - Show only certain dead code (100: highest confidence).
`vulture --min-confidence 80 .` - Show high and medium confidence dead code.
`vulture --min-confidence 60 .` - Show all confidence levels (default is 80).
`vulture --exclude tests/ .` - Exclude tests directory from analysis.
`vulture --ignore-names test_* .` - Ignore names matching pattern.
`vulture --make-whitelist . > whitelist.py` - Generate whitelist of false positives.
`vulture --help` - Display help and available options.

# Details
## Basic Usage
`vulture .` - Check all Python files in current directory.
`vulture script.py` - Check a specific file.
`vulture src/ lib/` - Check multiple directories.
`vulture *.py` - Check all Python files in current directory only.

## Confidence Levels
`vulture --min-confidence 100 .` - Only high confidence dead code (very few false positives).
`vulture --min-confidence 80 .` - Medium to high confidence (default).
`vulture --min-confidence 60 .` - Low to high confidence (more warnings).

## Filtering Results
`vulture --ignore-names test_*,_* .` - Ignore functions/variables matching patterns.
`vulture --ignore-decorators property,cached_property .` - Ignore decorated items.
`vulture --exclude tests/,venv/ .` - Exclude directories from analysis.
`vulture --exclude __pycache__,*.pyc .` - Exclude file patterns.

## Whitelist Management
`vulture --make-whitelist . > whitelist.py` - Generate whitelist of potential false positives.
`vulture --make-whitelist script.py > my_whitelist.py` - Generate whitelist for specific file.
`vulture . whitelist.py` - Check code with custom whitelist.
`vulture . whitelist1.py whitelist2.py` - Use multiple whitelists.

## Output Control
`vulture --help` - Show all available options.
`vulture --version` - Display vulture version.
`vulture . 2>&1 | grep -v test_` - Filter output (remove lines with "test_").

## Common Patterns
`vulture . --min-confidence 80 --exclude tests/` - Typical check excluding tests.
`vulture . --min-confidence 100` - Conservative check (minimal false positives).
