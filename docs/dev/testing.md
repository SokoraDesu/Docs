# Testing

!!!failure "Status"
    This reflects MVC branch. Main branch has almost no testing and it works differently.

Sokora has had a history of being rather buggy, as we know. A lot of work has been put onto this, slowly improving over time.

This is how we will end it, once and for all.

## Towards a test-driven, end-to-end covered Sokora

**Sokora now has a static test suite** (with Bun’s testing library). It’s still a work in progress and with relatively low coverage, but it advances well.

Our end goal is full test coverage. Combined with properly enforced division of duties, we will eventually achieve the enforcement of **test-driven-development** as a rule (where developers and contributors are required to write the tests for new code _before_ the code itself, making bugs orders of magnitude harder to write).

Statically testing a Discord bot is particularly difficult because the test suite runs actual code, creates actual cases, etc. so you need to use the Discord API and you need to have actual channel/user/role/server IDs rather than `1234`.

The approach we take is to have an in-bot `/test` command which only registers when you explicitly enable it and, when executed, will **log into another bot** and use that bot to execute the test suite against itself, then itself will give you the results.

## How to test Sokora

You need:

- One server.
- Two bot tokens. **For both, all data will likely be erased**.
- Two users **with different permissions** (one should be able to moderate the other one).
- One channel where a lot of junk isn’t a problem.

Setup the following variables in your `.env`

| Variable | What to put into it |
| --- | --- |
| `DEVELOPMENT_ENABLE_IRL_TEST_SUITE` | Set this to true for the test suite to work. |
| `DEVELOPMENT_GUILD_ID` | A testing server. Your testing bots and users should be in. |
| `TESTER_USER_ID_A` | One user ID. It should have moderation permissions over User B. |
| `TESTER_USER_ID_B` | Another user ID. |
| `TOKEN` | You already know ;), you’ll run `/test` here. |
| `TESTER_TOKEN` | Token for the helper bot. This one will send a few messages, ignore it. |
| `TESTER_CHANNEL_ID` | Test channel. The helper bot will yap here. |

Ready to go!

## Now what?

Now you can launch the bot as usual, then run `/test`.

Sokora will launch Sokora, then Sokora will test itself against Sokora (quite epic if you ask!)

> Give her some time, this can take a while. Take a chance to stretch your back.

Once done, you’ll receive the command-line output of `bun:test` as an attachment. It also shows up in your terminal, and console logs appear there more than in the attachment. Attachments are still useful because maybe two days later you forget about how you broke something and then you’ll want to check the error message.

And… that’s it when it comes to using the suite!

Check the test output at the end. If everything passes, then Sokora is balling and you can ball too (and commit and push, if you will).

Otherwise, scroll up to find the error, and get to fixing. A good practice is to check the test *before* checking the broken code, not only because it helps you detect what exactly errored (it really does! sometimes), but because even the best developer can get a bug in the test itself.

## And how to write new tests?

Great question!

There’s not much to say, it’s just:

```ts title="your-cool-test.test.ts" linenums="7"
describe("group name, this groups related tests", () => {
  test("test 1 name", async () => {
    expect(Sokora.cool).toBe(true);
    expect(Sokora.peak).toBe(true);
    expect(Sokora.ball).toBe(Infinity);
  })
})
```

Name groups as what they _contain_ (e.g. `moderation features`) and name tests for what they ensure is working (e.g. `warn feature works`).

Now there IS something to care about: you’re in a multi-client environment! There’s two bots around, and you might want access to them.

There’s a utility file in the testing folder which exports `state{}` and `setup()`. Make sure to call `setup` before tests run, then use state as needed, it contains the _tester_ client as well as the testing guild and users.

```ts title="your-cool-test.test.ts" linenums="2" hl_lines="2 5"
import { ... } from "discord.js";
import { state, setup } from "./utilities.ts";

beforeAll(async () => {
  await setup(); // VERY IMPORTANT!!
});

describe("stuff", () => {
  test("ban", async () => {
    const { moderator, target, guild, client } = state;

    await client.doSomething(); // can’t think of an example right now
    
    const result = await ban({
      guild,
      moderator,
      target,
      reason: "In the name of science and experimentation…",
      ...
    })
  })
})
```

*[E2E]: End to end
