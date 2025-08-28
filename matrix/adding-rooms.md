# Matrix Room Onboarding

The `@admin:nixos.org` user is capable of adding an alias that is rooted on its own homeserver, which is what we want for branding reasons.

It is however not a server admin, so we cannot rely on https://github.com/grahamc/matrix-management-tools/blob/main/process-all-rooms.sh, which requires access to the `/_synapse/` Admin API.

We can deal with both new and pre-existing rooms. For pre-existing rooms the existing admins need to hand over that permissions, and demote to moderator, so the room will fall exclusively under community administration.

## Preconditions

- Be joined to `#moderators:nixos.org` with your own account
    - so you can control Mjölnir
- Active session on the `@admin:nixos.org` account
    - The secret recovery key for the encryption things is on bitwarden
- Get moderator permissions on the space (or subspace) you want to add the room to
    - `!mjolnir powerlevel @admin:nixos.org 50 <room>`

## Spaces

Making a decision in which space or subspace a room belongs

- Main space
    - Community
        - Community projects
    - International
        - Regional channels
    - Teams
        - Official Teams
        - Unclear what they map to
            - https://nixos.org/community/#governance-teams
            - https://github.com/NixOS/nixpkgs/blob/master/maintainers/team-list.nix
            - https://github.com/orgs/NixOS/teams
    - Topics
        - Things that are not official teams yet? Best guess.

## Tasks

From the `@admin:nixos.org` user, execute the following steps:

- Create new room
    - or join it, if it already exists
- If you don't have "Admin" permissions, request them from existing admins
- Ask existing admins to step down to moderator role
    - Rooms should be owned by the community, represented by the moderation team, so we can guarantee the room will be maintained going forward
    - We can probably be more lenient for community project rooms
    - Existing "Admin" permissions can only be removed by a user for themselves
- Make sure the room is publicly accessible
- Add `:nixos.org` room alias
    - Promote it to the room default
    - Publish it in the nixos.org room directory
- Invite mjolnir
    - and set its power level to "Admin"
- Tell mjolnir to protect the room
    - `!mjolnir rooms add <alias>`
- Upload room avatar
    - Hash the room id (old) or room alias with md5 and download the avatar:
    - Set roomAlias: `export roomAlias=#example:nixos.org`
    - Run `wget -O /tmp/$roomAlias.png "https://www.gravatar.com/avatar/$(echo -n "$roomAlias" | md5sum | cut -d' ' -f1)?d=identicon&f=y&s=2048"`
- Add the room to the relevant space
- Verify permissions on Mjölnir are all good
    - `!mjolnir verify`
- Demote `@admin:nixos.org` to default level
    - Permissions can be restored via Mjolnir, when required

- Leave the room
