# XPorts

[English](README.md) | [中文](README.zh-CN.md)

Interactive TUI port manager for macOS — scan, filter & kill listening ports right in your terminal.

![tui-main](screenshots/tui-main.png)

## Features

- **Zero dependencies** — pure Node.js built-in modules, nothing to install
- **Interactive TUI** — full keyboard navigation, no mouse needed
- **Smart labels** — auto-detect known services (MySQL, Redis, Nginx, Docker...)
- **Multi-select & batch kill** — pick multiple ports and terminate them at once
- **Real-time filter** — press `/` to search by port, process name or description
- **i18n** — Chinese & English interface (`--lang=zh` / `--lang=en`)
- **System process awareness** — dims system services (AirPlay, rapportd, etc.)
- **Docker recognition** — highlights Docker-mapped ports in blue

## Screenshots

### `xports --help`

![tui-help](screenshots/tui-help.png)

### `xports`

![tui-main](screenshots/tui-main.png)

## Installation

### npm (recommended)

```bash
npm install -g @heyuan110/xports
```

### Git clone

```bash
git clone https://github.com/heyuan110/xports.git
cd xports
npm link
```

### Single file

```bash
curl -o /usr/local/bin/xports https://raw.githubusercontent.com/heyuan110/xports/main/bin/xports
chmod +x /usr/local/bin/xports
```

## Usage

```bash
xports                # Launch interactive TUI (Chinese by default)
xports --lang=en      # English interface
xports --lang=zh      # Chinese interface
xports -h | --help    # Show help
xports -v | --version # Show version
```

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `↑` `↓` / `j` `k` | Move cursor up / down |
| `Space` | Toggle select current item |
| `a` | Select all / deselect all |
| `Enter` | Kill selected processes (with confirmation) |
| `/` | Filter by keyword |
| `r` | Refresh port list |
| `q` / `Esc` | Quit |

## How It Works

XPorts calls `lsof -iTCP -sTCP:LISTEN -nP` to scan all listening TCP ports on your Mac, parses the output, and renders an interactive TUI with ANSI escape codes. No external dependencies — only Node.js built-in modules (`child_process`, `readline`).

## Requirements

- macOS (uses `lsof`)
- Node.js >= 14

## License

[MIT](LICENSE)

## Author

**bruce** — [heyuan110.com](https://heyuan110.com)
