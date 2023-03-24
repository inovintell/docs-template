# Adjusting linting

Code linting (and code fixers) are performed by
[ruff](https://github.com/charliermarsh/ruff), which is a faster
alternative to popular i[flake8](https://flake8.pycqa.org/en/latest/)
but significantly faster.

[py-template](https://github.com/inovintell/py-template) provides
a highly opinionated set of rules which might not exactly fit
your needs.

Luckily it is relatively easy to adjust these rules.

## Modifying `pyproject.toml`

All of the `ruff` rules are described within `[tool.ruff]` and following
sections (under `FIX SETTINGS`):

```toml
###############################################################################
#
#                                FIX SETTINGS
#
###############################################################################

[tool.black]
line-length = 79

[tool.ruff]
target-version = "py39"
```

What you are probably after is one of:

- `select` field - allows us to choose checkers and fixers
to run automatically
- `ignore` field - specific erros to exclude from a larger
set specified by `select`

Others are provided matching the following regex:

```toml
[tool.ruff.<CHECKER>]
```

These allow us to modify specific rules for different fixers and/or
checkers.

> __For more information check out `ruff` documentation
[here](https://beta.ruff.rs/docs/configuration/#using-pyprojecttoml)__

All of the options are available and you can tune them as you wish!
