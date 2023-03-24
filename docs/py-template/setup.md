# Setup of [py-template](https://github.com/inovintell/template)

> __TLDR: same as `README.md`, but needs
[GitHub Actions Secrets](https://docs.github.com/en/rest/actions/secrets)
set on a repo/organization level and `poetry` + `pre-commit` setup.

__WARNING: use repository name which is ABSENT from
[pypi.org](https://pypi.org/) or package index of your choosing.__

## Initial Setup

- Click green button `Use this template`
- Name your repository, but remember to use
__NAME ABSENT in [pypi.org](https://pypi.org/)__ and
__use `snake_case` for a name!__
- Enable `gh-pages` branch on `/` to have your documentation hosted
(see [here](https://docs.github.com/en/pages/quickstart))
- Enable hosted `renovatebot`, see [here](https://github.com/marketplace/renovate)
- Create `poetry` environment (make sure you have it installed, see
[here](https://python-poetry.org/docs/#installation) for more info)
- Enable `pre-commit` hooks locally

__Last two steps can also be quickly wrapped in a single function
usable from your shell, see
[here](https://inovintell.github.io/docs-template/py-template/tricks/)
for more information__

## Setup Credentials for Semantic Release to PyPI

> __If you don't want to release your package,
you don't have to perform this step!__

Please add to your repository's
[Encrypted Secrets](https://docs.github.com/en/actions/security-guides/encrypted-secrets)
the following:

- `PYPI_NAME` - any name of package index, e.g. `pypi` or `test-pypi`
- `PYPI_URL` - `url` to hosting:

  - `https://test.pypi.org/legacy/` - for `test-pypi`
  - `https://pypi.org/legacy/` - for `pypi`

- `PYPI_TOKEN` - account-wide token allowing for package creation

### Additionally for [`gemfury.com`](https://gemfury.com/)

To upload to [`gemfury.com`](https://gemfury.com/) package registry
one has to manually add:
<!-- markdownlint-disable -->
```yaml
poetry config http-basic.dialogue ${{ secrets.PYPI_TOKEN }} ${{ secrets.PYPI_TOKEN }}
```
<!-- markdownlint-enable-->

as the first command in `Deploy to registry`
[here](https://github.com/inovintell/py-template/blob/main/.github/workflows/python-release.yml#L41)
.
