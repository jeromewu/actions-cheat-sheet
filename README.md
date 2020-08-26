# actions-cheat-sheet

Cheat sheet for Github Actions! PR highly welcome. :smile:

- [Common](#common)
- [Linux Only](#linux-only)
- [MacOS Only](#macos-only)
- [Windows Only](#windows-only)

## Common

- Strategy: creates a build matrix for your jobs. You can define different variations of an environment to run each job in.

```yaml
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

## Windows Only

- `jobs.<job_id>.container` doesn't work when `jobs.<job_id>.runs-on` = `windows-*`
