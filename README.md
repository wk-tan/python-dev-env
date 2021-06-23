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

4. Install multiple versions of `python` and set one of them at global level
```bash
pyenv install 3.7.10
pyenv install 3.8.8
pyenv install 3.9.2
pyenv global 3.8.8
pyenv versions
```

5. Verify `python 3.8.8` is set at global level
```bash
echo `python --version`; echo `python3 --version`
echo `which python`; echo `which python3`
```

6. Upgrade `pip` and list all `pip` installed packages
```bash
pip install -U pip
pip list
```

7. Install JupyterLab and multiple commonly used packages
```bash
pip install jupyter jupyterlab black flake8 isort
```

## Poetry
[Poetry](https://python-poetry.org/docs) is a tool for dependency management and packaging in Python.

1. Install the latest version of `poetry` in home folder.
```bash
cd ~
curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python -

```

2. List `poetry` config and set creation of virtual environment to be within a project folder.
```bash
poetry config --list
poetry config virtualenvs.in-project true
```

## Start a new project
1. WIP

## Continue from an existing project
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

3. Utilize JupyterLab at global level with dependencies installed within `.venv`. Note that, the `python` command used here is defined in step 1. 
```bash
poetry run python -m ipykernel install --user --name {awesome_name} --display {Awesome Name}
jupyter kernelspec list
```

4. Log into JupyterLab and verify if the new kernel is available
```bash
jupyter lab
```

## Extras
### Global JupyterLab
1. Export path for JupyterLab
```bash
export PATH="$HOME/.pyenv/versions/{global_version}/bin:$PATH"
```

### Configure black, flake8 and isort in VS Code
1. Set following key-value pairs in `settings.json`
```json
{
    "python.defaultInterpreterPath": "/home/waikiat/.pyenv/versions/{global_version}/bin/python",
    "python.formatting.blackPath": "/home/waikiat/.pyenv/versions/{global_version}/bin/black",
    "python.linting.flake8Path": "/home/waikiat/.pyenv/versions/{global_version}/bin/flake8",
}
```
