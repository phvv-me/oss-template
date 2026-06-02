## OSS Template

Reusable Copier template for small, public software projects under `phvv-me`.

The template keeps the productization surface shared across projects while letting each repo provide language-specific commands. It is meant for projects like Maquina and Chefe, where CI, docs, release, changelog, badges, CodeRabbit, Dependabot, and LLM-facing files should stay almost identical.

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

- Common files: README, changelog, license, docs, `llms.txt`, GitHub workflows, Dependabot, CodeRabbit, security, contributing, and agent instructions.
- Language adaptation: Python, Rust, JavaScript, or generic projects differ mainly by setup and command variables.
- Publish adaptation: PyPI, crates.io, npm, generic publish command, or no publish target.
- Package manifests stay language-native. Add or keep `pyproject.toml`, `Cargo.toml`, or `package.json` in each project instead of forcing one cross-language abstraction.

## Local Test

```sh
uvx copier copy oss-template /tmp/example --defaults --data project_name=Example --data description="Example project" --data primary_language=python --data publish_target=pypi
```
