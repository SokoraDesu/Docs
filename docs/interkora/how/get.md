# Get stuff

With `soko$get`, you can get various things:

- leveling data
- news
- case list
- current settings
- starboard
- serverboard entries

Each one has its own slightly different syntax. (TODO: document properly)

```bash
# settings
soko$get settings leveling
soko$get settings leveling.rewards
# leaderboard
soko$get leaderboard 1 json
soko$get leaderboard 1 yaml
# news
soko$get news 3 yaml
soko$get news <t:123...>:>=,<t:234...>:<=
soko$get news <t:123...>:>
soko$get news <t:123...>:<=
# serverboard
soko$get serverboard 3 yaml
soko$get serverboard . json
# moderation
soko$get cases 84/-
soko$get cases 82/- yaml
soko$get cases 1/+
```
