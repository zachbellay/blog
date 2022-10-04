+++
title="Pyenv & Poetry New Project Start"
date=2021-05-31
extra.tldr=""
+++

```bash
# install pyenv on your machine

curl https://pyenv.run | bash

# install python in pyenv

pyenv install 3.9.5

# create virtual environment:

pyenv virtualenv 3.9.5 deez-nuts-joke-generator-dev

# set deez-nuts-joke-generator-dev as the default virtual environment for the current directory

pyenv local deez-nuts-joke-generator-dev

# install poetry in your virtual environment

pip install poetry

# initialize project

poetry init

# install new dependencies

poetry add numpy

# install dependencies (if a pyproject.toml + poetry.lock already exists for a project)

poetry install
```
