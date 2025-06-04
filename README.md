# Pydust Template for UV and Hatchling

This fork reworks the template to use [UV](https://github.com/uv-labs/uv), [Ruff](https://github.com/astral-sh/ruff), and [Hatchling](https://github.com/uv-labs/hatchling) instead of [Poetry](https://github.com/python-poetry/poetry) and [Black](https://github.com/psf/black).

### How to build

Environment:
```bash
pyenv local 3.13.1 # set python version
uv sync # install dependencies
```

Initial build:
```bash
uv run pytest # run python tests
uv run zig build test -Dpython-exe=$(uv python find) # run zig tests. Requires
```


### My environment
- All done with [ziggy-pydust==0.25.1](https://github.com/spiraldb/ziggy-pydust/releases/tag/0.25.1)
- On a Mac with M1 (ARM) chip
- Using `zig` `0.14.0`
- Using `python` `3.13.1`
  - IMPORTANT: python must be installed with `pyenv`, not `brew`. The python from `brew` comes in Framework format, which breaks pydust's build process.