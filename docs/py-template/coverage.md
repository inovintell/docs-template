# Adjusting coverage

Currently coverage is set to `100%`, both within local pipeline and
the CI.

This threshold might be undesirable in many cases, this document describes
how one might adjust it.

Upcoming sections change coverage threshold to `90%`.

## 1. Adjust `precommit`

Modify `.pre-commit-config.yaml` file, specifically `python-tests` entry:

```yaml
# Around the bottom of the file
- id: python-tests
  verbose: true
  name: Python Tests
  # Adjust --cov-fail-under to anything between 0 to 100
  entry: >
    poetry run pytest -n auto --pretty --cov=src
    --cov-fail-under=90--cov-report=term-missing test
  pass_filenames: false
  language: system
  stages:
    - commit
  types:
    - python
```

## 2. Adjust GitHub Actions

Modify `.github/workflows/python-tests.yml`, bottom of the file, by adding
the following argument to the action as presented below:

```yaml
- name: Upload combined coverage
  uses: ./.github/actions/python-coverage
  with:
    fail-under: 90
```

> __That's it, now your coverage checks should be at 90%!__
