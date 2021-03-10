# Snuske
A Discord bot for the World of Warcraft server Warmane used by thousands of people worldwide.

Thread on Warmane can be found here: https://forum.warmane.com/showthread.php?t=370139

## Description
I made this a few years back (November 2017). I basically made it in a night and published it as a Discord bot, and I never looked back at the code. Today I would've probably rewritten a lot of the functions, because what I have here is really, really ugly. But, it works quite well.

As of 10th of March 2021 at 10:58 PM (hey it's my birthday in an hour) 288.879 commands have been executed by this bot, and over 1200 servers have it installed with 95.000+ members in total.

## Installation
To run this on your own server, you need a few things installed first.

* MongoDB
* NodeJS
* NPM

Once you have those things installed, clone this repository and restore the dump from the `dump/` directory:

```
mongorestore -d warmane -c items dump/items.bson
```

The dump contains a list of all World of Warcraft 3.3.5a items, as well as their GearScore, which was calculated by a script I made by reverse engineering the original GearScore AddOn. The items are important, because we actually need some of the item's stats to determine the GearScore (as you can see in the `getGearScore` function).

Once the MongoDB database has been restored, you need to open `app.js` and edit a few things. You need the username, the password, and the database name (if you used the `mongorestore` command above, the database will be `warmane`).

Then you need to create a Discord application. I cannot remember exactly what you need to do, but here's a link to the page: https://discord.com/developers/applications

You need to get the Bot token, which can be found here:

![image](https://user-images.githubusercontent.com/1304665/110703265-d6759c00-81f3-11eb-9ab6-0e79b73eb9af.png)

and replace that in the `app.js` file as well.

Next, simply install the packages by running:

```
npm install
```

Once you're done, run `node app.js` and it will start the bot. I would personally run it as a service, but you can do it however you want.

## Find your bot invitation link
A regular invitation link looks like this:

```
https://discordapp.com/oauth2/authorize?&client_id=369568063781339152&scope=bot&permissions=0
```

If you go to your bot's Discord developer page, you can find the ID for your bot here:

![image](https://user-images.githubusercontent.com/1304665/110704096-d1651c80-81f4-11eb-9fb7-16ffa9a14ba3.png)

Simply replace the `client_id` in the URL with your bot's ID.
