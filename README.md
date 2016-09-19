# Python/JavaScript Virtual Environments managing toolkit

## env-py

Tool to create PYTHON virtualenvs and install requirements using PIP.
Arguments:

  1. Python version (for example: 2.7.12)
  2. Main requirements file. Virtualenv name will be
     created based on sha1 hash of it.
  3. Optional requirements file. Will not affect hash.

Virtual environment will be created using `PYENV`.
Optional environment variables:

  - `DOWNLOAD_TO`: path to PyPI packages downloads folder
  - `PYENV_ARGS`: PyEnv custom arguments (current: `${PYENV_ARGS}`)

All output are redirected to `STDERR`.
Expected value from `STDOUT`: virtualenv name (`ENV_ID`)


## env-js

This script is based on [NVM](https://github.com/creationix/nvm) tool and
NPM configuration abilities.

Arguments:
  1. NodeJS Version (for example: 6.6.0)
  2. `package.json` file. Virtualenv name will be
     created based on summary hash of dependencies
     (dependencies, devDependencies)

Virtual environment will be created using PYENV.
Optional environment variables:

  - `DOWNLOAD_TO`: path to NPM packages cache downloads folder
  - `NPM_PREFIX`: path where environments should be installed

All output are redirected to `STDERR`.
Expected value from `STDOUT`: virtualenv name (`ENV_ID`).
Run `npm run start` with `NODE_PATH` pointed to `$NPM_PREFIX/$ENV_ID`


Example:

    NPM_PREFIX=/tmp/npm \
    NVM_PREFIX=$(brew --prefix nvm) \
      ./env-js \
        6.6.0 \
	youproject/package.json
