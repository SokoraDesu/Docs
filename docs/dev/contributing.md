# Contribution guide

!!!success "Status"
    Whole page reflects both branches (except the last point, regarding reusable containers).

A few, simple guidelines onto how to contribute to Sokora.

## Some things you should keep in mind at all times

- Ensure to run the static formatter and analyzer (via `bun run ql`) before committing. It's relatively strict, fix any issues it reports and resort to ignore comments only if absolutely necessary.
- Remember to commit changes to `bun.lock` file.
- Do not repeat yourself, at all. Code duplication creates problems. Extract.
- Document via JSDoc anything that isn’t _actually_ self-explanatory and other developers will have to touch often (like utility functions or important parts of important files).
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

## Things you should keep in mind only when carrying specific tasks

### _I’m interacting with a setting that is specifically an ITERABLE OBJECT one._

If you’re defining it for the first time, add the `$` property to it:

```json
$: {
  "type": "TEXT",
  "desc": "",
  // val is needed, whatever you put inside will be ignored
  "val": ""
}
```

If you need to delete/reference a specific value, filter by `$`. It’s a GUID.

### _I’m finding a way for all of settingsEmbed.ts to be PROPERLY typed._

Choose a mansion you’d like us to buy for you.

For context, due to our type system being built assuming TypeScript is a better language than it actually is (see PR #91), we’ve hit some TypeScript limitations that make it very hard to convey what we’re doing to the compiler without errors. This section was created because we were actually going to tolerate getting `settingsEmbed.ts` (one of the most important files of the bot!) to production with a truckload of TypeErrors. By now this has been “resolved”, but by using bad practices and type casts everywhere. Anyone who solves it all is a hero and will probably be rewarded in some sort of way (not with an actual mansion, though).

### _I’m using a reusable container._

If consuming an existing one, watch out for regular containers and build/use containers.

- Containers that only export xEmbed(), like `userEmbed`, are regular containers. They take input and produce output (`ContainerBuilder`).
- Those that export useXEmbed() and buildXEmbed(), like `useErrorEmbed` vs `buildErrorEmbed`, are use/build containers.
    - The `build` variant is what you’d expect: input data, output a builder.
    - The `use` variant takes input, USES IT, and produces output of varying types (or `void`).
        - Here “use” can hold various meanings. For example, `useErrorEmbed` uses the embed by relaying it to our error tracking system, as well as auto-replying to the interaction you provide; then the function returns `void`.
