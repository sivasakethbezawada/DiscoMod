# Discord Server Management Bot

## Table of Contents
- [Purpose](#purpose)
- [Target Audience](#target-audience)
- [Features](#features)
- [Data Flow](#data-flow)
- [System Design](#system-design)
- [Development Schedule](#development-schedule)
- [Installation](#installation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Purpose
The Discord Server Management Bot is designed to assist server administrators and moderators with automation tools to streamline management tasks. It provides features like moderation, user engagement, analytics, and customization to enhance the server experience.

## Target Audience
- **Server Administrators**: Manage large or small Discord servers and need automation tools.
- **Moderators**: Enforce rules and maintain order in the server.
- **Community Managers**: Focus on engagement and growth of the server.
- **Developers**: Extend the bot's functionality with custom commands or integrations.

## Features
### Core Features
1. **Moderation Tools**
   - Auto-moderation (banning, muting, kicking users)
   - Profanity filter
   - Spam detection
2. **User Engagement**
   - Welcome messages for new users
   - Leveling system with role-based rewards
   - Custom commands for fun or utility
3. **Analytics**
   - Server activity tracking (messages sent, active users)
   - User growth statistics
4. **Customization**
   - Custom roles and permissions
   - Configurable prefixes and commands
5. **Utility**
   - Polls and voting systems
   - Reminders and scheduling
   - Integration with external APIs (weather, news, etc.)

### Advanced Features (Optional)
- **Dashboard**: Web-based interface for configuration and analytics.
- **Multi-Server Support**: Manage multiple servers from a single bot instance.
- **Logging**: Log moderation actions and server events for accountability.


## Data Flow
1. **User Interaction**
   - Users send commands in the Discord server.
   - The bot listens for commands using discord.py.
2. **Command Processing**
   - The bot validates the command and checks user permissions.
   - The bot executes the command (moderation, analytics, etc.).
3. **Data Storage**
   - User levels, logs, and configurations are stored in the database.
4. **Dashboard Interaction (Optional)**
   - Admins use a web dashboard for bot configuration and analytics.
   - The dashboard communicates with the bot’s backend via an API.

## System Design
### Components
1. **Bot Core**
   - Handles command parsing and execution.
   - Interacts with the Discord API via discord.py.
2. **Database**
   - Stores user data, logs, and server configurations.
3. **Dashboard (Optional)**
   - Provides a web interface for bot management.
4. **API Layer (Optional)**
   - Connects the bot and dashboard for data exchange.

### Architecture
- **Modular Design**: Separate modules for moderation, analytics, customization.
- **Event-Driven**: The bot reacts to events like messages and user joins.
- **Scalable**: Uses a cloud-based database and hosting for growth.


## Command List
### Debug Commands
- `/botinfo` Checks how many servers the bot is in.
- `/botsuggestion` Submits a suggestion directly to the bot's Discord server.
- `/bugreport` Submits a bug report directly to the bot's Discord server.
- `/discordserver` Sends an invite link to the bot's support server.
- `/invitelink` Sends the invite link for the bot.
- `/ping` Displays the bot's current latency in ms.
- `/serversettings` Sends current bot settings for this server.
### Fun Commands
- `/approved` Approves your profile picture or someone else's.
- `/blur` Blurs your profile picture or someone else's.
- `/dogfact` Sends a lovely dog fact.
- `/catfact` Same as dogfact, except it's for cats.
- `/contrast` Adds contrast effect to your profile picture or someone else's.
- `/deepfry` Add deepfried effect to your profile picture or someone else's.
- `/define` Looks up a term in the dictionary.
- `/nasanews` Looks up an astronomy-related term on NASA's Website and returns a fact about it.
- `/weather` Tells you information about the weather in a given location.
- `/yomomma` Sends a your mom joke to someone.
### Info Commands
- `/avatar` Displays the avatar of a user.
- `/help` Displays a list of all available commands along with their usage.
- `/serverinfo`  Displays information about the server you're in.
- `/userinfo` Displays information about a user's account account.
### Staff Commands
- `/addnote` Adds an admin note on someone's account. All staff members will be able to view this note.
- `/ban` Restricts a user's access to the server.
- `/baninfo` View details about a banned user.
- `/checknames` Check a member's previous nicknames.
- `/clear` Bulk deletes a certain amount of messages.
- `/delnote` Deletes a note from a user.
- `/delsuggestion` Deletes a suggestion.
- `/disablecmd` Disables a command from the server.
- `/editnote` Edits a note from a user.
- `/enablecmd` Enables a command from the server.
- `/kick` Kicks a user out of the server.
- `/mute` Restricts a user from sending messages.
- `/muteinfo` View details about a muted member.
- `/record` Displays how many punishments a user has ever received on the server.
- `/remindme` Sets a timer for a reminder.
- `/report` Submits a report to the staff's logs channel.
- `/serversuggestion` Submit a server suggestion.
- `/setlogschannel` Sets a custom channel where moderation logs will be sent.
- `/suggestion` Accept or decline a suggestion from your suggestion channel.
- `/suggestionchannel` Sets a channel for suggestions to be sent in.
- `/togglemsglogs` Toggles message logs on/off.
- `/unban` The username of the banned user.
- `/unmute` Removes a user's muted status earlier.
- `/viewnotes` Shows all notes linked to a user from this server.
- `/warn` Sends a warning message to a user.
### Role Commands
- `/rolepicker` Creates a menu that automatically assigns roles to users that react to it.
- `/addroletorp` Adds a role option to an existent role picker.
- `/removerolefromrp` Removes a role option from an existent role picker.
- `/disablerp` Disables an existent role picker.
- `/enablerp` Enables a disabled role picker.
- `/giverole` Adds a role to a user.
- `/takerole` Removes a role from a user.
### Welcome Commands
- `/setwelcomechannel` Sets a custom channel where newcommers will receive a welcome message.
- `/setleavechannel` Sets a custom channel where leaving members will be logged.
- `/welcomemessage` Sets a custom welcome message to be displayed when someone joins the server.
- `/leavemessage` Sets a custom good bye message for those leaving the server.
- `/welcomedm` Sets a custom welcome message that will be inboxed to new users.
- `/welcomerole` Sets a role to be assigned to new users when they join the server.
- `/togglewelcomemsg` Toggles welcome messages on/off.
- `/toggleleavemsg` Toggles leave messages on/off.
- `/togglewelcomedm` Toggles welcome DMs on/off.

## Usage
- Invite the bot to your Discord server.
   You can invite my bot running on the latest version [from here](https://discord.com/oauth2/authorize?client_id=723094801175806024&permissions=268561494&scope=bot%20applications.commands).

## Contributing
1. Fork the repository.
2. Create a new branch (`feature-branch`).
3. Commit changes and push to your fork.
4. Open a pull request.

## License
This project is licensed under the [MIT License](LICENSE).

