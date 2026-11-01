# Contribution guide: some things to keep in mind

A few, simple guidelines onto how to contribute to Sokora.

- Ensure to run the static formatter and analyzer (via `bun run ql`) before committing. It's relatively strict, fix any issues it reports and resort to ignore comments only if absolutely necessary.
- Remember to commit changes to `bun.lock` file.
- Do not repeat yourself, at all. Code duplication creates problems. Extract.
- Document via TSDoc anything that isn’t _actually_ self-explanatory and other developers will have to touch often (like utility functions or important parts of important files).
- Use the functions from `safeThings` instead of using `discord.js` provided methods whenever there’s one. This includes, but is not limited to:
    - Reply to an interaction (`safeReply`)
    - Edit a message (`safeEdit`)
    - Get members (`safeMembers`)
    - Get a channel (`safeChannel`)
    - Get a role (`safeRole`)
    - Get an individual member (`safeMember`)
    - Get a user (`safeUser`)
    - Get a guild (`safeGuild`)
    - Get a channel to send important bot messages to (`safeAlertChannel`)
    - *Your safest bet is to check out this file once when cloning the repo, then each time it gets modified, as we add new safeThings from time to time.*
- Comment your code liberally. Don’t be afraid to leave questions, and answer those you find. Explain anything that requires context, you’re unsure about, or simply feel would be better with a human explanation on top.
