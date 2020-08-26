# actions-cheat-sheet

Cheat sheet for Github Actions! PR highly welcome. :smile:

- [Common](#common)
- [Linux Only](#linux-only)
- [MacOS Only](#macos-only)
- [Windows Only](#windows-only)

## Common

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
