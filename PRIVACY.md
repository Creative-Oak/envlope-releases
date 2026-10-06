# Envlope privacy policy

*Last updated: 6 October 2026*

Envlope is made by Creative Oak ApS (Denmark). This policy explains what happens to your data when you use the Envlope
Mac app, its command line tool (`envlope`) and its MCP server for AI agents (`envlope-mcp`).

**The short version: Creative Oak has no servers and receives none of your data.** Envlope keeps your environment
variables on your Mac and, if you sync, in your own iCloud account. We don't collect analytics, crash reports or
usage data, and you don't need an account with us.

## What Envlope stores, and where

**On your Mac.** Your projects, profiles, variable values, variable sets, teams, folder locations and settings are
stored under `~/Library/Application Support/Envlope`. Every file is encrypted (AES-256-GCM) with a key that's kept in
your macOS Keychain. When you apply a profile, Envlope writes it to the project's env file (for example `.env`) in the
folder you chose, readable only by your user account.

**In your iCloud account.** If you're signed in to iCloud, Envlope syncs your data through Apple's CloudKit, in your
own private iCloud database. Variable values and everything else Envlope syncs are stored in CloudKit's encrypted
fields, so Apple can't read them. This data counts towards your iCloud storage. Apple's handling of iCloud data is
covered by [Apple's privacy policy](https://www.apple.com/legal/privacy/).

**Shared with people you choose.** When you share a project or a team, the people you invite (and only them) can read
and change that project or team, including its values. You can see who has access and remove people with
**Manage people**. People you share with can keep copies of what they've seen, as with any shared secret.

**Backups.** If you export a backup, Envlope writes a file wherever you choose, encrypted with a password you pick.
Creative Oak never sees the file or the password.

## Network connections

Envlope connects to:

- **Apple iCloud (CloudKit)**, to sync and share, if you're signed in to iCloud.
- **GitHub**, to check for updates (the update feed at `raw.githubusercontent.com`) and to download them
  (`github.com`). Like any website, GitHub receives your IP address, and the request includes Envlope's version
  number. Envlope sends nothing else. You can turn off automatic update checks in Settings → Updates.

Envlope makes no other network connections. Commands you choose to run through Envlope (with `envlope run`, or an
agent you approve) make whatever connections those programs make.

## AI agents

The MCP server runs on your Mac. It never gives an agent a secret value directly. When an agent asks to run a
command with your variables, you see the exact command in Envlope and decide whether to allow it. A command you allow
receives your variables and can do what it likes with them, so only allow commands you trust.

## Your choices

- Use Envlope without iCloud: everything then stays on your Mac.
- Delete a project: it's removed from your Macs and from iCloud (and for the people it was shared with). Deleted items
  stay in **Settings → Recently deleted** on your Mac for 30 days.
- Remove all data: delete the projects in Envlope, then delete `~/Library/Application Support/Envlope` and Envlope's
  entries in Keychain Access. To remove Envlope's iCloud data, go to System Settings → your name → iCloud → Manage →
  Envlope.

## Children

Envlope is a developer tool and isn't directed at children.

## Changes

If this policy changes, the new version is published here with a new date, and significant changes are mentioned in
the release notes.

## Contact

Questions about privacy: open an issue at
[github.com/Creative-Oak/envlope-releases/issues](https://github.com/Creative-Oak/envlope-releases/issues).
