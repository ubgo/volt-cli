# volt-cli — templates for `volt new cli`

One repo, many variants: `templates/_base` is the shared skeleton; each variant directory overlays files on top of it. Fetched by `volt new` as a tarball at a **pinned tag** — never `main`, so a bad commit here can never break scaffolding fleet-wide.

| Variant | Gives you |
|---|---|
| `minimal` (default) | stdlib-only CLI: flag parsing, version stamping, zero dependencies |
| `cobra` | cobra root command with `--version` |

```sh
volt new cli mytool                      # minimal
volt new cli mytool --template cobra
volt new cli --list
```

Files ending in `.tmpl` are rendered with `[[.Name]]`, `[[.Module]]`, etc. (`[[ ]]` delimiters so Go's `{{ }}` in rendered files passes through untouched); everything else copies verbatim. Keep variants thin — an overlay past ~50 lines means the kit is missing an abstraction.
