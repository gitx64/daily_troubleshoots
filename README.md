# troubleshoots

a collection of issues i ran into and fixed (or at least found a workaround for). mostly linux, bash, and misc sysadmin stuff.

## structure

each file is named `DD-MM-YYYY:topic.md`. topics are whatever felt relevant at the time — driver configs, locale issues, gpg signing, tmp dir shenanigans, etc.

## adding a new one

```bash
./newmd "what went wrong this time"
```

or just `./newmd` and type it when prompted. it'll create a file with today's date.

## contents

| date | topic |
|---|---|
| 19-04-2026 | tmux locale and nerd fonts |
| 20-04-2026 | default network not starting on libvirt |
| 25-04-2026 | missing dependencies while building from source |
| 01-05-2026 | reverse search command history (ctrl+r) |
| 01-05-2026 | bash stream operators (<, >, <<) |
| 02-05-2026 | how /tmp works |
| 13-05-2026 | switching i915 to xe driver |
| 17-05-2026 | recovering sudo after breaking setuid |
| 12-07-2026 | gpg key not found on commit |

## why

because i kept solving the same problem twice.
