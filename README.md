# 🛡️ Ryzen X Prime Security Bot

**Advanced Discord Server Protection • AntiNuke • AntiRaid • AutoMod**

Ryzen X Prime Security Bot is a feature-rich Discord security and moderation bot built to help protect Discord communities against server nuking, raid attacks, spam, unauthorized bot additions, and moderation abuse.

Powered by **Node.js, Discord.js v14, MongoDB, and LMDB**, the bot combines automated security systems, moderation tools, verification features, event logging, and a scalable hybrid-sharding architecture.

---

## ✨ Features

### 🛡️ Advanced Security
- **AntiNuke Protection** — Helps detect and respond to potentially destructive server actions.
- **AntiRaid System** — Security controls for suspicious joining activity and raid attempts.
- **Unauthorized Bot Protection** — Helps protect servers against unapproved bot additions.
- **Security Configuration** — Configure supported security settings for individual servers.
- **Audit Log Monitoring** — Monitor relevant Discord audit log events.
- **Recovery Actions** — Perform supported moderation or recovery actions when configured correctly.

### 🤖 AutoMod
- Automated moderation tools for supported message and member events.
- Spam detection and prevention features.
- Configurable moderation responses.
- Event-driven monitoring for suspicious activity.

### ✅ Verification
- Member verification functionality.
- Verification-related event handling.
- Tools to help manage the member onboarding process.

### 🔨 Moderation
- Server moderation commands.
- Member management utilities.
- Moderation-related logging and event handling.
- Owner-only management tools.

### 📋 Logging and Utilities
- Security and moderation event handling.
- Member join and message event monitoring.
- Utility and information commands.
- Report command integration with a configured Discord channel.
- Emoji synchronization utilities.

### ⚡ Performance and Architecture
- **Discord.js v14** for Discord API integration.
- **Hybrid Sharding** for scalable bot operation.
- **MongoDB** for persistent application data.
- **LMDB** for local, high-performance state and caching.
- **HTTP Health Server** on port `5000`.
- **Canvas and Canvacord** for supported image-generation features.

> Feature availability and behavior depend on the implementation, configuration, permissions, and Discord API capabilities.

---

## 🧰 Technology Stack

| Technology | Purpose |
|---|---|
| Node.js | JavaScript runtime |
| Discord.js v14 | Discord bot framework |
| MongoDB | Persistent data storage |
| quickmongo | MongoDB integration |
| LMDB | Local database and state storage |
| Hybrid Sharding | Bot process scaling |
| Canvas | Image rendering |
| Canvacord | Discord-related image utilities |

---

## 📁 Project Structure

```text
RyzenXPrimeSecurityBot/
├── src/
│   ├── app.js
│   ├── cluster.js
│   ├── config.json
│   ├── emojis.json
│   ├── commands/
│   │   ├── antinuke/
│   │   ├── antiraid/
│   │   ├── automod/
│   │   ├── verification/
│   │   ├── moderation/
│   │   ├── owner/
│   │   └── utility/
│   ├── events/
│   ├── database/
│   │   └── lmdb/
│   └── utils/
│       └── emojiSync.js
├── package.json
└── README.md
```

*The directory names above illustrate the project organization; actual command subdirectories may differ.*

### Core Files

- `src/app.js` — Initializes the Discord client, database connection, command and event loaders, and HTTP health server.
- `src/cluster.js` — Starts the bot through the hybrid-sharding entry point.
- `src/config.json` — Contains bot configuration and integration settings.
- `src/commands/` — Houses security, moderation, verification, utility, and owner commands.
- `src/events/` — Contains event handlers for security, automod, logging, messages, and member activity.
- `src/database/lmdb/` — Stores local LMDB database state.
- `src/utils/emojiSync.js` — Provides emoji synchronization functionality.
- `src/emojis.json` — Contains emoji definitions.
- `package.json` — Defines dependencies and application scripts.

---

## 📋 Requirements

Before installing, make sure the environment has:

- Node.js 22 or another version compatible with the project's dependencies.
- npm.
- MongoDB Atlas or a reachable MongoDB server.
- A Discord application and bot token.
- Git, if cloning from GitHub.
- Linux build tools and graphics libraries for native Canvas dependencies.

**Recommended deployment:** Debian or Ubuntu VPS.

---

## 🚀 Installation

### 1. Clone the repository

```bash
git clone https://github.com/ItzMePara9/RyzenXSecurity
cd RyzenXSecurity
```

Replace the placeholders with the actual repository URL and directory name.

### 2. Install system dependencies

On Debian or Ubuntu:

```bash
sudo apt update

sudo apt install -y \
  git curl build-essential python3 make g++ \
  libcairo2-dev libjpeg-dev \
  libpango1.0-dev libgif-dev librsvg2-dev
```

These packages provide common native build dependencies required by Canvas.

### 3. Install Node.js

Install Node.js 22 using the official NodeSource setup:

```bash
curl -fsSL https://deb.nodesource.com/setup_22.x -o /tmp/nodesource_setup.sh
sudo bash /tmp/nodesource_setup.sh
sudo apt install -y nodejs
```

