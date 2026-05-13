## How to change the locale of tmux to show proper nerd icons and support for ansible:

```bash
export LANG=en_US.UTF-8
```
add this to the shell profile and source it for permanent fix.

- if still not fixed then change the default-terminal to tmux-256color in ~/.tmux.conf

set -g default-terminal "tmux-256color"
set -as terminal-overrides ',xterm*:sitm=\E[3m'

- Also you can try to set 

```bash
TERM=$TERM
```
