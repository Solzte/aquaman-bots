<div align="center">

# Aquaman Bots

**A comprehensive, multi-module Discord server management ecosystem.**

</div>

---

## Prerequisites

- **Node.js** >= 18.0.0
- **MongoDB** (Local or Atlas)
- **Discord Application Tokens**

---

## Installation & Setup

1. **Install Dependencies:**

        npm install

2. **Configuration:**
   Update the core configuration file located at Global/Settings/System.js with your infrastructure parameters (Guild ID, MongoDB URI, and specific Bot Tokens).

3. **Initialize Storage:**
   For a fresh deployment, clear the existing giveaway state by overwriting Global/Settings/Server/Giveaways.json with an empty array:

        []

4. **Launch via PM2:**

        npm install -g pm2
        pm2 start ecosystem.config.js

---

## Process Management

| Command                         | Action                  |
| ------------------------------- | ----------------------- |
| `pm2 start ecosystem.config.js` | Bootstrap all modules   |
| `pm2 status`                    | View operational status |
| `pm2 logs`                      | Stream application logs |
| `pm2 restart all`               | Restart the ecosystem   |

---

## Module Architecture

| Module              | Purpose                                       |
| ------------------- | --------------------------------------------- |
| **Mainframe** | Core commands and baseline operations.        |
| **Elixir** | Auxiliary functions and supplementary tools.  |
| **Point** | Experience (XP) and points progression logic. |
| **Guardian Logger** | Centralized audit and server event logging.   |
| **Guardian Punish** | Automated moderation and penalty enforcement. |
| **Guardian Backup** | State preservation and data backup.           |
| **Welcomes** | Distributed greeting and onboarding daemon.   |

---

## Operational Requirements

- **Gateway Intents:** You must enable Presence, Server Members, and Message Content intents in the Discord Developer Portal for all active bots.
- **Segregation:** Each module requires its own distinct Discord Application and token.
- **Security:** Never commit your configuration files containing bot tokens to version control.
