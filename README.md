# Discord.py Bot Documentation

This documentation will guide you through the process of creating a Discord bot using the `discord.py` library. <br>
We'll cover everything from setting up the environment to deploying the bot, with example code provided at each step. <br>
Let's make this a fun and easy learning experience! <br>


## 1 - Initialize
### 1.1: Installing `discord.py`
First, you need to install the `discord.py` library. Open your terminal and run:
```bash
pip install discord.py
```
### 1.2: Deploying your bot
Read this article bellow to learn how to create, invite, and deploy
your bot to your server. <br>
[https://builtin.com/software-engineering-perspectives/discord-bot-python](https://builtin.com/software-engineering-perspectives/discord-bot-python)<br>
[https://medium.com/@thomaschaigneau.ai/building-and-launching-your-discord-bot-a-step-by-step-guide-f803f7943d33](https://medium.com/@thomaschaigneau.ai/building-and-launching-your-discord-bot-a-step-by-step-guide-f803f7943d33)<br>
[https://www.freecodecamp.org/news/create-a-discord-bot-with-python/](https://www.freecodecamp.org/news/create-a-discord-bot-with-python/)

## 2 - Complicated Manners
### 2.1: Invite Errors
- Insufficient information <br>
  Sometimes you encountered a very strange error just because you don't enable all of this settings<br><br>
  ![image](https://github.com/user-attachments/assets/acf408fa-876b-489e-b1fa-2121a35de3d0)<br><br>
  You need to **ENABLE** all of the settings to make the bot works<br><br>
  ![image](https://github.com/user-attachments/assets/48fc5555-12b1-48b0-8026-c161db6da5fa)

- Buttons <br>
first o first you need to install additional pacakge to makes this work
install this package :
```bash
$ pip install git+https://github.com/Rapptz/discord.py.git@master
```
<br>
After it, add this code to your command code

```py
@bot.command()
async def button(ctx):
  view = discord.ui.View()
  item = discord.ui.Button(style=discord.ButtonStyle.blurple, label="Click Me", url="https://google.com")
  view.add_item(item=item)
  await ctx.send("This message has a button!", view=view)
```

or maybe some complicated one like this :
```py
# Define a simple View that gives us a confirmation menu
class Confirm(discord.ui.View):
    def __init__(self):
        super().__init__()
        self.value = None

    # When the confirm button is pressed, set the inner value to `True` and
    # stop the View from listening to more input.
    # We also send the user an ephemeral message that we're confirming their choice.
    @discord.ui.button(label='Confirm', style=discord.ButtonStyle.green)
    async def confirm(self, interaction: discord.Interaction, button: discord.ui.Button):
        await interaction.response.send_message('Confirming', ephemeral=True)
        self.value = True
        self.stop()

    # This one is similar to the confirmation button except sets the inner value to `False`
    @discord.ui.button(label='Cancel', style=discord.ButtonStyle.grey)
    async def cancel(self, interaction: discord.Interaction, button: discord.ui.Button):
        await interaction.response.send_message('Cancelling', ephemeral=True)
        self.value = False
        self.stop()
```

on this particular code, we subtract the `@discord.ui.button`.

you could find other example on : [https://github.com/Rapptz/discord.py/tree/master/examples/views](https://github.com/Rapptz/discord.py/tree/master/examples/views)
