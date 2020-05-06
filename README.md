## Discord interactive chat bot assembled using [discord.py](https://github.com/Rapptz/discord.py) and [DialoGPT](https://github.com/microsoft/DialoGPT).

### Requirements:
- Ubuntu terminal
- Discord account
- At least 2GB of RAM to run DialoGPT-small model

### Installation of dependencies:
#### In Ubuntu terminal run following commands.
```
$ sudo apt-get update
$ sudo apt-get install python3-pip libffi-dev libnacl-dev python3-dev
```
Change root password (if you know what it is ignore this step).
```
$ passwd 
```
Create user from which you are going to run bot to not run bot as root.
```
$ sudo adduser bot
$ su - bot
$ pip3 install -U torch==1.4.0+cpu torchvision==0.5.0+cpu -f https://download.pytorch.org/whl/torch_stable.html
$ pip3 install -U discord.py
$ pip3 install -U transformers
```

### Alternatively if installation doesn't work follow instructions from:
- [On pytorch.org/get-started/locally/ you can even choose which operating system you are going to use and it will show command to run.](https://pytorch.org/get-started/locally/)
- [There is how to install and run first quick example in README file on github.com/Rapptz/discord.py](https://github.com/Rapptz/discord.py)
- [On github.com/microsoft/DialoGPT you can find out how to train models and install dependencies](https://github.com/microsoft/DialoGPT)


### Generating Discord Token:
- Go to https://discordapp.com/developers/applications
- Click "New Application"
- Name it whatever you want (i named mine "ai-bot")
- Click "Create"
- Go to "Bot" tab (it's on the left side under settings)
- Click "Add Bot"
- Alert with "ADD A BOT TO THIS APP?" will appear, click "Yes, do it!"
- Under Token click "Copy" for the next step

### Setting up environment variable:
```
$ echo "export DISCORD_TOKEN=paste_your_token_here" >> ~/.bash_profile
$ source ~/.bash_profile
```

### Adding bot to your server and giving him permissions:
- Go back to your application view (if you haven't closed it from step "Generating Discord Token" you can skip sub steps for this bullet) 
    - Go to https://discordapp.com/developers/applications
    - Select your app under "My Applications" (mine was "ai-bot")
- Go to OAuth2 tab (it's on the left side under settings)
- Click on button "Add Redirect"
    - Paste http://localhost in the field
    - Alert "Careful — you have unsaved changes!" will come up      
        - Click on "Save Changes" button
- Under "OAuth2 URL Generator"
    - Click on "SELECT REDIRECT URL" and choose http://localhost from dropdown
- Under "SCOPES" select:
    - "bot"
- Under "BOT PERMISSIONS" select:
    - Send Messages
    - Read Message History
- From "SCOPES" area copy link 
- Paste copied link into your browser and select server you want to invite bot to
- Click continue
- Click Authorize 
- Pass capcha
- Go to server you invited your bot
- Depending on your server settings you might have to modify bot role to have permissions to use the channel and read / send messages

### Running bot:
- Go to terminal and run:
```
$ wget https://raw.githubusercontent.com/Apurer/interactive-chat-bot/master/ai-bot.py
$ python3 ai-bot.py
```
- To stop bot from running press: CTRL + C

### To run in bot background
- Go to terminal and run:
```
$ chmod +x ai-bot.py
$ nohup ~/ai-bot.py &
```
- To stop bot from running run command:
```
$ pkill -f ai-bot.py
```