# Initialization

> __What happens after I click `Use this template`?__

More or less the following (for everry template):

- `.github/workflows/initialization.yml` is run
- This workflow changes every `{{cookiecutter.<variable>}}` to
appropriate value based on your GitHub's `<name>/<repo>`
(this includes folders being renamed, text being replaced
and so on...)
- Leftover files (including `initialization.yml`) are
removed
- Those changes are pushed back to the repository by
GitHub Actions Bot
- Labels used for automated change labeling are cloned
from our source repository

The best thing - it is automated, you don't even have
to think about it!
