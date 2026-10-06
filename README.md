# Envlope

A Mac app for your projects' `.env` files and environments (Development, Staging, Production…). Keep them in one place,
write the one you need to the project folder when you need it, and share them with your team through iCloud.

## Download

**[Download the latest version](https://github.com/Creative-Oak/envlope-releases/releases/latest)** (the `.dmg` file),
open it and drag Envlope to Applications. Envlope updates itself after that.

Requires macOS 14 or later, on Apple silicon or Intel. Envlope is signed by Creative Oak ApS and notarized by Apple.
Sync and sharing need iCloud; everything else works without it.

## What it does

- **Profiles:** each project's environments, imported from its `.env` files, edited in place, values masked by default.
- **Apply safely:** writing a profile to the env file shows exactly what changes first, and Undo puts the old file back.
- **Sync and share:** between your Macs, with people on a project, or with a whole team. Edits merge per variable;
  when two people change the same one, Envlope asks which to keep.
- **Command line and AI agents:** `envlope run -- <command>` runs a command with a profile, nothing written to disk.
  An MCP server lets agents use your variables without seeing them, and every command needs your approval.
- **Backups:** export everything to a password-encrypted file.

## More

- [Guide](GUIDE.md): how to use Envlope, sharing and teams, the command line, agents, and what happens to your data.
- [Privacy policy](PRIVACY.md): Creative Oak runs no servers and collects nothing.
- [Release notes](https://github.com/Creative-Oak/envlope-releases/releases)
- Problems or questions: [open an issue](https://github.com/Creative-Oak/envlope-releases/issues).

© Creative Oak ApS
