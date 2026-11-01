---
hide:
  - toc
---

# Moderate

You can prepare moderation actions.

```bash
soko$mod [action] [("time if needed")] [user] ["reason"] [silent?]

# for example:
soko$mod mute (1d 12h) @JohnDoe "Annoying"
soko$mod ban @JohnDoe "Very very annoying!"
soko$mod warn @JaneDoe "Annoying too, but don’t tell her" true
```

!!!note "mod is only for executing"
    For reading (i.e. getting the case list), use [`soko$get`](./get.md).

Actions won’t get executed outright, instead moderators will get suggested to run them with a button to immediately do it.

This is useful if you want to integrate your own safety system with Sokora’s case system.
