# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

# v2.1.1

### Fixed
- Small bug in close command.

# v2.1.0

### Added
- Ability to set a custom thread creation response message.
    - Do this via `config set thread_creation_response [message]`

### Changed
- Improve logs command format.
- Improve thread log channel message to have more relevant info.
- Improve close command.
    - You now can close the thread after a delay and use a custom thread close message.
    - You also now have the ability to close a thread silently.

# v2.0.10

### Security
- Fix a bug where blocked users were still able to message modmail.

# v2.0.9

### Added 
- Support for custom blocked emoji and sent emoji
- Use the `config set blocked_emoji` or `sent_emoji` commands.

### Quick Fix
- Support multiple image and file attachments in one message
- This is only possible on mobile so its good to handle it in code.

# v2.0.8

Improvements in commands and new config options available.

### Added 
- Added the ability to use your own log channel 
    - You can do this via the `config set log_channel_id <id>` command.
- Added the ability to use your own main inbox category.
    - You can do this via the `config set main_category_id <id>` command.

### Changed
- You now have the ability to supply a reason when blocking a user. 
- Blocked users are now stored in the database instead of in the channel topic.
    - This means you can delete the top channel in the modmail category now. (Migrate first though.)

# v2.0.7

New command and improvements in bot update message interfaces. 

### Added 
- Added a changelog command to view the bot's changelog within discord.

### Changed
- Update command now shows latest changes directly from the [CHANGELOG.md](https://modmail.tk/) in the repo.
- Auto update messages also show latest changes from repo.
- Remove latest changes section from the `about` command.

# v2.0.6

### Fixed
- Fix logs sending duplicated thread close logs.
- The bot will now tell you that a user is no longer in the server when you try to reply to a thread.
    - Before this, it looked like you replied to the thread but in reality the message didnt get sent.

# v2.0.5

### Changed
- Alias command now checks if you are adding a valid alias - command combo.
- Deleting a channel manually will now correctly close the thread and post logs.

# v2.0.4

### Fixed
- Fixed a one off bug where the channel topic dissapears, but modmail operations should still continue
- Fixed linked_message_id issues.

# v2.0.3

Fixed some issues with how data is displayed in the info embed.

### Fixed
- Thread creation embed now shows the correct amount of past logs. 
- If using a seperate server setup, roles in the info embed now are shown as names instead of mentions.
    - This is due to the fact that you can't mention roles across servers.

# v2.0.2

### Security
- Made the logs command require manage messages permissions to execute. 
    - Before this patch, anyone could use the logs commands.

# v2.0.1

Bug fixes and minor improvements.

### Changed
- Improved block/unblock commands.
    - They now take a wider range of arguments: Usernames, nicknames, mentions and user IDs.

### Fixed
- Setup command now configures permissions correctly so that the bot will always be able to see the main operations category.

# v2.0.0

This release introduces the use of our centralized [API service](https://github.com/kyb3r/webserver) to enable dynamic configuration, auto-updates, and thread logs. To use this release you must acquire an API token from https://modmail.tk. Read the updated installation guide [here](https://github.com/kyb3r/modmail/wiki/installation).

### Changed
- Stability improvements through synchronization primitives 
- Refactor thread management and code
- Update command now uses `api.modmail.tk` 
- Removed `archive` command
    - Explanation: With thread logs (that lasts forever), there's no point in archiving.
- `contact` command no longer tells the user you messaged them 👻 

### Fixed
- Status command now changes playing status indefinitely

### Added
- Dynamic help command (#84)
- Dynamic configuration through `api.modmail.tk` 
- Thread logs via `logs.modmail.tk` (#78)
    - `log` command added
- Automatic updates (#73)
- Dynamic command aliases and snippets (#86)
- Optional support for using a seperate guild as the operations center (#81)
- NSFW Command to change channels to NSFW (#77)

# v0.0.0