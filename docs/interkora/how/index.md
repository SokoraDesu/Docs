---
hide:
  - toc
---

# How it works

Interkora is simple. You just write commands in the message box and they run.

```bash
soko$get settings leveling.rewards
```

You can stack several calls.

```bash
soko$get settings leveling.rewards
soko$get settings welcome.join_message
soko$mod mute @Goos "Bad behavior"
```

They run right away… if these conditions are met:

- Interkora is enabled. Server admins have to enable it by default.
- The entity that runs that is given permission.

!!!quote "What is an entity?"
    In Interkora terms, an entity is anything that can use Interkora. A user, a bot or a webhook. When saying “the entity”, we’re talking about the executor of the command.

Interkora’s permission system is simple. There are two levels to this:

- Unregistered entities, i.e. a real user, or a webhook/bot you manually add.
    - These take an on/off approach. You either let them do anything (by adding them to a whitelist) or nothing (by not adding, or removing, them).
- Registered entities, i.e. integrations that you install.
    - These declare a list of permissions they want to access. If they change it, you need to re-authorize them. For now the list has to be accepted as a whole or rejected (on/off like before), but fine-grained controls are planned.

!!!quote "What is an integration?"
    It’s basically a featured “thing” that does stuff on its own and uses Interkora to do something meaningful. The word “extension” may help you get the idea quicker, though it would be _slightly_ inaccurate as you don’t _extend_ what Sokora does but rather _integrate_ with it to do your own thing.

---

Knowing all of this, the idea of how it makes sense to use Interkora might be more clear to you.

**You can use this as an API** that works without auth tokens or you having a server **from your own code** to do meaningful things! Anything you can think of (we’re working on providing our own examples and pre-made integrations).

The easiest thing is to use Discord webhooks, as you don’t need a full bot setup for them to work; just make a `POST` request to the Discord-provided endpoint with the Interkora message. The webhook can be only in a server you control, then you pass the webhook ID to users who want your app to be installed and that’s about it (and yes, we know a marketplace would be much better than doing that; we’re working on it).

> This documentation will be improved over time.
