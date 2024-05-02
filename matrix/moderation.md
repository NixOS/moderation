# Matrix moderation

Live chats sometimes require quick intervention.

We have a private channel that we can use to interact with the mjolnir bot.

Docs: <https://github.com/matrix-org/mjolnir/blob/main/docs/moderators.md>

## Banning a user

```
!mjolnir ban user <@user-id>
```

If the account is a troll, use `!mjolnir redact <@user-id> [#room-id]` to
remove the offending messages.

## Unbanning a user

```
!mjolnir unban user <@user-id> true
```

The `true` at the end is important and makes sure the change is applied to all rooms.

## Muting a user

```
!mjolnir powerlevel <@user-id> -1 [room]
```

If no room is given, the mute is propagated across all rooms protected by
Mjolnir. Unmuting happens by resetting the powerlevel to `0`.
