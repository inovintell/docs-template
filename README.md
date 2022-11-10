# inovintell templates documentation

## Quick Usage

- Click green button `Use this template`
- Name your repository however you wish (snakecase advised)
- Enable `gh-pages` branch on `/` to have your documentation hosted
(see [here](https://docs.github.com/en/pages/quickstart))
- Optional (but recommended):
[add main branch protection](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/defining-the-mergeability-of-pull-requests/about-protected-branches)
rules
- That is all, all functionalities below are inherited!

> __For optimal experience please use language/functionality
specific templates briefly described below.__

## [template (Generic)](https://github.com/inovintell/template)

> __Use it to as base for a project written in
not supported (yet) language__

Includes, amongst other things:

- Automated PR labeling __based on file changes__
- Automated dependency updates and management
- Automated PR & commits checks in accordance to
[Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)
- Increased security (e.g. [semgrep](https://semgrep.dev/) or
[step-security/harden-runner](https://github.com/step-security/harden-runner))
- Automated linting of `.md` and `.yml` files
- Metadata definitions (e.g. `CONTRIBUTING.md` guide)

See in-depth documentation [here](./docs/template).

## [py-template (Python)](https://github.com/inovintell/template)

> __Use it for any Python project with no (minor) adjustments!__

Includes everything generic template has to offer and extends
functionality by providing:

- [Continuous Integration](https://www.atlassian.com/continuous-delivery/continuous-integration)
for every pull request (tests run using multiple cores!)
- [Continuous Deployment](https://en.wikipedia.org/wiki/Continuous_deployment)
(after pull request is merged) to PyPI repository of your choice
- Automated documentation creation from Python's `docstrings`
- Automated code fixing and linting for every PR
- Identical `dev` experience to the created pipelines via simple
`poetry install --all-extras`!
- Tunable via __single `pyproject.toml`__ in adherence to
[latest Python's best practices](https://pip.pypa.io/en/stable/reference/build-system/pyproject-toml/)

See in-depth documentation [here](./docs/py-template)

## Contributing

If you:

- find any feature missing/desired
- find a bug

Please raise a new GitHub Issue in template-specific repository
or open a new Pull Request.
