# clean-up-macos

A small, safety-first macOS cleanup repo.

It focuses on user-space cleanup only:

- `~/Library/Caches`
- `~/Library/Logs`

It does **not** try to guess what an “unused app” is, delete `/var/log`, or remove language packs automatically. Those tasks are risky and better handled manually or with a dedicated tool you trust.

## What it does

- Shows the exact files and folders it will touch
- Runs in dry-run mode by default
- Refuses to run as `root`
- Requires `--apply` for deletion
- Can skip the confirmation prompt with `--yes`

## Requirements

- macOS
- Bash 3.2+ or later-compatible Bash

## Usage

```bash
./bin/clean-macos
./bin/clean-macos --apply
./bin/clean-macos --logs
./bin/clean-macos --cache --apply
./bin/clean-macos --apply --yes
```

## Safety model

The script only targets allowed user directories under your home folder. It does not accept arbitrary paths, and it prints the resolved deletion list before any destructive action.

## Notes on the Reddit cleanup list

The common cleanup ideas are useful as a checklist, but this repo intentionally automates only the safer parts:

- Cache cleanup: automated
- Log cleanup: automated for user logs
- Language files: manual review recommended
- Unused apps: manual review recommended
- Generic system-cleaning tools: use at your own discretion

## Installation

```bash
chmod +x bin/clean-macos
```

Then run it directly from the repository.
