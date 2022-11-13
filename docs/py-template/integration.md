# Integration with existing projects

> __Make sure you went over
[features](https://inovintell.github.io/docs-template/py-template/functionality/)
section before diving right in!__

While `py-template` is best suited as a base
for new projects, you can also integrate with
existing ones (unfortunately not as easily).

## General guidelines

> Steps below should be performed in addition to
[setup](https://inovintell.github.io/docs-template/py-template/setup/)
steps!

> __You might want to initialize an empty
"dummy" repo to have initialized elements
to choose from__

While the steps are not as straightforward,
a rough guideline could be summarized as:

- Move your code to `/src/<project_name>` (keep
`_version.py` and import it in a similar fashion to
[`__init__.py`](https://github.com/inovintell/py-template/blob/main/src/%7B%7Bcookiecutter.repository%7D%7D/__init__.py)
)
- Move your `tests` to `tests` folder (given they use `pytest`)
- Copy whole `.github` folder as-is (keep in mind you might have to perform
a few manual adjustments depending on your project)
- Copy
[`pyproject.toml`](https://github.com/inovintell/py-template/blob/main/pyproject.toml)
and specify your dependencies/optional dependencies in appropriate
sections under
[`[tool.poetry.dependencies]`](https://github.com/inovintell/py-template/blob/main/pyproject.toml#L19)
__and commit `poetry.lock` after you do that!__
- Copy
[`gen_ref_pages.py`](https://github.com/inovintell/py-template/blob/main/docs/gen_ref_pages.py)
to `/docs` folder (automated documentation creation)
- Copy [`renovate.json`](https://github.com/inovintell/py-template/blob/main/renovate.json)
and enable renovate bot __(unless you have one already setup)__
- Copy `.yamllint.yml` __(unless you have one already setup)__
- Copy `.gitignore` __(unless you have one already setup)__
- Copy `.editorconfig` __(unless you have one already setup)__

Feel free to open an Issue with your repository and a short
description of desired effect and we will try to help you with
the adjustment process!

