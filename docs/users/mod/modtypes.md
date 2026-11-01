# Case types

A tiny reference onto what you can do with Sokora and how it works.

Icons are used to reflect the following properties:

- :material-clock-time-two: Actions can be given a duration/expiry
- :material-volume-mute: Actions that can be done silently
- :material-undo: Actions that can be fully reverted

## User moderation

### KICK (:material-volume-mute:)

Kick a user, optionally with a reason. They will be able to join back if they get an invite link.

### BAN (:material-clock-time-two: | :material-volume-mute: | :material-undo:)

Ban a user, optionally with a reason and a duration (after which the ban expires). Also allows to delete recent messages from the user. They won’t be able to join until the ban is lifted, if ever.

For performance, Sokora uses scheduled intervals for revoking temporal bans, so there are a few minutes of error margin (either early or late unban). It shouldn’t really be perceived, though.

:material-undo: Undo with `/unban`.

### WARN (:material-volume-mute: | :material-undo:)

Warn a user. Warnings are mere text notes with no effect on the user. If not silent, the user is privately messaged by Sokora with the warning message. Use them to track rule violations.

:material-undo: Undo with `/delwarn`.

!!!bug "About DELWARN"
    Warnings can be deleted, in which case the record will be wiped from the database. This isn’t great, and replacing this with a warning deletion case is already planned.

## Channel moderation

### CLEAR

Wipes several messages on a channel, defaults to the active one. Has a max of 100 messages, and cannot delete extremely old messages due to Discord API limitations. Use it to quickly get rid of inappropriate messages.

### LOCK (:material-undo:)

Locks a channel, so no one but admins can type into it. Use it to cool down a heated channel.

:material-undo: Undo with `/unlock`.

### SLOWDOWN (:material-undo:)

Slows a channel down, so people can only send messages every set amount of time. Use it keep extremely active chats under control.

:material-undo: Undo with `/slowdown`, setting the slowdown to zero.
