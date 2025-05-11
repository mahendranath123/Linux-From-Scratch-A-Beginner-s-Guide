# VI Editor Shortcuts Cheat Sheet

## 🔄 Modes in VI Editor
| Mode | Description | How to Enter |
|------|-------------|--------------|
| **Normal Mode** (default) | Navigation and command execution | Press `Esc` from other modes |
| **Insert Mode** | Text editing | Press `i` from Normal mode |
| **Command Mode** | Saving, quitting, searching | Press `:` from Normal mode |
## 🧭 Basic Navigation
| Shortcut | Action |
|----------|--------|
| `h` | Move left |
| `l` | Move right |
| `j` | Move down |
| `k` | Move up |
| `0` | Move to beginning of line |
| `^` | Move to first non-blank character |
| `$` | Move to end of line |
| `w` | Move to next word |
| `b` | Move to previous word |
| `gg` | Move to start of file |
| `G` | Move to end of file |
| `:n` | Move to line number n |
## ✏️ Insert Mode Shortcuts
| Shortcut | Action |
|----------|--------|
| `i` | Insert before cursor |
| `I` | Insert at beginning of line |
| `a` | Append after cursor |
| `A` | Append at end of line |
| `o` | Open new line below |
| `O` | Open new line above |
| `Esc` | Exit insert mode |
## ✂️ Editing Text
| Shortcut | Action |
|----------|--------|
| `x` | Delete character under cursor |
| `X` | Delete character before cursor |
| `dw` | Delete word |
| `dd` | Delete line |
| `d$` | Delete to end of line |
| `d0` | Delete to beginning of line |
| `D` | Delete to end of line |
| `u` | Undo last action |
| `Ctrl + r` | Redo last undo |
| `yy` | Yank (copy) line |
| `yw` | Yank word |
| `p` | Paste after cursor |
| `P` | Paste before cursor |
## 🔍 Search and Replace
| Shortcut | Action |
|----------|--------|
| `/pattern` | Search forward for pattern |
| `?pattern` | Search backward for pattern |
| `n` | Repeat search forward |
| `N` | Repeat search backward |
| `:%s/old/new/g` | Replace all in file |
| `:s/old/new/g` | Replace all in current line |
## 📂 Working with Multiple Files
| Shortcut | Action |
|----------|--------|
| `:e filename` | Open new file |
| `:w` | Save file |
| `:wq` | Save and exit |
| `:q!` | Quit without saving |
| `:split filename` | Horizontal split |
| `:vsplit filename` | Vertical split |
| `Ctrl + w + w` | Switch between splits |
