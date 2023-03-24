# Python versioning

Currently [py-template](https://github.com/inovintell/py-template) is set to
support Python versions `3.9` or above according to `numpy`'s
[NEP29](https://numpy.org/neps/nep-0029-deprecation_policy.html)
(which is not a standard per-se, but due to large influence of the package
it is followed by many projects, especially in scientific Python).

Currently tests are run locally using Python version of your choosing
(but greater than `3.9`), while the code checkers run on versions
`3.9.x` or `3.10.x` (due to lack of support of `3.11` from `pytype`).

Within GitHub pipelines we have currently pinned tests to run across
the following version matrix (and across Linux and MacOS for each):

- `3.9` (lowest supported version you should target)
- `3.10`
- `3.11`

This approach is well-suited for libraries and frameworks, which should
provide support for larger set of dependencies, __but might be unnecessary
for standalone applications__ (like Dockerized FastAPI service).

If you are __not__ developing a library we advice to use only one
version of Python (preferably `3.10` due to the ease of setup and no conflicts)
and one OS (usually `linux` locally and `ubuntu` within pipeline).

> Rest of the document describes how to adjust config to Python `3.10` and
Ubuntu and is tailored to standalone applications

## 1. Adjusting `pyproject.toml`

Modify `.pyproject.toml`` file under `DEPENDENCIES` section as shown below:

```toml
###############################################################################
#
#                               DEPENDENCIES
#
###############################################################################

[tool.poetry.dependencies]
# Only change here
python="~=3.10"
```

After that we need to adjust `ruff` settings to tailor any automated fixers
and code checkers to our new version.

One can do it under `FIX SETTINGS` section via single line change:


```toml
###############################################################################
#
#                                FIX SETTINGS
#
###############################################################################

[tool.black]
line-length = 79

[tool.ruff]
# Only change here
target-version = "py310"
```

## 2. Adjusting GitHub Actions

Modify `.github/workflows/python-tests.yml` and `matrix` specifically as shown below
(you can simply remove the OSes/versions you are not interested in):

```yaml
jobs:
  tests:
    if: ${{ ! contains(github.repository, 'template') }}
    strategy:
      matrix:
        py:
          - '3.10'
        os:
          - ubuntu-latest
    name: >
      ${{ matrix.os }} | py-${{ matrix.py }}
    runs-on: ${{ matrix.os }}
```

> These two steps should be enough to adjust to specific version and lower 
costs/entry barrier by only testing across single version and OS.
