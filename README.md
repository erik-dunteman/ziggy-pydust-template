# Pydust Template for UV and Hatchling

This fork reworks the template to use [UV](https://docs.astral.sh/uv/), [Hatchling](https://github.com/pypa/hatch), and [Ruff](https://github.com/astral-sh/ruff), instead of [Poetry](https://github.com/python-poetry/poetry) and [Black](https://github.com/psf/black).

Changes were minimal, just small pyproject.toml and build.py (hatch_build.py) changes to use PEP 621 standard.

We also reconfigure to a self-managed zig build. This means pytest no longer runs Zig tests automatically, you must manually run them.

### How to build

Environment:
```bash
pyenv local 3.13.1 # set python version
uv sync # install dependencies
```

Build and run tests:
```bash
uv run pytest # run python tests
uv run zig build test -Dpython-exe=$(uv python find) # run zig tests
```
Note the `-Dpython-exe=$(uv python find)` flag is required to avoid a codepath in pydust that shells out to `poetry`.


### My environment
- All done with [ziggy-pydust==0.25.1](https://github.com/spiraldb/ziggy-pydust/releases/tag/0.25.1)
- On a Mac with M1 (ARM) chip
- Using `zig` `0.14.0`
- Using `python` `3.13.1`
  - IMPORTANT: python must be installed with `pyenv`, not `brew`. The python from `brew` comes in Framework format, which breaks pydust's build process due to how the path is parsed.