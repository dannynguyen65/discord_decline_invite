# discord_decline_invite_script
Python script to automate declining invitations in Discord
import discord
from discord.ext import commands

TOKEN = 'YOUR_DISCORD_TOKEN'
GUILD_ID = 1234567890  # Replace with the server's identifier where you want to decline invitations

bot = commands.Bot(command_prefix='!')

@bot.event
async def on_ready():
    print(f'The bot {bot.user.name} is ready!')

@bot.event
async def on_invite_create(invite):
    guild = bot.get_guild(GUILD_ID)
    if invite.guild.id == guild.id:
        await invite.delete()
        print(f'Rejected an invitation to the server {guild.name}')

bot.run(TOKEN)
