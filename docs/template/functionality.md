# Functionality of [template](https://github.com/inovintell/template)

Below is a detailed list of functionalities and their locations
within source code (so you can modify them if you wish with ease):

## Automated updates

These are carried out by
[renovatebot/renovate](https://github.com/renovatebot/renovate)
at least once a day.

Each time a new version of any dependency of your project is released,
a Pull Request will be created and merged automatically (after
all tests pass of course).

You can find our settings in
[`renovate.json`](https://github.com/inovintell/template/blob/main/renovate.json)

## Automated code changes labeling

Every file/folder provided by our templates has an associated label,
so __you always know what kind of file was change by the PR!__

After a PR changing some file is open, GitHub Actions Bot tags it
with appropriate label so your developers don't ever have to worry
about it.

Responsible workflow is located in
[`.github/workflows/labeler.yml`](https://github.com/inovintell/template/blob/main/.github/workflows/labeler.yml)
and labels are specified in
[`.github/labeler.yml`](https://github.com/inovintell/template/blob/main/.github/labeler.yml).

__Please note labels are automatically cloned from our templates after you click
`Use this template`__

## Verifying Semantic change are performed

Semantic versioning/releases are possible via
[Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/).

Our pipelines verify __every commit in PR and PR title__ adhere to the
simple standard:

```bash
fix|feat[!]: <change description>
```

__NOTE:__

> We don't use `scopes` (and advise you not to), as these information
is handled automatically by the labeling system

Aforementioned checks are carried out by
[`.github/workflows/pr-linter.yml`](https://github.com/inovintell/template/blob/main/.github/workflows/pr-linter.yml)
and
[`.github/workflows/commit-linter.yml`](https://github.com/inovintell/template/blob/main/.github/workflows/commit-linter.yml)
.

## Unified editor settings

Tabs or spaces? No more,
[`.editorconfig`](https://github.com/inovintell/template/blob/main/.editorconfig)
is a well-respected standard ending this (and similar debates), so
developers can focus on actual coding instead.

See [EditorConfig](https://editorconfig.org/) for more information
and integrations with specific editors/IDEs.

## Linting YAML files

YAML can be written in plethora of ways, hence enforcing one standard
seems to be beneficial.

Our settings of choice can be found in
[`.yamllint.yml`](https://github.com/inovintell/template/blob/main/.yamllint.yml),
but feel free to adjust them to your liking!

If any `.yml` (or `.yaml`) file is changed by Pull Request, the following
[`.github/workflows/yaml-linter.yml`](https://github.com/inovintell/template/blob/main/.github/workflows/yaml-linter.yml)
is run which checks adherence to the aforementioned standard.

## Linting Markdown files

Might be helpful during creating documentation, workflow responsible
for it can be seen in
[`.github/workflows/markdown-linter.yml`](https://github.com/inovintell/template/blob/main/.github/workflows/markdown-linter.yml)

## Metadata

Specifying your code standards and how to contribute is a nice
way to encourage others to participate in your project.

We provide
[`CONTRIBUTING.md`](https://github.com/inovintell/template/blob/main/CONTRIBUTING.md)
and
[`CODE_OF_CONDUCT.md`](https://github.com/inovintell/template/blob/main/CODE_OF_CONDUCT.md)
so you don't have to. :)
