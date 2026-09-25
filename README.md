# ci-templates

Shared GitHub Actions workflows for my Python repos.

## python-tests.yml

Runs `ruff check`, `mypy` (non-blocking) and the fast pytest suite
(`pytest -m "not network" -n auto`) on ubuntu-latest.

Add this file to any repo as `.github/workflows/tests.yml`:

```yaml
name: tests
on:
  push:
    branches: [main, master]
  pull_request:
jobs:
  tests:
    uses: bglong11/ci-templates/.github/workflows/python-tests.yml@main
    with:
      package: my_package        # or "." for script-style repos
      # python-version: "3.12"   # optional, default 3.12
```

Change this workflow once and every calling repo picks it up.

If this repo is private: Settings > Actions > General > Access, allow access
from repositories owned by the user, or calling repos cannot use it.
