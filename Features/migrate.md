# Migration Guide
<small>Last updated: 20/6/26</small>

<!-- START START -->
<b>This guide covers level data migration, which is not yet released.</b> It will be released with Sokora 0.4, which is under active development.
<!-- END START -->

<!-- START(Introduction) -->
## Introduction
A hard part of switching to a new and better bot (like Sokora) with a levelling system is that you probably were using another bot for this purpose before. This usually leaves you with three options:
- Keep both bots, doing with one what you could do with the other one. Easiest, but suboptimal.
- Remove your previous bot. Optimal, but your leaderboard is lost, which your members won't like.
- Not use Sokora. Your leaderboard is kept, but you miss the best Discord bot. Not good!
<!-- $$ -->
However, <b>if you use MEE6, Tatsu, Lurkr or Amari for levelling, you're lucky!</b>
<!-- $$ -->
We can bring your leaderboard over to Sokora.
<!-- END(Introduction) -->

<!-- START(Setup) -->
## Setting up your previous bot for import

This process depends on the bot you're migrating from.
<!-- $$ -->
<!-- $$ -->
### MEE6
You need to enable leaderboard visibility from your dashboard. Open the leaderboard settings in the MEE6 dashboard and enable the option \`Make my server's leaderboard public\`. Otherwise data cannot be imported.
<!-- $$ -->
<!-- $$ -->
### Tatsu
*Nothing required.*
<!-- $$ -->
<!-- $$ -->
### Lurkr
You need an API key, obtained from <https://lurkr.gg/docs/api#authentication>.
<!-- $$ -->
Additionally, you need to grant specific permissions for the server you want to import from. Check the same link, it describes this immediately after explaining how to get your API key.
<!-- $$ -->
Lastly, you need to manually change \`Choose the visibility for the web leaderboard\` in Lurkr's dashboard to \`Public\`.
<!-- $$ -->
<!-- $$ -->
### Amari
You need an API key, obtained by manually requesting it from Amari's Discord server at <https://amaribot.com/support>.
<!-- $$ -->
It's worth noting we tried to get it ourselves to test this feature and we were told that they're currently not issuing API keys as they're redoing the system or something like that.
<!-- END(Setup) -->

<!-- START(Importing your data) -->
## How to import your data

On your server, run Sokora's */import* command from any channel. You'll be presented with a list containing all options listed above together with an *Import* button, which will either direct you to the next step head on or trigger a modal asking for an API key, depending on the bot.
<!-- $$ -->
<!-- $$ -->
Once you're in the next step, you will be presented with a small preview of what will be imported. You have three buttons: "<b>Merge data</b>", "<b>Overwrite data</b>" and "<b>Check JSON first</b>". The embed explains them on its own, but for your information, this is what they do:

- <b>Merge data</b> ADDS the level XP from your previous bot on top of whatever Sokora has stored.
- <b>Overwrite data</b> REPLACES the level XP from Sokora with the one from your bot.
<!-- $$ -->
Merge and overwrite are equivalent in their result if Sokora was newly added (and thus has no data).

- <b>Check JSON first</B> presents a preview of how Sokora has read your bot's level XP, sorted from highest to lowest (it'll only show whatever it can fit in the message). Said preview is, obviously, formatted in JSON; nothing hard to read if you don't know what that means. You'll still have both Merge and Overwrite buttons available after clicking this one.

Once you click to merge/overwrite leveling data, Sokora will start immediately. Give it some time. It'll tell you when its done.
<!-- $$ -->
And once done, you're good to go! You can now remove your old bot and keep your leaderboard.
<!-- END(Importing your data) -->

<!-- START(FAQ) -->
## FAQ
<CLOSABLE (What about level rewards like roles and channels? Do these get imported?)>
Usually yes, though it depends on the bot. If a bot supports level rewards but we cannot import them, Sokora will warn you about that.
</CLOSABLE (What about level rewards like roles and channels? Do these get imported?)>
<!-- $$ -->

<CLOSABLE (What does bot support depend on? Why is *x* bot not supported?)>
Sokora gets the data by trying to work around bot-provided APIs. However, not all bots provide APIs and prefer to lock the data so only they can access it. We can't do much about that.
</CLOSABLE (What does bot support depend on? Why is *x* bot not supported?)>
<!-- $$ -->

<CLOSABLE (I've imported my levelling data but now XP gain feels different, why?)>
Because it is in fact different, we simply can't import your XP growth settings (especially because each bot uses a different mathematical formula to compute XP gain).
</CLOSABLE (I've imported my levelling data but now XP gain feels different, why?)>
<!-- $$ -->

<CLOSABLE (Is this import ability Sokora-specific?)>
Actually not. We made it available for use to most Discord bots.
<!-- $$ -->
Learn more about this at <https://github.com/hokkiai/djs-level-importer>.
<!-- $$ -->
<small>(Note: we're the creators and main maintainers but due to an agreement it's not Sokora who publishes the source code, thus the GitHub URL not pointing to our organization).</small>
</CLOSABLE (Is this import ability Sokora-specific?)>
<!-- $$ -->
<CLOSABLE (Say another bot implements this, can I move from Sokora to it?)>
<b>Not <i>yet</i>.</b> We know it sounds a bit hypocritical, however we do NOT intend to engage in vendor lock-in like other bots, it's just technical reasons: Sokora doesn't have a web API and thus it's <i>still</i> in the same state as developer-unfriendly bots.
<!-- $$ -->
We are (obviously) working on this and will eventually update the library so Sokora leveling data can be freely imported as you deserve. Just give us some time!
</CLOSABLE (Say another bot implements this, can I move from Sokora to it?)>
<!-- $$ -->
<!-- $$ -->
<!-- END(FAQ) -->
