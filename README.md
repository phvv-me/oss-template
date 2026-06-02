## OSS Template

Reusable Copier template for small, public Python projects under `phvv-me`.

The template bakes one fixed toolchain (uv, ruff, pyrefly, mypy strict, pytest, mkdocs-material) so every repo shares the same CI, docs, release, changelog, badges, CodeRabbit, Dependabot, and LLM-facing files. It is meant for projects like Maquina and Chefe, where the productization surface should stay almost identical.

## Use

Create a new project:

```sh
uvx copier copy gh:phvv-me/oss-template my-project
```

Apply to an existing project:

```sh
uvx copier copy gh:phvv-me/oss-template .
```

Update later:

```sh
uvx copier update .
```

Copier stores answers in `.copier-answers.yml`, then uses them for future three-way updates.

## Shape

- Three prompts only: `project_name`, `description`, and `cli_command` (leave blank for a library with no CLI).
- Everything else is a silent, baked default (owner, license Apache-2.0, min Python 3.13, docs accent, CI matrix, version matrix). Override any of them with `--data` when needed.
- Python only. Each project gets a full `pyproject.toml` plus the shared tooling (ruff, mypy strict, pyrefly, pytest, coverage) and a green skeleton out of the box.
- Publishing is PyPI Trusted Publishing via the `pypi` environment.

## Local Test

```sh
uvx copier copy oss-template /tmp/example --defaults --data project_name=Example --data description="Example project" --data cli_command=example
```
