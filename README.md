# Discord Server Manager Bot

## Overview
Discord Server Manager is a custom bot designed to provide functionality that is often missing from major Discord bots. This bot offers unique features for server management, channel organization, and message logging. It was developed with the assistance of Claude 3.5 Sonnet, refining and expanding upon initial concepts and scripts.

## Features
- **Server Setup**: Automatically set up server structure based on a configuration file.
- **Channel Tagging**: Mark channels with custom tags for easier management.
- **Message Logging**: Log messages from tagged channels, with customizable start points.
- **User Aliases**: Allow users to register aliases for use in logged messages.
- **Message Whitelisting**: Set up format requirements for messages to be logged.
- **Server Purging**: Ability to remove all custom channels and roles (use with caution).
- **Extension System**: Support for modular functionality through a custom extension system.

## Prerequisites
- Python 3.8 or higher
- pip (Python package manager)
- A Discord account and a registered Discord application/bot

## Installation

1. Clone the repository:
   ```
   git clone https://github.com/your-username/Discord-Server-Manager.git
   cd Discord-Server-Manager
   ```

2. Install the required Python packages:
   ```
   pip install -r requirements.txt
   ```

3. Create a `.env` file in the root directory with the following content:
   ```
   DISCORD_BOT_TOKEN=your_bot_token_here
   DATA_FILE=bot_data.json
   ```
   Replace `your_bot_token_here` with your actual Discord bot token.

4. (Optional) Create a `server_config.txt` file if you want to use the `!setup_server` command. Format:
   ```
   CATEGORY: Category Name
   CHANNEL: Channel Name | Channel Topic
   ROLE: Role Name, Color (in hex), Permission1, Permission2, ...
   ```

## Usage

1. Run the bot:
   ```
   python main.py
   ```

2. Once the bot is running and connected to Discord, you can use the following commands:
   - `!setup_server`: Set up the server based on `server_config.txt`
   - `!mark <tag>`: Mark the current channel with a tag
   - `!unmark <tag>`: Remove a tag from the current channel
   - `!log_tagged <tag> [message_id]`: Log messages from channels with the specified tag
   - `!register_alias <alias>`: Register an alias for yourself
   - `!set_whitelist <format1>, <format2>, ...`: Set message format whitelist
   - `!purge_server`: Remove all custom channels and roles (admin only, use with caution)
   - `!reload`: Reload all extensions (admin only)

## Extending the Bot

To add new features:
1. Create a new Python file in the `extensions` folder.
2. Define a class that inherits from `commands.Cog`.
3. Define your new commands within this class.
4. Add a `setup` function to add the Cog to the bot.

Example:
```python
from discord.ext import commands

class MyCog(commands.Cog):
    def __init__(self, bot):
        self.bot = bot

    @commands.command()
    async def mycommand(self, ctx):
        await ctx.send("This is a new command!")

async def setup(bot):
    await bot.add_cog(MyCog(bot))
```

## Contributing
Contributions to the Discord Server Manager bot are welcome! Please feel free to submit pull requests or create issues for bugs and feature requests.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgements
- Thanks to the Discord.py library developers.
- Special thanks to Claude 3.5 Sonnet for assistance in refining and expanding the bot's functionality.
