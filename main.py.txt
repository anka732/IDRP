import discord
from discord.ext import commands
import os

intents = discord.Intents.default()
intents.message_content = True

bot = commands.Bot(command_prefix="!", intents=intents)

@BOT.event
async def on_ready():
    print(f"Bot online sebagai {bot.user}")

@BOT.command()
async def ping(ctx):
    await ctx.send("Pong! 🏓")

@BOT.command()
async def halo(ctx):
    await ctx.send(f"Halo {ctx.author.mention} 👋")

@BOT.command()
async def info(ctx):
    await ctx.send(
        "🤖 Bot Info\n"
        "Nama: Bot Sederhana\n"
        "Versi: 1.0\n"
        "Dibuat dengan Python"
    )

@BOT.command()
async def say(ctx, *, text):
    await ctx.send(text)

@BOT.command()
async def help(ctx):
    await ctx.send(
        "📜 Daftar Command\n"
        "!ping → cek bot\n"
        "!halo → salam\n"
        "!info → info bot\n"
        "!say <teks> → bot ngomong\n"
    )

bot.run(os.getenv("TOKEN"))