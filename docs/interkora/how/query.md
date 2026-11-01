---
hide:
  - toc
---

# Query commands

With `soko$query` you access control commands.

## Control your own query

You can, for example, set a working guild, as by default all commands run on the guild you send the messages to but you might want to change that:

```bash
soko$query set-guild ["guild-id"]
# run some commands for that guild
soko$query reset-guild
# return to default
```

Commands will only work on guilds where you exist and you have permissions to do stuff. This is useful for 3rd party bots, so you can add buttons that work seamlessly without the “ugly” command messages appearing somewhere the user doesn’t want, by sending the messages to a bot-controlled guild where Sokora is added so it can read them.

!!!tip
    You don’t need to enable or configure Interkora in said guild, Sokora checks enablement status only for the one the actions are supposed to run within.

## Control future queries

Query also exposes settings for future settings. For now, only whitelist control is exposed, so you can do it without going through PSE (as Discord doesn’t let us make PSE’s whitelist control behave as good as we’d like).

```bash
# add to
soko$query set-whitelisted [entity-id] [wlid]

# remove from
soko$query reset-whitelisted [entity-id] [wlid]
```

!!!question "wlid?"
    Because of how Discord works, for now we hold two separate whitelists: one for webhooks and one for users/bots. `wlid` is **w** for the former and **u** for the latter; a single letter to tell lists apart.

## Inspect

You can also use `get-ent [entity-id]` to get the JSON payload of an entity, and `get-req` to get all permission requests on your guild.