Verify the installation:

```bash
node --version
npm --version
```

### 4. Install project dependencies

```bash
npm install
```

Review `package.json` for the available scripts and dependency requirements.

### 5. Configure the bot

Open the configuration file:

```bash
nano src/config.json
```

Example configuration:

```json
{
  "token": "YOUR_DISCORD_BOT_TOKEN",
  "prefix": ";",
  "MONGO": "mongodb+srv://username:password@cluster.mongodb.net/ryzenxbot",
  "owner": [
    "YOUR_DISCORD_USER_ID"
  ],
  "extraowners": [],
  "reportChannel": "DISCORD_CHANNEL_ID",
  "support_server_link": "https://discord.gg/your-server",
  "inviteURL": "https://discord.com/oauth2/authorize?client_id=BOT_ID&permissions=8&scope=bot%20applications.commands"
}
```

Replace every placeholder with the appropriate value.

| Setting | Description |
|---|---|
| `token` | Discord bot token |
| `prefix` | Prefix used for prefix-based commands |
| `MONGO` | MongoDB connection URI |
| `owner` | Discord user IDs authorized for owner-only commands |
| `extraowners` | Optional additional owners |
| `reportChannel` | Channel ID for report functionality |
| `support_server_link` | Discord support server invitation |
| `inviteURL` | Bot authorization URL |

**Security recommendation:** Keep credentials out of public repositories. Use environment variables wherever the application supports them, and ensure the configuration file does not contain real secrets before committing.

### 6. Start the bot

For the hybrid-sharded entry point:

```bash
npm start
```

For the non-sharded entry point, if defined in `package.json`:

```bash
npm run start:no-shard
```

The actual command names depend on the scripts configured in `package.json`.

---

## 🔐 Environment Variables

The application supports environment variables for the Discord token and MongoDB connection URL.

On Linux, configure them for a test session:

```bash
export DISCORD_TOKEN="YOUR_DISCORD_BOT_TOKEN"
export MONGODB_URL="YOUR_MONGODB_CONNECTION_STRING"

npm start
```

Environment variables take precedence over corresponding configuration values when the application is implemented to read them that way.

Do not commit `.env` files, service credentials, database passwords, or real Discord tokens to GitHub.

---

## 🤖 Discord Application Setup

### 1. Create a Discord application

