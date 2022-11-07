# Functionality of [py-template](https://github.com/inovintell/py-template)

> __Please see [template/functionality](./docs/template/functionality.md)
for base functionality, this templates only adjusts and extends it
to be more useful for Python!__

Below is a detailed list of functionalities and their locations
within source code (so you can modify them if you wish with ease),
functionalities provided by base templates __are not repeated here__:

## Local development

In order to have the exact same configuration as is run in `pipelines`
described below do the following:

- clone your repository
- run `poetry install --all-extras`

Now you are able to `autofix`/`lint`/`run tests` in the __exact same way!__

> Note: you might have to read the following sections for exact
commands being run, although most of it is specified via `pyproject.toml`.

## Tooling configuration

All of the easily tunable parameters are located in
[`pyproject.toml`](https://github.com/inovintell/py-template/blob/main/pyproject.toml)
including:

- Tests dependencies/settings
- Automated fixers dependencies/settings
- Linters dependencies/settings
- Code statistics reporting
- Documentation creation/styling
- Semantic release

## Automated code fixing/linting

After opening a PR your code will be subject to the following:

- Whatever is possible will be fixed and pushed back to the branch
(e.g. `black` formatting, removing unused `import`s etc.)
- Linters are run on formatted version to find errors which
we are unable to fix automatically
- Code statistics are run and saved as
[GitHub Job Summaries](https://github.blog/2022-05-09-supercharging-github-actions-with-job-summaries/)

__Note: Please `git pull` from remote before pushing more code
to the branch due to automated fixers!__

Pipeline is defined in
[`.github/workflows/python-code-checker.yml`](https://github.com/inovintell/py-template/blob/main/.github/workflows/python-code-checker.yml)
while settings are defined in
[`pyproject.toml`](https://github.com/inovintell/py-template/blob/main/pyproject.toml)
(code comment sections Fixers, Linters and Reporters)

## Continuous Integration

We provide a dummy folder
[`tests`](https://github.com/inovintell/py-template/tree/main/tests),
where all of your [`pytest`](https://docs.pytest.org/en/7.2.x/)s
should reside.

After every Pull Request the following pipeline is run:

- Tests are run across matrix of `python` and `os` versions
(last three minor versions and `ubuntu-latest`/`macos-latest`)
- Coverage is calculated for every item and uploaded as HTML report
- Coverage is combined and uploaded as HTML report

One can check either the `HTML` reports after downloading,
or checking GitHub Actions status directly.

See
[`.github/actions/python-test/action.yml`](https://github.com/inovintell/py-template/blob/main/.github/actions/python-test/action.yml)
for core functionality and
[`.github/workflows/python-tests.yml`](https://github.com/inovintell/py-template/blob/main/.github/workflows/python-tests.yml)
for its usage in a workflow.

## Continuous Deployment

After a PR is thoroughly checked and finally merged, `py-template` will
take care of deploying your `python` package to package registry
of your choice (see Setup section).

Please see
[`.github/workflows/python-release.yml`](https://github.com/inovintell/py-template/blob/main/.github/workflows/python-release.yml)
for the pipeline functionality.

And finally...

## Automated documentation generation

Every documented function will automatically be added to
`API Reference` section, which exactly models your source code.
This action is performed after Continuous Deployment ran successfully.

One can see the script responsible for it in
[`docs/gen_ref_pages.py `](https://github.com/inovintell/py-template/blob/main/docs/gen_ref_pages.py)

In general, simply add code to `src/<repo-name>` and watch
it automagically appear via
[`mkdocs.yml`](https://github.com/inovintell/py-template/blob/main/mkdocs.yml)

> Please note we are also validating you have sufficiently documented
your code via automated action
[`.github/workflows/python-docstrings-coverage.yml`](https://github.com/inovintell/py-template/blob/main/.github/workflows/python-docstrings-coverage.yml)
(anything below `100` won't pass, fortunately it is easily tunable :) )

## Caching (additional info, advanced)

We tried our best in order to improve pipelines efficiency as much
as possible. In order to do that, we have created a two level
caching mechanism:

- `pipx` is cached on a per-python, per-os level
- `poetry` is cached on a per-python, per-os level

This means initial pass of your actions might be a lot slower
(even a couple minutes), but after the initial run everything
will be simply downloaded from cache.

To see how we did it (or modify/improve it), check
[`.github/actions/setup-poetry/action.yml`](https://github.com/inovintell/py-template/blob/main/.github/actions/setup-poetry/action.yml)
