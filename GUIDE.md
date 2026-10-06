# Envlope guide

- [Install and update](#install-and-update)
- [Projects and profiles](#projects-and-profiles)
- [Writing the env file](#writing-the-env-file)
- [Sync between your Macs](#sync-between-your-macs)
- [History](#history)
- [Sharing a project](#sharing-a-project)
- [Teams](#teams)
- [Sharing a team project with someone outside the team](#sharing-a-team-project-with-someone-outside-the-team)
- [What happens to your data when…](#what-happens-to-your-data-when)
- [Variable sets](#variable-sets)
- [Backups](#backups)
- [The command line](#the-command-line)
- [AI agents (MCP)](#ai-agents-mcp)
- [Safety features](#safety-features)
- [Troubleshooting](#troubleshooting)

## Install and update

Download the latest `Envlope-x.y.dmg` from [Releases](https://github.com/Creative-Oak/envlope-releases/releases/latest),
open it and drag Envlope to **Applications**. Envlope needs macOS 14 or later.

Envlope checks for updates once a day and asks before installing one. **Envlope → Check for Updates…** checks now, and
**Settings → Updates** turns automatic checks off. Updates are signed by Creative Oak, and Envlope refuses an update
that isn't. Your data stays when you update.

Keep everyone who shares projects on the same version where you can. If someone's Mac saves data in a newer format,
older versions leave that data alone and show **Update Envlope** in the sidebar until they update.

## Projects and profiles

A **project** is one codebase. A **profile** is one environment of it: Development, Staging, Production and so on.

- **Link a project:** drop the project's folder anywhere on the window, or use **File → Link Project Folder…** (or the
  **+** next to a team, to put it straight into that team). Envlope first shows what it will do: it links the folder
  and keeps an encrypted copy of each `.env`, `.env.local` or `.env.<name>` file as a profile. The files stay where they
  are and aren't changed. Dropping a single env file onto an existing project adds it as another profile.
- **Several at once:** select several folders, drop a folder that holds projects (like `~/Developer`), or use **File →
  Link Projects in Folder…**. Envlope lists the unlinked project folders it finds (two levels down), you tick the ones
  you want and choose Personal or a team.
- **Example files:** `.env.example`-style files list the keys a profile should have. `.env.local.example` applies to the
  Local profile, `.env.example` to the rest. If a profile lacks some, a card says which keys and which file lists them,
  and **Add as Empty** adds them for you to fill in.
- **Other file names:** add more endings (for example `.secrets`) in **Settings → Extra env file endings**.
- **Edit:** click a name or value to change it, and press Return. Values are secret by default and shown as dots; the eye
  reveals one value. Switch **Secret** off for values that aren't (a port, a log level). Add variables in the last row.
- **Profiles:** the **⋯** button next to the profile picker creates a new profile, duplicates the selected one (with
  all its values and sets, handy for making Staging from Production), renames it or deletes it.
- **Where the folder is:** a project remembers its folder on each Mac separately, so teammates can keep it anywhere.
  If a project isn't linked to a folder on this Mac yet, Envlope asks where it is.

## Writing the env file

- **Apply** writes the selected profile to the project's env file (`.env`, or `.env.local` if that's what the project
  uses). First you see every variable that will be added, changed or removed, and nothing is written until you click
  **Write .env**.
- **Undo** puts back the env file as it was before the last write (and asks first too). Undo can itself be undone.
- **Capture** goes the other way: it stores what's in the env file now into the selected profile. It shows the changes
  first too, since the profile syncs to everyone who has the project.
- When the env file doesn't match the profile, a card says how many keys differ; **Compare…** (or **Diff**) lists them
  grouped as different values, only in the file, and only in Envlope, with Apply and Capture right there.
- **Open .env** (next to the folder path) opens the file in your editor. Choose the editor in **Settings → Env files**.
- If the env file isn't ignored by Git, a banner offers to add it to `.gitignore`.
- The **menu bar** icon applies a profile without opening the window (with the same confirmation).

## Sync between your Macs

Sign in to the same iCloud account on each Mac and install Envlope; your projects appear on each one. Envlope syncs at
launch, when you switch back to it, a few seconds after you edit, and when iCloud reports a change. The **Sync** button
syncs right away, and **Settings → Sync automatically** turns background syncing off.

Changes to different variables merge without asking. If the same variable was changed in two places, Envlope asks which
value to keep. Nothing is overwritten silently.

**Setting up another Mac:** install Envlope and sign in to the same iCloud account; your projects, teams and sets
appear after the first sync. Then, per project, click **Choose folder…** to tell Envlope where it lives on that Mac.
A few things are per Mac on purpose: folder links, the command line tools (install them again), always-allowed agent
commands, approved risky values, and settings like extra file endings.

## History

**History** (next to the folder path) lists every change to a project's profiles: who made it, when, and the value
before and after (secret values stay masked until you reveal them). **Restore** puts an old value back, recorded as a
new change. History syncs with the project, so everyone who has it sees the same list. Envlope keeps the last 400
changes from the past year per project.

Set your **nickname** in **Settings → You**. It's shown to the people you share with, in their member lists and next
to your changes in History. (Without one, they see what iCloud shares about you, sometimes just an email address.)

## Sharing a project

Select a personal project and click **Manage people** (the person icon in the toolbar). Invite people by name, email or
phone number. They get an invitation, open it, and the project appears in their Envlope. Everyone on a project can read
and change it.

**Manage people** also shows who has joined and lets you remove people or stop sharing.

## Teams

A team is a shared space for several projects: invite people once, and they get every project in the team, including
projects added later.

1. **Settings → Teams**: type a name and click **Create team**.
2. Click **Manage people…** next to the team and invite your teammates.
3. Right-click a project in the sidebar → **Move to** → the team.

Everyone on the team can see and change its projects. **Settings → Teams** lists who has joined.

## Sharing a team project with someone outside the team

Select the team project, click **Manage people** → **People on "Project" Only…**, and confirm. Then invite people as for
any project; they get only that project, not the rest of the team.

Good to know:

- The team keeps access throughout. People who join the team later get the project too, and people who leave the team
  lose it, once the Mac of whoever first shared it outside the team has synced. That person is the project's owner,
  and only they can invite more people to it.
- People outside the team don't get the team's variable sets. Give them the values in the project itself if they need
  them.
- Everyone on the team should use Envlope 1.5 or later.

## What happens to your data when…

| When… | …this happens |
| --- | --- |
| You **delete a project** | It's removed from Envlope on all your Macs and for everyone it's shared with (including the whole team). The env file in its folder isn't touched. |
| Someone else **deletes a project** you have | It's removed from your Envlope too, and kept for 30 days in **Settings → Recently deleted**, where you can restore it. If you had edited it since, your edit wins and it comes back for everyone. |
| You **move a project to Personal** | Only you (and people you shared it with directly) keep it. The team loses access. |
| You **leave a team** | Its projects and sets are removed from your Mac (into Recently deleted). Everyone else keeps them. A team project you shared outside the team stays yours, under your personal projects; the team stops getting it. |
| The owner **deletes a team** | Its projects become the owner's personal projects. Everyone else loses access; their copies go to Recently deleted. |
| You're **removed from a project** | It's removed from your Mac, into Recently deleted. |
| You're **removed from a team** | Its projects and sets go to Recently deleted on your Mac. Any you had changed since your last sync stay, as your personal projects and sets. |
| You **switch iCloud accounts** | Nothing is deleted. Your projects stay on the Mac and sync to the new account. |

Env files in your project folders are never deleted or changed by any of this; only **Apply** and **Undo** write them.

## Variable sets

A set is a group of variables several projects use, such as a Sentry DSN or shared AWS keys. Create and edit sets in
**Settings → Variable sets**, and switch them on per profile with the **Sets** menu next to the profile picker. A
profile's own values override a set's. Give a set to a team (the picker next to it in Settings) so the team's members
get its variables too.

## Backups

**File → Export Backup…** (or **Settings → Backup**) saves every project, profile, value and variable set into one file,
encrypted with a password you choose. Envlope can't recover a forgotten password, so keep it in your password manager.

**Import Backup…** adds the projects and sets from a backup that aren't on this Mac; ones that are here stay as they
are. Everything comes back as your personal projects and sets (move them into a team again if you like), and you
choose each project's folder again. iCloud is not a backup: a delete syncs to every Mac.

## The command line

**Settings → Command line and agents → Install…** links the `envlope` command into `/usr/local/bin` (if that needs an
administrator, Envlope shows a command to paste into Terminal instead). The tools run from inside the app, so they're
updated with it.

```
envlope list                      # projects and profiles
envlope status                    # which profile is active, drift, missing keys
envlope use <profile>             # write a profile to the env file (shows the changes, asks first)
envlope diff [profile]            # compare the env file with a profile
envlope capture <profile>         # store the env file into a profile
envlope keys                      # key names of the active profile
envlope get <KEY> [--reveal]      # one value (secrets only with --reveal)
envlope undo                      # restore the previous env file (asks first)
envlope run [-p project] -- <cmd> # run a command with the active profile; nothing written to disk
```

Run it from anywhere inside a project folder, or pass `-p <project>`. Scripts without a terminal must pass `--yes` to
`use` and `undo`. The command line works with the data on your Mac; the app does the syncing.

## AI agents (MCP)

Envlope includes an MCP server, so AI coding agents can work with your environments without seeing your secrets. Copy
the configuration from **Settings → Command line and agents → Copy MCP Config** into your agent's MCP settings. It
looks like this:

```json
{ "mcpServers": { "envlope": { "command": "/Applications/Envlope.app/Contents/Helpers/envlope-mcp" } } }
```

Agents can list key names, see which keys are missing or out of date, and run commands with a profile's variables.
**Every command needs your approval:** Envlope shows the exact command, project, profile and folder, and you choose
**Deny**, **Allow Once** or **Always Allow This Command**. No answer within two minutes counts as Deny. Commands you
always allow are listed, and can be removed, in Settings.

A command that receives your secrets can do anything with them, so only allow commands you understand. Also stop
agents reading `.env*` files directly, in your agent's own permission settings.

## Safety features

- **Confirmation before writing:** nothing changes the env file without showing you the changes first.
- **Variables that can run code:** values like `NODE_OPTIONS`, `DYLD_*`, `LD_PRELOAD`, `PATH`, `BASH_ENV` or
  `GIT_SSH_COMMAND` can make programs run code. When one of these was set by someone else (or another Mac) and you
  haven't approved its value on this Mac, it's shown in full and must be confirmed before Envlope writes it or runs a
  command with it.
- **No symbolic links:** Envlope never reads or writes an env file that's a link to somewhere else.
- **Private files:** env files Envlope writes are readable only by your user account.
- **Recently deleted:** anything removed on this Mac or by sync stays restorable for 30 days.
- **Encryption:** everything Envlope stores on your Mac is encrypted with a key in your Keychain, and synced values are
  in CloudKit's encrypted fields. See the [privacy policy](PRIVACY.md).

## Troubleshooting

- **"Not signed in to iCloud" in the sidebar:** sign in under System Settings → your name. Envlope works without
  iCloud, but doesn't sync or share.
- **A project you shared doesn't appear for someone:** they need to open the invitation link, be signed in to iCloud,
  and run Envlope 1.5 or later. Ask them to click **Sync**.
- **"Update Envlope" in the sidebar:** someone saved data with a newer version. Use **Check for Updates…**.
- **The command line can't read its data:** open the Envlope app once on this Mac first, so its Keychain key exists.
- **Something else:** [open an issue](https://github.com/Creative-Oak/envlope-releases/issues). Please don't include
  any secret values.
