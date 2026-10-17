# Import your leveling settings onto Sokora

!!!warning "Not available yet"
    This will release with Sokora 0.4.

A hard part of switching to a new and better bot (like Sokora) with a leveling system is that you probably were using another bot for this purpose before. This usually leaves you with three options:

* **Keep both bots**: one does what the other one could do. Easiest, but suboptimal.
* **Remove previous bot**: Optimal, but your leaderboard is lost, which your members won't like.
* **Remove Sokora**: Your leaderboard is kept, but you miss the best Discord bot. Not good!

However, **if you use MEE6, Tatsu, Lurkr or Amari for leveling, you're lucky!**

We can bring your leaderboard over to Sokora.

## Setting up your previous bot for import

This process depends on the bot you're migrating from.

### MEE6

You need to enable leaderboard visibility from your dashboard. Open the leaderboard settings in the MEE6 dashboard and enable the option `Make my server's leaderboard public`. Otherwise data cannot be imported.

### Tatsu

You need an API key, obtained by running `t!apikey` anywhere in the server to migrate.

### Lurkr

You need an API key, obtained from <https://lurkr.gg/docs/api#authentication>.

Additionally, you need to grant specific permissions for the server you want to import from. Check the same link, it describes this immediately after explaining how to get your API key.

Lastly, you need to manually change `Choose the visibility for the web leaderboard` in Lurkr’s dashboard to `Public`.

### Amari

You need an API key, obtained by manually requesting it from Amari's Discord server which you can find at <https://amaribot.com/support>.

!!!note "Worth noting"
    We tried to get it ourselves to test this feature and we were told that they're currently not issuing API keys as they're redoing the system or something like that. Documentation-wise our code is correct, but we haven’t tested it.

## How to import your data

On your server, run Sokora's `/import` command from any channel. You'll be presented with a list containing all options listed above together with an <span class="discord-button discord-button--primary">Import</span> button, which will either direct you to the next step head on or trigger a modal asking for an API key, depending on the bot.

Once you're in the next step, you will be presented with a small preview of what will be imported. You have three buttons: <span class="discord-button discord-button--success">Merge data</span>, <span class="discord-button discord-button--danger">Overwrite data</span> and <span class="discord-button">Check JSON first</span>. The embed explains them on its own, but for your information, this is what they do:

* **Merge data** ADDS the level XP from your previous bot on top of whatever Sokora has stored.
* **Overwrite data** REPLACES the level XP from Sokora with the one from your bot.

!!! tip
    If you’ve just added Sokora (so it has no data), merge and overwrite do the same.

* **Check JSON first** presents a preview of how Sokora has read your bot's level XP, sorted from highest to lowest (it'll only show whatever it can fit in the message). Said preview is, obviously, formatted in JSON; nothing hard to read if you don't know what that means. You'll still have both Merge and Overwrite buttons available after clicking this one.

Once you click to merge/overwrite leveling data, Sokora will start immediately. Give it some time. It'll tell you when its done.

And once done, you're good to go! You can now remove your old bot and keep your leaderboard.

## FAQ

??? question "What about level rewards like roles and channels? Do these get imported?"
    It depends on the bot. As of now we only can do this for MEE6; Amari is on the works. If a bot supports level rewards but we cannot import them, Sokora will warn you about that.

??? question "What does bot support depend on? Why is _x_ bot not supported?"
    Sokora gets the data by trying to work around bot-provided APIs. However, not all bots provide APIs and prefer to lock the data so only they can access it. We can't do much about that.

??? question "I've imported my leveling data but now XP gain feels different, why?"
    Because it is in fact different, we simply can't import your XP growth settings (especially because each bot uses a different mathematical formula to compute XP gain).

??? question "Is this import ability Sokora-specific?"
    Actually not. We made it available for use to most Discord bots.

    Learn more about this at <https://github.com/sokoradesu/honlvlimport>.

??? question "Say another bot implements this, can I move from Sokora to it?"
    **Not _yet_.** We know it sounds a bit hypocritical, however we do NOT intend to engage in vendor lock-in like other bots, it's just technical reasons: Sokora doesn't have a web API and thus it's *still* in the same state as developer-unfriendly bots.

    We are (obviously) working on this and will eventually update the library so Sokora leveling data can be freely imported as you deserve. Just give us some time!
