# Tips & Tricks

In order to have even more automation you can supplement usage
of [py-template](https://github.com/inovintell/py-template) with
a set of predefined aliases.

> __These aliases should be placed either in `~/.bashrc`
(for `bash` shell) or `/.zshrc` (for `zsh` shell). For other
shells please see their respective documentation.__

Check below for even more automation:

## Clone & Initialize

Function below will:

1. Clone repository
2. Install `poetry` dependencies
3. Setup necessary `pre-commit` hooks

Feel free to rename this function to whatever you like!

```bash
# Git Clone Initialize Python
gclip () {
    # Automatically clones and initializes a git repo (for Python language)
    # USAGE: gclip <repo_url>
    url=$1
    # Get last part of url without .git extension and use it as repo name
    repo_name="$(echo "${url##*/}" | cut -f 1 -d '.')"
    git clone "${url}"
    cd "${repo_name}"
    poetry install --all-extras
    poetry run pre-commit install -t pre-commit -t commit-msg
}
```

Example usage (from command line):

```bash
gclip https://github.com/inovintell/py-template.git
```

__Note: `SSH` protocol is of course supported by the function above__
