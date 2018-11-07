# Ops

## Run admin commands from Discord chat

As an Op, you can run administrative commands like below from the Discord chat (web, or mobile!) without having to be logged in to the Minecraft GUI client using `!cmd /help` & Co.  

Not all plugins' commands work through chat.  For example Nucleus' `/world` only works in-game; on chat `!cmd /world` is unknown, and `!cmd world` works but is silent, because it outputs only to STDOUT on the server container log, not into chat.
   

## Player Permissions

    /lp user <PLAYER> showtracks
    /lp user <PLAYER> promote level
    /lp user <PLAYER> demote level

do several times, until reaching the right level; currently:

* default: forced to Adventure mode (not Creative)
* verified: /hat, /nick, /rules, /message - but still Adventure
* assistant: Creative!  Also /teleport, /back, /warp, /ignite.
* fbi: /jail
* boss: LP, /fly, /ban, /kick, /freezeplayer, /gamemode AND -surtout- /world

These groups may be changed in the future.
