# Functionality of [template](https://github.com/inovintell/template)

Below is a detailed list of functionalities and their locations
within source code (so you can modify them if you wish with ease):

## Automated dependency updates

These are carried out by
[renovatebot/renovate](https://github.com/renovatebot/renovate)
at least once a day.

Each time a new version of any `dependency` of your project is released,
a `pull request` will be created and merged automatically (after
all the tests turn green).

You can find our settings in
[`renovate.json`](https://github.com/inovintell/template/blob/main/renovate.json)
and adjust them to your liking.

## Automated labeling

Every file/folder provided by our templates has an associated github `label`,
so __you always know what kind of file was change by the PR__
(see [here](https://github.com/inovintell/template/labels) for
an example list of GitHub labels).

After a `pull request` is open, __GitHub Actions Bot__ tags it
with appropriate label for easier change discovery.

Workflow carrying out these actions is located in
[`.github/workflows/labeler.yml`](https://github.com/inovintell/template/blob/main/.github/workflows/labeler.yml)
and labels are specified in
[`.github/labeler.yml`](https://github.com/inovintell/template/blob/main/.github/labeler.yml).

__Please note labels are automatically cloned from our templates after you click
`Use this template`.__

## Semantic Pull Requests/commits

Semantic versioning/releases are possible via
[Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/).

Our pipelines verify __every commit in `pull request` and its' title__
adhere to this simple standard:

```bash
fix|feat[!]: <change description>
```

which are tailored to:

- `PATCH` - e.g. `fix: remove typo`
- `MINOR` - e.g. `feat: add new security pipeline`
- `MAJOR` - e.g. `fix!: remove predict_proba method`

If you are not sure what this means, you can
read more about `semver` [here](https://semver.org/).

__NOTE:__

> We don't use `scopes` (and advise you not to), as this type of
information is handled automatically by the labeling system

Aforementioned checks are carried out by
[`.github/workflows/pr-linter.yml`](https://github.com/inovintell/template/blob/main/.github/workflows/pr-linter.yml)
and
[`.github/workflows/commit-linter.yml`](https://github.com/inovintell/template/blob/main/.github/workflows/commit-linter.yml)
.

## Unified editor settings

Tabs or spaces?
[`.editorconfig`](https://github.com/inovintell/template/blob/main/.editorconfig)
is a well-respected standard ending this debate, so
developers can focus on actual coding instead with repository-wide
defaults.

See [EditorConfig](https://editorconfig.org/) for more information
and integrations with specific editors/IDEs.

## Linting YAML files

YAML might be written in a plethora of ways, hence enforcing one standard
will improve readability across the codebase.

Our settings of choice can be found in
[`.yamllint.yml`](https://github.com/inovintell/template/blob/main/.yamllint.yml),
but feel free to adjust them to your liking!

If any `.yml` (or `.yaml`) file is changed by `pull request`,
the following workflow
[`.github/workflows/yaml-linter.yml`](https://github.com/inovintell/template/blob/main/.github/workflows/yaml-linter.yml)
is run which lints your code.

## Linting Markdown files

Helpful during documentation creation (like this one!), workflow responsible
for it can be seen in
[`.github/workflows/markdown-linter.yml`](https://github.com/inovintell/template/blob/main/.github/workflows/markdown-linter.yml)
.

## Metadata

Specifying your coding standards and how to contribute is a welcoming
way to encourage others to participate in your project.

We provide
[`CONTRIBUTING.md`](https://github.com/inovintell/template/blob/main/CONTRIBUTING.md)
and
[`CODE_OF_CONDUCT.md`](https://github.com/inovintell/template/blob/main/CODE_OF_CONDUCT.md)
so you don't have to. :)

## Security

We provide various security functionalities, including, but not limited to
[Supply Chain Attacks protection](https://learn.microsoft.com/en-us/microsoft-365/security/intelligence/supply-chain-malware?view=o365-worldwide)

It is provided by
[`stepsecurity/harder-runner`](https://github.com/step-security/harden-runner)
open source projects for every action in the repository, for example:

<!-- markdownlint-disable -->
```
- name: Harden Runner
  uses: step-security/harden-runner@dd2c410b088af7c0dc8046f3ac9a8f4148492a95 # tag=v1.4.5
  with:
    egress-policy: block
    allowed-endpoints: >
      api.github.com:443
      github.com:443
```
<!-- markdownlint-enable-->

will block any outgoing connections from the workflow if the endpoints
differ from the two specified.

__Please note we are pinning actions by hashes of commits, which is another
security measure__
