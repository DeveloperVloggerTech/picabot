# picabot
A discord bot for didney worl who has an appetite for non-nutritive substances

## Dependencies
This discord bot uses discord.js, dotenv, googleapis, node-opus, and ytdl-core.  
These dependencies are part of the [package.json](https://github.com/aaronshappell/picabot/blob/master/package.json) and can be installed locally via npm.

## Installation and Running
How to install and run picabot for various systems/hosting options.  
The google api key isn't necessary but is required for the `yt` command to work.
### Locally
First install nodejs and npm. Download them for your system [here](https://nodejs.org/en/download/).  
You can then install the bot by cloning the git repo with `git clone https://github.com/aaronshappell/picabot.git`. Then you must install the necessary dependencies with `npm install` in the project directory. Make sure you have a `.env` file with your bot token and google api key as `BOTTOKEN` and `GOOGLEAPIKEY` respectively. See [example.env](https://github.com/aaronshappell/picabot/blob/master/example.env) for details.  
You can run the bot with `node ./` from within the project directory. It will print `Bot ready` when the bot is ready to recieve commands.
### Heroku
Make sure you have set your config variables in heroku (environment variables) with your bot token and google api key as `BOTTOKEN` and `GOOGLEAPIKEY` respectively. You also need to add a [ffmpeg buildpack](https://github.com/jonathanong/heroku-buildpack-ffmpeg-latest) to your project for voice to work.  
You can run the bot by pushing to your remote heroku repository or on the website. Doing so will automatically install the necessary dependencies for your dyno instance. On the resources tab of your heroku app turn off the web dyno and turn on the worker dyno. You can check the log with `heroku logs --tail` to verify that your bot is running and you will see `Bot ready`.  
**Note:** messages saved with the `save` command will not be permanently saved due to heroku's ephemeral file system and the dyno lifecycle.
### Google Compute Engine
Soon to come...

## Commands
### Current Commands
`!help <command> | -a or --all`: Gives you a list of commands you can use or details on specific command(s)  
`!bot`: Tells you information about the bot  
`!ping`: Pings the bot, useful for seeing if it's alive  
`!roll <amount>d<sides>+<modifier>`: Rolls DnD style dice  
`!8ball`: Asks a magic 8ball for a fortune  
`!save <key> <message>`: Saves a personalized message with a given key  
`!recall <key>`: Lists your saved messages or recalls a saved message with a given key  
`!delete <key>`: Deletes a saved message with a given key  
`!insult`: (NOT DONE) Call the bot to your voice channel to deliver a special insult  
`!addsong <link>`: Adds a song to the song queue via a youtube link  
`!yt <query>`: Searches for a youtube video to add to the song queue  
`!play`: Resumes the current song  
`!pause`: Pauses the current song  
`!prev <amount>`: Skips back in the queue by a certain amount of songs  
`!next <amount>`: Skips ahead in the queue by a certain amount of songs  
`!goto <index>`: Skips to a certain song in the queue by its index  
`!random`: Chooses a random song from the queue to play.  
`!clear <index>`: Clears the song queue or a specific song in the queue  
`!shuffle`: Toggles shuffling of the song queue  
`!autoremove`: Toggles autoremoving songs of the song queue  
`!song`: Gives you information about the currently playing song  
`!music`: Gives you a list of the songs currently in the queue  
### Example Command
A command in the commands object consists of three parts: usage, description, and its process.
```
"command": {
    "usage": "<argument>",
    "description": "Describes what the command does",
    "process": function(message, args){
        //Do stuff here
    }
}
```