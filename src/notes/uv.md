`uv init project-name` - Create a new Python project in a new folder.
`uv init .` - Create a new Python project in current folder.
`uv add package-name` - Add a package to the project.
`uv remove package-name` - Remove a package from the project.
`uv pip install package-name` - Add a package to the project without updating toml file.
`uv pip uninstall package-name` - Remove a package from a project without updating toml file.
`uv sync` - Sync dependencies from uv.lock file.
`uv pip list` - List all installed packages.
`uv run script.py` - Run a Python script in the project environment.
`uv tree` - Show dependency tree.
`uv tool install <tool>` - Install a tool

# Details
## Project Setup
`uv init` - Initialize a new project in current directory.
`uv init project-name` - Create a new project with specified name.
`uv venv` - Create a virtual environment (.venv).
`uv venv --python 3.11` - Create virtual environment with specific Python version.

## Managing Packages
`uv add package-name` - Add package and update pyproject.toml and uv.lock.
`uv add package-name==1.2.3` - Add specific version of a package.
`uv add package-name --dev` - Add as development dependency.
`uv remove package-name` - Remove a package.
`uv pip install package-name` - Install package into virtual environment.
`uv pip install -r requirements.txt` - Install packages from requirements file.
`uv pip list` - Show all installed packages.
`uv pip show package-name` - Display package information.

## Dependency Management
`uv sync` - Install/sync all dependencies from uv.lock.
`uv sync --dev` - Sync including development dependencies.
`uv lock` - Create or update uv.lock file.
`uv lock --upgrade` - Update all dependencies to latest versions.

## Running Code
`uv run script.py` - Execute Python script in project environment.
`uv run python script.py` - Run script explicitly with Python.
`uv run python -m module-name` - Run a Python module.
`uv run python` - Start interactive Python REPL in project environment.

## Python Version Management
`uv python list` - List all available Python versions.
`uv python pin 3.11` - Pin project to use Python 3.11.
`uv python install 3.11` - Download and install Python 3.11.
`uv python uninstall 3.10` - Uninstall a Python version.

## Verification & Info
`uv --version` - Display uv version.
`uv tree` - Show dependency tree.
`cat pyproject.toml` - View project configuration.
`cat uv.lock` - View locked dependencies.
