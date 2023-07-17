# Matrix moderation

Live chats sometimes require quick intervention.

We have a secret chan that we can use to interact with the mjolnir bot.

Docs: <https://github.com/matrix-org/mjolnir/blob/main/docs/moderators.md>

## Banning a user

```
!mjolnir ban destructive user <@user-id>
```

If the account is a troll, use `!mjolnir redact <@user-id> <#room-id>` to
remove the offending messages.
