# opencode-lean-ctx

Routes [OpenCode](https://opencode.ai) shell commands through the
[lean-ctx](https://github.com/yvgude/lean-ctx) binary's inline rewriter, so
supported commands return compressed output (fewer tokens for the model).

The rewriting happens in the shell `create.before` hook — after the permission
check has matched the original command text — so your allow rules (e.g.
`ls *`, `git diff *`) keep matching the command you wrote, not the rewritten one.
If the binary is missing or a rewrite fails, the command runs unchanged.

## Install

```jsonc
// opencode.json
{
  "plugins": ["opencode-lean-ctx@git+https://github.com/joseph280996/opencode-lean-ctx.git"]
}
```

## Configuration

| Env var | Default | Meaning |
|---|---|---|
| `LEAN_CTX_BINARY` | `/opt/homebrew/bin/lean-ctx` | Path to the lean-ctx binary (Linux/other: point at your install or PATH copy) |

Requires the lean-ctx binary to be installed. Without it the plugin disables
itself with a warning.

Tested on OpenCode v2.2.2.

## License

MIT
