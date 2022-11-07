# Setup of [py-template](https://github.com/inovintell/template)

> __TLDR: same as `README.md`, but needs
[GitHub Actions Secrets](https://docs.github.com/en/rest/actions/secrets)
set on a repo/organization level.__

__WARNING: use repository name which is ABSENT from
[pypi.org](https://pypi.org/) or package index of your choosing.__

## Initial Setup

- Click green button `Use this template`
- Name your repository, but remember to use
__NAME ABSENT in [pypi.org](https://pypi.org/)__ and
__use `snake_case` for a name!__
- Optional (but recommended):
[add main branch protection](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/defining-the-mergeability-of-pull-requests/about-protected-branches)

## Setup Credentials for package release

> __If you don't want to release your package, you don't have to do this step!__

Please add to your repository's
[Encrypted Secrets](https://docs.github.com/en/actions/security-guides/encrypted-secrets)
the following:

- `PYPI_NAME` - any name of package index, e.g. `pypi` or `test-pypi`
- `PYPI_URL` - `url` to hosting:

  - `https://test.pypi.org/legacy/` - for `test-pypi`
  - `https://pypi.org/legacy/` - for `pypi`

- `PYPI_TOKEN` - account-wide token allowing for package creation

### Additionally for [`gemfury.com`](https://gemfury.com/)

To upload to [`gemfury.com`](https://gemfury.com/) one has to manually add:
<!-- markdownlint-disable -->
```yaml
poetry config http-basic.dialogue ${{ secrets.PYPI_TOKEN }} ${{ secrets.PYPI_TOKEN }}
```
<!-- markdownlint-enable-->

as the first command in `Deploy to registry`
[here](https://github.com/inovintell/py-template/blob/main/.github/workflows/python-release.yml#L41)
.
