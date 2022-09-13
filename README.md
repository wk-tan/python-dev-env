# Python Development Environment Setup

## pyenv
[pyenv](https://github.com/pyenv/pyenv) is a simple Python version management.

1. Ensure `python` command is OS default.
```bash
echo `python --version`; echo `python3 --version`
echo `which python`; echo `which python3`
```

2. Install the latest version of `pyenv` in home folder.
```bash
cd ~
curl -L https://github.com/pyenv/pyenv-installer/raw/master/bin/pyenv-installer | bash
```

3. Verify `pyenv` installation by checking its version and list installable `python` versions.
```bash
pyenv --version
pyenv install -l 
```

4. Install Python build dependencies following this [link](https://github.com/pyenv/pyenv/wiki#suggested-build-environment).

5. Install multiple versions of `python` and set one of them at global level.
```bash
pyenv install 3.8.13
pyenv install 3.9.13
pyenv install 3.10.5
pyenv global 3.9.13
pyenv versions
```

6. Verify `python 3.9.13` is set at global level.
```bash
echo `python --version`; echo `python3 --version`
echo `which python`; echo `which python3`
```

7. Upgrade `pip` and list all `pip` installed packages.
```bash
pip install -U pip
pip list
```

8. Install JupyterLab and multiple commonly used packages.
```bash
pip install jupyter jupyterlab black flake8 isort poetry-kernel
```

## Poetry
[Poetry](https://python-poetry.org/docs) is a tool for dependency management and packaging in Python.

1. Install the latest version of `poetry` in home folder.
```bash
cd ~
curl -sSL https://install.python-poetry.org | python3 -
```

2. List `poetry` config and set creation of virtual environment to be within a project folder.
```bash
poetry config --list
poetry config virtualenvs.in-project true
```

### Continue from an existing project
1. Clone a GitHub repository which is developed using different `python` version.
```bash
git clone git@github.com:{username}/{awesome_project}.git
cd {awesome_project}
pyenv local {python_version}
```

2. Install the repository dependencies in `.venv` folder.
```bash
poetry install
```

## Extras
### Utilize Poetry kernel in JupyterLab
1. Install `ipykernel` as a development dependency.
```bash
poetry install --dev ipykernel
```

2. Choose Poetry as a running kernel.

### Configure black, flake8 and isort in VS Code
1. Set following key-value pairs in `settings.json`.
```json
{
  "python.defaultInterpreterPath": "/home/waikiat/.pyenv/shims/python",
  "python.sortImports.path": "/home/waikiat/.pyenv/shims/isort",
  "python.sortImports.args": [
    "--profile=black",
  ],
  "python.formatting.blackPath": "/home/waikiat/.pyenv/shims/black",
  "python.linting.flake8Path": "/home/waikiat/.pyenv/shims/flake8"
}
```
