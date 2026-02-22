# Changelog

All notable changes to twi-cli are documented in this file.

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).
This project uses a `MAJOR.MINOR.PATCH` versioning scheme.

---

## [2.1.0] - 2025

### Added
- Robust jq parsing using safely pre-computed ANSI escape variables to avoid injection errors with special characters in stream titles
- Intuitive follow list management menu with add, remove, import, and manual edit options
- Import channels from an external text file via the Manage Followed Channels menu
- `cleanup_followed_file` function to normalize, deduplicate, and sort the follow list on every write

### Changed
- Follow list is now stored as a human-readable commented text file with a descriptive header
- Settings menu now shows current values inline next to each option
- Main menu and settings menu strip trailing option text after `.` for reliable case matching
- Replaced raw ANSI escape sequences inside jq with `--arg` injected variables for portability

### Fixed
- fzf selection no longer breaks on stream titles containing special characters or newlines
- `gsub("\n"; " ")` applied to all title and category fields before display
- Config toggle function correctly re-evaluates variable state after writing to disk

---

## [2.0.0] - 2025

### Added
- Search by game/category using Twitch GraphQL `searchFor` query
- Search by channel name with live/offline status indicator in results
- `show_streams_for_game` function to list top live streams within a selected category
- Settings menu with quality selection, player selection, and toggleable low-latency and ad-block options
- Manual channel entry from the main menu

### Changed
- Migrated all API calls from REST to Twitch's public GraphQL endpoint
- Replaced hardcoded client ID handling with a named constant `CLIENT_ID`
- Batched follow list API queries in groups of 100 to respect API limits
- Follows live cache is now stored as line-delimited JSON at `~/.cache/twi-cli/follows_live.json`

### Removed
- Dependency on the unofficial Twitch API wrapper scripts from earlier versions

---

## [1.0.0] - 2025

### Added
- Initial release
- Interactive fzf-based main menu
- Local follow list support stored as a plain text file
- Live status check for followed channels using Twitch GraphQL API
- Stream playback via streamlink with configurable quality and player
- Low-latency and ad-block flags passed through to streamlink
- `~/.config/twi-cli/config` for persistent user preferences
- Direct channel playback via command-line argument
- `--help` flag with usage output
- Graceful `SIGINT` handling
- Dependency check on startup with install instructions
