# Gate Language Support for VS Code

Syntax highlighting for the [Gate](https://gitorii.com) workflow language (`.gate` files).

Gate is the native automation language of the [Torii](https://gitorii.com) ecosystem — a DSL for version control workflows.

## Features

- Syntax highlighting for `.gate` files
- Keyword highlighting: `workflow`, `struct`, `impl`, `fn`, `enum`, `if`, `else`, `for`, `in`, `return`, `async`, `await`, `import`
- Type highlighting: `string`, `number`, `bool`, `list`, `map`, `version`, `path`, `url`, `regex`, `bytes`, `date`, `datetime`, `duration`, `future`, `channel`
- Native function highlighting: `save`, `sync`, `branch.*`, `tag.*`, `snapshot.*`, `mirror.*`, `remote.*`, `scan.*`, `history.*`, `semver.*`, `notify.*`, `repo.*`
- String interpolation highlighting: `{variable}` inside strings
- Comment highlighting: `//` and `/* */`
- Auto-closing brackets and quotes
- Indentation rules

## Example

```gate
import "shared/notify.gate"

workflow release(version: string) {
    save("chore: release {version}")
    tag.create(version)
    sync(push: true)

    on_error {
        snapshot.restore("before-release")
        notify("Release failed for {version}")
    }
}
```

## Installation

Install from the VS Code Marketplace (search for "Gate Language") or from the [releases page](https://gitlab.com/paskidev/gate-vscode/-/releases).

## Related

- [Torii](https://gitorii.com) — the Git client Gate is built for
- [Gate spec](https://gitlab.com/paskidev/gate) — language specification
