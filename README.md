# actions-cheat-sheet

Cheat sheet for Github Actions! PRs are highly welcome. :smile:

- [Common](#common)
- [Linux Only](#linux-only)
- [MacOS Only](#macos-only)
- [Windows Only](#windows-only)

## Common

- Strategy: creates a build matrix for your jobs. You can define different variations of an environment to run each job in.

```yaml
jobs:
  multiple_os_versions:
    runs-on: ${{ matrix.os }}
    strategy:
      matrix:
        os: [ubuntu-16.04, ubuntu-18.04]
        node: [6, 8, 10]
    steps:
      - uses: actions/setup-node@v1
        with:
          node-version: ${{ matrix.node }}
```

## Linux Only

- Use container in Linux

```yaml
jobs:
  linux_with_container:
    runs-on: ubuntu-latest
    container: gcc:4
    steps:
      - name: GCC version
        run: gcc -v
```

## MacOS Only

- `jobs.<job_id>.container` doesn't work when `jobs.<job_id>.runs-on` = `macos-*`
- Use gcc-8 / gcc-9 as default gcc runtime

```yaml
jobs:
  macos_with_gcc_and_make:
    runs-on: macos-latest
    steps:
      - name: GCC version
        shell: bash
        run: |
          shopt -s expand_aliases
          alias gcc='gcc-8'
          gcc -v
```

## Windows Only

- `jobs.<job_id>.container` doesn't work when `jobs.<job_id>.runs-on` = `windows-*`
- Use bash

```yaml
jobs:
  windows_with_bash:
    runs-on: windows-latest
    steps:
      - name: Display PATH
        run: echo $PATH
        shell: bash
```
