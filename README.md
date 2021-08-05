# FiveM-Queue

## How to install
---
- Drop the folder inside your resources folder.
- Add `start connectqueue` inside your server.cfg. - *Preferrably at the top*
- Set convars to your liking.
- Open `connectqueue/server/sv_queue_config.lua` and edit to your liking.
- Renaming the resource may cause problems.

## How to use / Examples
---
To use the API add `server_script "@connectqueue/connectqueue.lua"` at the top of the `__resource.lua` file in question.
I would also suggest adding `dependency "connectqueue"` to it aswell.
You may now use any of the functions below, anywhere in that resource.

### OnReady
This is called when the queue functions are ready to be used.
```Lua
    Queue.OnReady(function() 
        print("HI")
    end)
```

## AddPriority
Call this to add an identifier to the priority list.
The integer is how much power they have over other users with priority.
This function can take a table of ids or individually.
```Lua
-- individual
Queue.AddPriority("STEAM_0:1:33459672", 100)
Queue.AddPriority("steam:110000103fd1bb1", 10)
Queue.AddPriority("ip:127.0.0.1", 25)

-- table
local prioritize = {
    ["STEAM_0:1:33459672"] = 100,
    ["steam:110000103fd1bb1"] = 10,
    ["ip:127.0.0.1"] = 25,
}
Queue.AddPriority(prioritize)
```

## RemovePriority
Removes priority from a user.
```Lua
Queue.RemovePriority("STEAM_0:1:33459672")
```

## IsReady
Will return whether or not the queue's exports are ready to be called.
```Lua
print(Queue.IsReady())
```
