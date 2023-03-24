# FAQ

Common issues and possible solutions:

## Updated `poetry` dependencies, but pipeline does not see that

Please run the following in your shell:

```sh
poetry run install --all-extras
```

## I want to run specific check

Please run the following in your shell:

```sh
poetry run pre-commit <hook-id>
```

`<hook-id>`s can be found in `.pre-commit-config.yaml`, for example:

```yaml
- id: yaml-linter # This one
  verbose: true
  name: YAML Linter
  entry: poetry run yamllint
  language: system
  stages:
    - commit
  types:
    - yaml
```

## One of the GitHub Actions is failing, but working locally

Try clearing the cache and restarting the failing action.
See
[here](https://docs.github.com/en/actions/using-workflows/caching-dependencies-to-speed-up-workflows#managing-laches)
for more information.

If the above does not help, please raise an issue with an extensive
description (changes performed by commit, which action fails etc.)
