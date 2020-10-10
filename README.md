# Phasmophobia Chroma

This is a fork of the PhasmoPhobia Config by Fiskybusiness.  I plan on adding a bunch of useful functions, however, uploading what I have now as an initial release.

## FAQ
* Q: Will this get me banned?
* A: Probably not.  The only anti-cheat that i've found checks for a balance over 250k (then sets it back to 100).  
* Q: I have problem X and don't know what to do.  Help pls?
* A: Create an issue post. Do not add me on Discord for bug reports.

## Getting Started

* Step 1: Make a copy of your original Assembly-CSharp.dll so you can easily switch back to non-modded game
* Step 2: Copy the Assembly DLL and modconfig.cfg to your Phasmophobia install location, and overwrite the DLL (<SteamInstallLocation>\steamapps\common\Phasmophobia\Phasmophobia_Data\Managed)
* Step 3: Configure the values in modconfig.cfg to your liking
* Step 4: Launch the game and enjoy.

### Known Bugs

* The Game will likely break when multiple players die at the same time. Having tens of ghosts is risky in this sense. This is due to how the game handles death and would probably require a full re-write to support fully. Consider games with 3+ Ghosts to be "for fun"

* Currently, the 'fullItems' flag is purely visual. Enabling this will prevent items from spawning.  I'll fix this at some point, but for now, leave it as-is.

### serverPlayers

Maximum Capacity you want your Server to Have

```
serverPlayers=16
```

### Player Name Attributes

You can set the player Name in Lobby and color of the displayed name using HTML color codes

```
// Basic name
playerName=Boring Name
HTMLColor=#0000FF

// PuRpLe NaMe
playerName=Boring Name
HTMLColor=#9400D3
```

### run/walk Speed
You can set the player's run and walk speed but using a decimal number. Please note it porbably shouldn't go higher than ten, and making it negative will make you go backwards. Moonwalking is dangerous
```
//defaults
runSpeed=1.6
walkSpeed=1.2

//gotta go fast
runSpeed=3.5
walkSpeed=5.5
```

### numGhosts

Number of Ghosts in the Level. Each will have Bone Evidence and its own ghost room. 

```
// Don't do this, this is bad.  We don't like bad things.
numGhosts=20
```

### idleTimerLow/IdleTimer High
Much of the Ghosts behaivour is determined by making a State Transition from the "Idle" State. Ghosts will by default stay in this mode for 2 - 6 seconds before doing something else like moving to a new room or interacting with an object.
Set the minimum and maximum time in the idle state to increase/decrease total activity of all Ghosts

```
//super high activity
idleTimerLow=0
idleTimerHigh=1

//super low activity
idleTimerLow=10
idleTimerHigh=20
```

### numCharges

Use these to control how many times you can use cameras or salt. This will not affect other players, only you

```
numChargesSalt=100
numChargesPhoto=9
```

### Ghost Hunting

You can prevent the ghost from ever entering the hunting mode with this toggle

```
//off
huntingEnabled=false
//on
huntingEnabled=true
```
### Ghost Select

You can toggle whether or not the ghost selection screen exists with this toggle

```
//off
ghostSelector=false
//on
ghostSelector=true
```

### Ghost Appear

You can toggle whether or not the ghost always is visible during the game

```
//off
ghostAlwaysAppear=false
//on
ghostAlwaysAppear=true
```

### ToolTips and Custom GhostNames

To add a custom tooltip or GhostName add a row in the .cfg file with the associated prefix. If there is no records, or the "useCustomNames" flag is set to false it will default to the original tooltips and Names.

```
//adding Names
ghostName=Ghost #1
ghostName=Ghost #2
//on
tooltip=Tooltip for ghost #1
tooltip=Tooltip for ghost #2

//use custom Names
useCustomNames=true
```

### Hunting Sanity

You can control the minimum threshold for the average (in)sanity [100 - current Sanity = insanity] of all players before a Ghost is eligble to Hunt. Normally this Value is 50, with an upper threshold of 75 before there's a 1/3 chance the Ghost will do a hunt the next action cycle. Lower this value for the ghost to hunt earlier in the level and more often

```
//hunts almost immediately
huntingSanityLow=0
huntingSanityHigh=10

//hunts almost never
huntingSanityLow=75
huntingSanityHigh=90

//NOTE THE LOW MUST ALWAYS BE LOWER THAN HIGH -- THE GHOST WONT HUNT OTHERWISE -- probably
```

### Sanity Modifier

You can edit the rate at which your sanity drains with sanityModifier -- this will only effect the drain after the setup period
```
//drains really fast
sanityModifier=25

//normal drain rate
sanityModifier=0.12
```

### Camera Shutter Speed

You can edit the cooldown for the handcamera taking pictures **Probably will crash clients if the cooldown is too fast**

```
//normal
cameraShutterSpeed=2

//Sanic
cameraShutterSpeed=0.2
```

### Max Add-able Items

You're able to edit the max amount of items you can add.  Please note that this does NOT 'give' you the item, but merely increases the max amount you CAN add.

```
// Default values
maxEMF=2
maxFlashlight=4
maxPhotoCam=3
maxLighter=2
maxCandle=4
maxUV=2
maxCrucifix=2
maxVideoCam=6
maxSpiritBox=2
maxSalt=2
maxSmudge=4
maxTripod=5
maxStrongFlashlight=4
maxMotion=4
maxSound=4
maxThermometer=3
maxSanityPills=4
maxGhostWriting=2
maxInfared=4
maxHeadMounted=4
maxGlowstick=2
maxParabolic=2
```

### Full Items

This flag currently does nothing, but when it's functional, maxes out all items in the lobby by default.  I.e, if your max amount of glowsticks is 20 and this flag is enabled, you'll start with 20 glowsticks in the session.

```
fullItems=true
```

### Modding player stats

**IMPORTANT NOTE:** Doing this will PERMANENTLY alter your game save.  I HIGHLY recommend you create a backup so you do not accidentially change your legit save by going to `%appdata%/../LocalLow/Kinetic Games/Phasmophobia` and creating a backup of your `saveData.txt` file.  Clone it, then launch the game.

If you don't care about playing the game normally and would rather cheat your level / money, you can do this using the following commands.  

FOR MONEY:
1. Set `enableSetMoney=true`
2. Set `setMoney=someAmount`.

Ex:
```
enableSetMoney=true
setMoney=1000
```

The same goes for levels.  Note: If the enable is not set to 'true' in ALL LOWERCASE, nothing will happen to your money/level.  This is so you do not accidentially mess up your save files.  
