# Dynamic (variables)

You can write the following variables in some places to dynamically show certain pieces of data. Data like ’current time’ or ’member count’ always refer to what that value is at the moment of sending the specific message. Dynamic variables are currently supported for **join messages, leave messages, join DMs, and news.**

## 🎛 • Examples

!!!quote "Example data"
    Imagine it’s 1/11/2026, we’re in a server named “Cool Server“, with 40 members and owned by @johnowner, and that the person in the join/leave message is @jane.

A simple example: `Welcome to (servername), **(name)**!` will result in:

> Welcome to Cool Server, **Jane**!

Adding more stuff: 

`Hi **(username)**! Thanks for joining *(servername)* at (currentdate, simple), **(serverowner)** and the ***(count)*** members are happy to meet you!`

will result in:

> Hi **jane**! Thanks for joining *Cool Server* at 1/11/26, **johnowner** and the **40** members are happy to meet you!

## 🛜 • Dynamic mentioning

You can use a similar syntax to mention specific users, roles, channels, or timestamps, since Discord disallows this natively:

`Thank you so much to (1136046074700771400, user) for making this announcement the (1770053619077, detailed_timestamp). We love you!`

will result in:

> Thank you so much to @zakahacecosas for making this announcement the 2 de febrero de 2026 a las 18:33. We love you!

## 📜 • All variables

| Variable | Replacement |
| --- | --- |
| `(name)` | display name of the user who joined |
| `(username)`|username of the user who joined |
| `(count)`|member count |
| `(servername)`|name of this server |
| `(serverowner)`|name of the server owner |
| `(currentdate)`|current date in the ’July 10, 2025’ format |
| `(currentdate, simple)`|current date in the ’7/10/25’ format |
| `(currentdate, detailed)`|current date in the ’July 10, 2025 at 1:11 PM’ format |
| `(<id>, user | role | channel)` | given an ID, allows you to mention/link it (Discord modals don’t let you do this natively) |
| `(<timestamp>, default_timestamp | simple_timestamp | detailed_timestamp)` | given a Discord timestamp (Unix epoch in milliseconds), formats it as a date |

!!!question "Unix epoch?"
    **Discord timestamps** (and likewise most time systems in the world) **use a thing called Unix epoch to count time**. Just search online: there are many tools online to generate one for your desired date.
