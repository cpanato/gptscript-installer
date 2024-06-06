# gptscript-installer

This action enables you to install [gptscript](https://github.com/gptscript-ai/gptscript) in your GitHub Workflows.

## Usage

This action currently supports GitHub-provided Linux, macOS and Windows runners (self-hosted runners may not work).

Add the following entry to your Github workflow YAML file:

```yaml
uses: cpanato/gptscript-installer@main
with:
  gptscript-release: '0.8.0' # optional
```

Example using a pinned version:

```yaml
jobs:
  test_gptscript_action:
    runs-on: ubuntu-latest

    permissions: {}

    name: Install gptscript and test presence in path
    steps:
      - name: Install gptscript
        uses: cpanato/gptscript-installer@main
        with:
          gptscript-release: '0.8.0'
      - name: Check install!
        run: gptscript --version
```

Example using the default version:

```yaml
jobs:
  test_gptscript_action:
    runs-on: ubuntu-latest

    permissions: {}

    name: Install gptscript and test presence in path
    steps:
      - name: Install gptscript
        uses: cpanato/gptscript-installer@main
      - name: Check install!
        run: gptscript --version
```


### Optional Inputs

The following optional inputs:

| Input | Description |
| --- | --- |
| `gptscript-release` | `gptscript` version to use instead of the default. |
| `install-dir` | directory to place the `gptscript` binary into instead of the default (`$HOME/.gptscript`). |
| `use-sudo` | set to `true` if `install-dir` location requires sudo privs. Defaults to false. |
