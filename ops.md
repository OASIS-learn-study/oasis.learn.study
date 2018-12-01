# Ops

## Run admin commands from Discord chat

As an Op, you can run administrative commands like below from our [Discord chat](https://discord.gg/NPbutxm) (web, or mobile!) without having to be logged in to the Minecraft GUI client using `!cmd /help` & Co.  

Not all plugins' commands work through chat.  For example Nucleus' `/world` only works in-game; on chat `!cmd /world` is unknown, and `!cmd world` works but is silent, because it outputs only to STDOUT on the server container log, not into chat.
   

## Player Permissions

    /lp user <PLAYER> showtracks
    /lp user <PLAYER> promote level
    /lp user <PLAYER> demote level

do several times, until reaching the right level; currently:

* default: forced to Adventure mode (not Creative)
* verified: /hat, /nick, /rules, /message - but still Adventure
* assistant: Creative!  Also /teleport, /back, /warp, /ignite.
* fbi: /jail & place Command Blocks
* boss: LP, /fly, /ban, /kick, /freezeplayer, /gamemode AND -surtout- /world

These groups may be changed in the future.

To debug missing permissions (and then add), use:

    /lp verbose on <YOU>
    /lp check <PLAYER> minecraft.command.tp
    /lp editor
    /lp verbose off <YOU>
    

# Worlds

A server can contain several worlds!  We use [Nucleus](https://nucleuspowered.org) for their administration. Here's how to navigate:

    /world list
    /world load aworld
    /spawn aworld
    /back
    /world tp aworld michaelpapa7
    /back

This is how to create new ones:

    /world create -g minecraft:default_1_1 --gm survival --di minecraft:easy survive
    /world create -g flat --gm creative --di peaceful rhjom
    /world create -g flat --gm adventure --di peaceful lobby
    /world setspawn
    /world sethardcore | setdifficulty | sethardcore

This is how to unload and delete no longer used worlds:

    /world unload aworld
    /world remove aworld
