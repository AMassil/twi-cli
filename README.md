# twi-cli

A terminal-based CLI tool for browsing and watching Twitch streams, heavily inspired by [ani-cli](https://github.com/pystardust/ani-cli). Navigate channels, categories, and your personal follow list entirely from the command line using an interactive fuzzy finder interface.

[Capture vidéo du 2026-02-26 22-23-11.webm](https://github.com/user-attachments/assets/e3c0c6a1-db2a-404b-9db2-40bc8dbab7fd)

---

## Features

- Browse and watch your locally followed channels with live status
- View the top 30 globally live streams
- Search Twitch by game/category or channel name
- Watch any specific channel directly by name
- Configurable stream quality, player, low-latency mode, and ad blocking
- Follow list management: add, remove, import from file, or edit manually
- Persistent config stored in `~/.config/twi-cli/`

---

## Dependencies

The following tools must be installed and available in your `$PATH`:

| Tool         | Purpose                             |
|--------------|-------------------------------------|
| `curl`       | HTTP requests to Twitch GraphQL API |
| `jq`         | JSON parsing                        |
| `fzf`        | Interactive fuzzy finder menus      |
| `streamlink` | Stream extraction and playback      |
| `mpv`        | Default media player                |
| `sed`        | Config file editing                 |
| `awk`        | Text processing                     |
| `grep`       | Pattern matching                    |
| `tr`         | Text transformation                 |
| `sort`       | Sorting channel lists               |
| `wc`         | Line counting                       |

**Ubuntu/Debian:**

```bash
sudo apt update && sudo apt install curl jq fzf streamlink mpv coreutils grep gawk
```

**Arch Linux:**

```bash
sudo pacman -S curl jq fzf streamlink mpv gawk grep
```

**macOS (Homebrew):**

```bash
brew install curl jq fzf streamlink mpv gawk grep
```

---

## Installation

```bash
git clone https://github.com/AMassil/twi-cli.git
cd twi-cli
chmod +x twi-cli
```

To install system-wide:

```bash
sudo cp twi-cli /usr/local/bin/twi-cli
```

---

## Usage

Launch the interactive menu:

```bash
twi-cli
```

Watch a specific channel directly:

```bash
twi-cli shroud
```

Show help:

```bash
twi-cli --help
```

---

## Configuration

On first run, a config file is created at `~/.config/twi-cli/config` with the following defaults:

```bash
DEFAULT_QUALITY="best"
DEFAULT_PLAYER="mpv"
LOW_LATENCY="true"
DISABLE_ADS="true"
```

You can edit this file manually or use the Settings menu inside the tool.

**Quality options:** `best`, `1080p60`, `1080p`, `720p60`, `720p`, `480p`, `360p`, `worst`, `audio_only`

**Player options:** `mpv`, `vlc`, `ffplay`

---

## Follow List

Your follow list is stored at `~/.config/twi-cli/followed.txt`. It is a plain text file with one channel name per line. Lines starting with `#` are treated as comments and ignored.

```
# My followed channels
shroud
tarik
riotgames
```

You can manage this list through the "Manage Followed Channels" menu, edit the file directly, or import channels from an existing text file.

---

## How It Works

twi-cli communicates with Twitch using the public GraphQL API endpoint used by the Twitch web client. No OAuth token or Twitch developer account is required. Channel live status is fetched in batches of 100 and cached locally at `~/.cache/twi-cli/follows_live.json` for the duration of a session.

---

## Limitations

- Uses Twitch's public client ID, which may break if Twitch changes their internal API
- Ad blocking via streamlink's `--twitch-disable-ads` flag may not be fully effective
- VODs and clips are not currently supported
- Requires a terminal with ANSI color code support

---

## Contributing

Contributions are welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md) before opening a pull request.

---

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