Visit the [Discord Developer Portal](https://discord.com/developers/applications), create an application, and add a bot user.

### 2. Configure privileged intents

Under **Bot → Privileged Gateway Intents**, enable the intents required by the implementation:

- **Server Members Intent** — For member join and member-related features.
- **Message Content Intent** — For message-based moderation and prefix commands that inspect message content.
- **Presence Intent** — Only if the bot uses presence data.

Some intents may require approval for eligible verified applications.

### 3. Invite the bot

Generate an OAuth2 authorization URL using the `bot` and `applications.commands` scopes.

Grant only the permissions required by the features being used. Although Administrator may simplify setup, it gives the bot extensive control over a server and should not be granted unnecessarily.

### 4. Configure role hierarchy

Move the bot's highest role above the roles it must manage.

Depending on enabled features, required permissions may include:

- View Audit Log
- Manage Roles
- Manage Channels
- Manage Webhooks
- Ban Members
- Kick Members
- Moderate Members
- Manage Messages
- View Channels
- Send Messages
- Read Message History

Permissions alone cannot override Discord's role hierarchy restrictions.

---

## 🗄️ MongoDB Setup

Ryzen X Prime Security Bot uses MongoDB for persistent data through `quickmongo`.

### MongoDB Atlas

1. Create a cluster in [MongoDB Atlas](https://www.mongodb.com/atlas).
2. Create a database user with a strong password.
3. Configure network access to allow the bot's server to connect.
4. Copy the connection URI.
5. Set the URI through `MONGODB_URL` or the supported configuration field.
6. Start the bot and check the logs for database connection errors.

Example URI:

```text
mongodb+srv://username:password@cluster.mongodb.net/ryzenxbot
```

Use a properly URL-encoded password if it contains reserved URI characters.

### Local MongoDB

If MongoDB is installed on the same server, a typical connection URI is:

```text
mongodb://127.0.0.1:27017/ryzenxbot
```

Ensure the MongoDB service is running and accessible to the bot.

---

## 🖥️ VPS Deployment with systemd

For production deployments, a `systemd` service can automatically start the bot and restart it after unexpected exits.

### 1. Prepare the installation directory

Assuming the repository is located at `/opt/ryzenx-security-bot`:

```bash
sudo adduser --system --group \
  --home /opt/ryzenx-security-bot ryzenxbot

sudo chown -R ryzenxbot:ryzenxbot \
  /opt/ryzenx-security-bot
```

Install dependencies and complete configuration before enabling the service.

### 2. Create an environment file

```bash
sudo install -m 600 /dev/null \
  /etc/ryzenx-security-bot.env

sudo nano /etc/ryzenx-security-bot.env
```

Add:

```bash
DISCORD_TOKEN=YOUR_DISCORD_BOT_TOKEN
MONGODB_URL=YOUR_MONGODB_CONNECTION_STRING
NODE_ENV=production
```

Restrict access to this file because it contains credentials.

### 3. Create the service

```bash
sudo nano /etc/systemd/system/ryzenx-security-bot.service
```

Add:

```ini
[Unit]
Description=Ryzen X Prime Security Bot
After=network.target

[Service]
Type=simple
User=ryzenxbot
Group=ryzenxbot
WorkingDirectory=/opt/ryzenx-security-bot
EnvironmentFile=/etc/ryzenx-security-bot.env
ExecStart=/usr/bin/node src/cluster.js
Restart=on-failure
RestartSec=10

[Install]
WantedBy=multi-user.target
```

Verify that the application supports these environment variable names and that the configured Node.js path is correct.

### 4. Enable and start

```bash
sudo systemctl daemon-reload

sudo systemctl enable --now ryzenx-security-bot
```

Check the service:

```bash
sudo systemctl status ryzenx-security-bot
```

View live logs:

```bash
sudo journalctl -u ryzenx-security-bot -f
```

Restart after configuration changes:

```bash
sudo systemctl restart ryzenx-security-bot
```

---

## ❤️ Health Endpoint

The application starts an HTTP health server on port `5000`.

When the health server is configured to listen on the loopback interface, test it locally:

```bash
curl http://127.0.0.1:5000
```

If it is configured to listen on an externally reachable interface, the endpoint may be reachable at:

```text
http://YOUR_SERVER_IP:5000
```

The exact response and health-check behavior depend on the implementation. Avoid exposing the endpoint publicly without reviewing its routes, access controls, and firewall rules.

---

## 🛠️ Troubleshooting

### Bot does not come online

- Confirm the Discord token is valid.
- Check the bot's startup logs.
- Verify that outbound connections to Discord are permitted.
- Confirm that the required Gateway intents are enabled.
- Check that dependencies installed successfully.

### MongoDB connection fails

- Verify the connection URI.
- Check MongoDB Atlas network access rules.
- Confirm the database username and password.
- Verify that the server can reach the database host.

### Commands do not work

- Check the configured command prefix.
- Confirm that the command is registered and loaded.
- Verify application command synchronization if using slash commands.
- Review Discord permissions and required intents.

### Security actions fail

- Check the bot's role position.
- Confirm the relevant Discord permissions.
- Verify audit log access.
- Test the feature with controlled actions in a private server.

### Canvas installation errors

- Verify that the required native libraries are installed.
- Review the Node.js version and package compatibility.
- Inspect npm's installation output for missing system dependencies.

---

## 🔒 Security Best Practices

- Never publish Discord bot tokens or MongoDB credentials.
- Keep secrets out of Git history, not just out of the latest commit.
- Use a restricted MongoDB database account.
- Grant only the Discord permissions needed by the enabled features.
- Back up important MongoDB data and LMDB files.
- Test AntiNuke, AntiRaid, and AutoMod in a private test server before production use.
- Monitor application logs and investigate unexpected crashes.
- Review privileged owner commands carefully.
- Avoid running the bot as root.
- Keep Node.js and project dependencies updated.
- Review exception handling to ensure critical failures are logged and visible.

If a credential has been exposed, revoke or rotate it immediately.

---

## 💾 Backup and Recovery

The project uses MongoDB for persistent application data and LMDB for local state.

Recommended backup practices:

- Back up the MongoDB database regularly.
- Stop or safely quiesce the application before copying LMDB files unless the database implementation supports consistent live backups.
- Store backups outside the application directory.
- Restrict access to backup files.
- Periodically test restoration procedures.

Do not assume that copying the source repository alone preserves the bot's runtime data.

---

## 🗺️ Roadmap

Potential future improvements:

- [ ] Web-based security dashboard.
- [ ] Advanced raid analytics.
- [ ] Improved security event reporting.
- [ ] Configurable per-server security profiles.
- [ ] Expanded logging and observability.
- [ ] Automated backup management.
- [ ] Additional moderation integrations.

---

## 🤝 Contributing

Contributions, bug reports, and feature suggestions are welcome.

1. Fork the repository.
2. Create a feature branch.
3. Make the changes and test them.
4. Commit with a descriptive message.
5. Open a pull request explaining the changes.

Please avoid submitting credentials, private server data, or other sensitive information.

---

## 📜 License

No license has been specified here. Add a `LICENSE` file to clarify the permissions and restrictions that apply to using, modifying, and distributing this project.

Until a license is added, do not assume that the repository is licensed for unrestricted reuse.

---

## ⚠️ Disclaimer

Ryzen X Prime Security Bot is provided as a server administration and protection tool. Its effectiveness depends on configuration, permissions, implementation, and Discord API behavior.

No security bot can guarantee complete protection against every raid, exploit, or destructive action. Server administrators remain responsible for access control, backups, permissions, and incident response.

Use the bot responsibly and test security features before deploying them to production communities.

---

**Built for safer Discord communities. 🛡️**

*Ryzen X Prime Security Bot*
