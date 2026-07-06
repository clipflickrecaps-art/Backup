---
name: Duplicate workflow from artifact registration
description: Why a phantom duplicate workflow keeps restarting and how to remove it
---
A stray `<dir>/.replit-artifact/artifact.toml` registers an artifact-managed workflow (named `<dir>: <title>`) that the platform auto-restarts and that cannot be deleted via workflow tools (PROHIBITED_ACTION). It competes for the app's port, bot token polling, and SQLite session locks.

**Why:** The Telegram Backup app kept hitting `Conflict: getUpdates` and `database is locked` errors because an artifact registration in `telegram-backup/` spawned a second instance.

**How to apply:** If a duplicate workflow keeps reappearing, look for `.replit-artifact` directories in project subfolders and delete the whole directory — the platform then unregisters the artifact and its workflow automatically.
