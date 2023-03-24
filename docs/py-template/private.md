# Private releases

Currently [py-template](https://github.com/inovintell/py-template) is set to
to perform public releases on `PyPI`. 

If the project fails to release documentation __will not be updated__
after merging.

While we advise open-sourcing your projects we understand some of the code
should be kept private.

Follow the steps below in order to perform private release (__package
will be installable from the GitHub URL, see
[poetry documentation](https://python-poetry.org/docs/dependency-specification/#git-dependencies)
for more information__).

## 1. Adjusting release process

There is no need for explicit release, simply __remove 
`.github/workflows/python-release.yml`__ and you are good to go.

## 2. Adjusting documentation release

As the release is not present anymore you have to adjust documentation
release process (which is hooked on release passing).

Change the following lines in `.github/workflows/python-docs-release.yml`
at the top (`on` section changed):

```yaml
---
name: Generate Documentation

on:
  push:
    branches:
      - main
```

That's it, now your documentation will be published privately (keep in mind
you have to enable documentation release via GitHub, see
[here](https://docs.github.com/en/pages/quickstart))
