# setup-mx

GitHub Action that installs the [MX Script](https://github.com/jlkdevelop/mxscript) (`mx`) CLI on a runner.

> Founded by [Jassim Alkharafi](https://github.com/jlkdevelop). MIT-licensed.

## Usage

```yaml
- uses: jlkdevelop/setup-mx@v1
- run: mx test
```

Pin a specific version:

```yaml
- uses: jlkdevelop/setup-mx@v1
  with:
    version: v0.14.0
```

`version` accepts `latest` (default), `v0.14.0`, or `0.14.0`.

## Supported runners

| OS               | x64 | arm64 |
| ---------------- | --- | ----- |
| `ubuntu-*`       | ✅  | ✅    |
| `macos-*`        | ✅  | ✅    |
| `windows-*`      | ✅  | ✅    |

The action downloads the matching prebuilt binary from the [mxscript releases page](https://github.com/jlkdevelop/mxscript/releases) and adds it to `$PATH`.

## Outputs

| Name      | Description                            |
| --------- | -------------------------------------- |
| `version` | The mx version that was installed.     |

## Example: full CI workflow

```yaml
name: CI
on: [push, pull_request]

jobs:
  test:
    runs-on: ${{ matrix.os }}
    strategy:
      matrix:
        os: [ubuntu-latest, macos-latest, windows-latest]
    steps:
      - uses: actions/checkout@v4
      - uses: jlkdevelop/setup-mx@v1
      - run: mx test
```

## License

[MIT](./LICENSE) © Jassim Alkharafi
