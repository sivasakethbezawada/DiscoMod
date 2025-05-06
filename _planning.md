# DiscoMod Bot Planning

## Requirements

**Functional Requirements**  
- Slash-command interface for key features: moderation (ban, mute, kick), information (serverinfo, userinfo), fun (dogfact, joke), utility (weather, suggestions).  
- Persistent storage of configurations and actions in MongoDB.  
- Welcome message customization per guild.  
- Reaction-role menus with dynamic configuration.  
- Command rate-limiting and logging for abuse prevention.  
- Suggestions workflow with voting and closure.

**Non-Functional Requirements**  
- High availability: automatic reconnection to Discord and MongoDB.  
- Scalability: support for sharding when in many guilds.  
- Observability: structured logs and health-check endpoint.  
- Security: environment-based secrets management; permission checks on commands.  
- Maintainability: clear project structure, linting, tests, and documentation.

## Personas

- **Server Administrator**  
  Manages bot installation, sets up welcome channels, configures roles, and oversees moderation settings.

- **Moderator**  
  Uses moderation commands (ban/kick/mute/unmute), reviews punishment records, and ensures community guidelines.

- **General Member**  
  Invokes fun and utility commands (dogfact, joke, weather) and participates in suggestions and polls.

- **Developer/Contributor**  
  Extends bot functionality, writes new commands, maintains CI/CD workflows, and ensures code quality.

## System Design

**Architecture Components**  
- Discord Client: connects via `discord.js`, handles `interactionCreate` and other events.  
- Command Modules: independent files exposing command metadata and execution logic.  
- Event Handlers: dynamically loaded listeners for Discord events (guildMemberAdd, messageReactionAdd, etc.).  
- Database Layer: Mongoose models for punishments, mutes, welcome settings, role pickers, suggestions, and usage logs.  
- Scheduler: job system for timed actions (unmute expiration, log purges).  
- Utilities: logger, embed builder, rate limiter, and scheduler helper.  
- Deployment: Dockerized service with GitHub Actions CI/CD and optional Kubernetes/SSH deployment.

**Data Flow**  
1. Bot startup loads configuration and connects to Discord and MongoDB.  
2. Slash commands are registered or updated via a deployer script.  
3. Incoming interactions trigger command handlers, which perform business logic and database operations.  
4. Events (member join, reactions) invoke corresponding handlers to send messages or update roles.  
5. Scheduled jobs run periodically to handle time-based workflows and cleanup.

## Use Cases

- **UC1: Welcome New Member**  
  1. Admin runs `/setwelcomechannel #welcome` and `/setwelcomemessage Welcome {user} to {guild}!`.  
  2. A new member joins, `guildMemberAdd` sends the formatted welcome embed.

- **UC2: Moderate a User**  
  1. Moderator issues `/mute @user 10m Spamming`.  
  2. Bot assigns “Muted” role, records expiration in DB, and schedules unmute.  
  3. After 10 minutes, scheduler removes role and logs action.

- **UC3: Reaction Role Menu**  
  1. Admin runs `/rolepicker create #roles 🟢@Green 🔴@Red`.  
  2. Bot posts an embed with reactions.  
  3. Members react to receive or remove the specified roles.

- **UC4: Fun Interaction**  
  1. User invokes `/dogfact`.  
  2. Bot fetches a random fact from an external API and replies with an embed.

- **UC5: Suggestion Workflow**  
  1. User runs `/suggest Add new channel`.  
  2. Bot posts suggestion in configured channel with 👍/👎 reactions.  
  3. Admin uses `/suggestclose  accepted “Great idea!”` to update status.

## Configuration & Environment

**Required Environment Variables**  
- BOT_TOKEN  
- MONGODB_URI  
- OPENWEATHER_API_KEY  
- LOG_CHANNEL_ID  
- ENV (development|production)

**MongoDB Models**  
- Punishment (userId, type, reason, moderatorId, timestamp)  
- MutedMember (userId, expiresAt, moderatorId)  
- WelcomeSetting (guildId, channelId, messageTemplate)  
- RolePicker (guildId, messageId, roleIds)  
- Suggestion (suggestionId, userId, channelId, status, reason)

## Risks & Mitigations

- **Model Drift**: Changes to Discord API could break event handlers.  
  Mitigation: automated integration tests and dependency updates.

- **Rate Limits**: High traffic may trigger Discord rate limits.  
  Mitigation: implement internal rate-limiting and backoff strategies.

- **Data Loss**: MongoDB outages risk losing stateful configurations.  
  Mitigation: enable MongoDB replication and periodic backups.

## Roadmap & Milestones

1. Project scaffold, config loader, and basic client setup.  
2. Core commands (ping, botinfo, serverinfo, userinfo).  
3. Database integration and moderation commands.  
4. Fun/utility commands and scheduler.  
5. Reaction roles, suggestions, and welcome system.  
6. Testing, linting, and CI/CD pipelines.  
7. Documentation and localization support.  