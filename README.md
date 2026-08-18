CoA Heal Assist v0.10.1

CoA Heal Assist has reached a much more stable and feature-complete point. This release focuses on cleaner healer frames, better raid usability, safer Ascension compatibility, configurable visuals, and improved performance.

Highlights
Healium-style compact healing frames
Up to 14 configurable spell buttons
Drag spells directly from the spellbook onto healer buttons
Per-character spell layouts and settings
Party, raid, tank, pet, friend, healer, and DPS frame options
Independent movable Raid Group 1–8 panels
Automatic Me / My Group detection
In parties, automatically shows your current party
In raids, automatically detects and displays your assigned raid group
Automatically follows you if the raid leader moves you to another group
Minimap launcher
Left-click: open Settings
Right-click: show/hide healer UI
Drag: move minimap icon
Buff, HoT & Shield Tracking
Tracks your own Buffs / HoTs / Shields
Active tracked buffs can grey out the corresponding spell button
Optional Show My Buff/HoT Icons setting
New shield/absorb overlay
Displays shields as a blue section over the target’s health bar
Shrinks as the absorb is consumed
Disappears when the shield is gone
Shield overlay can be enabled or disabled in Settings
Cleanse Support
Supports:
Curse
Disease
Poison
Magic
Bleed
Matching cleanse spell buttons receive a red warning
Manual REMOVES configuration remains available for custom CoA spells
Proc & Charge Support
Manual action-bar binding for custom Ascension abilities
Charge counter mirroring
Proc/free-cast detection
Proc-ready spells use a steady bright gold highlight
Separate Proc / Charge / Both binding modes
UI Improvements
Removed unnecessary toolbar clutter from the healer frame
Lock, Reset, Frames, Config, version, and addon information moved into Settings
Added adjustable frame background
Use Frame Background toggle
Background Transparency slider
Cleaner Settings layout with corrected button/label spacing
Optional spell-button tooltips
Adjustable:
visible button count
button size
button spacing
frame scale
Ascension Compatibility / Safe Mode

Recent Conquest of Azeroth updates caused the Ascension client to crash with:

CharacterAdvancementBuildEntry::UpdatePointers:
entry 7051 not found

CoA Heal Assist now uses a safer compatibility approach:

Removed automatic spellbook scanning on login
Removed automatic Scan All operations during startup
Avoids risky custom spell-ID probing during initialization
No automatic advancement/spellbook traversal when loading the addon
Existing saved spell setups remain intact
Manual configuration remains available

These changes significantly reduce the chance of the addon triggering native Ascension client assertion failures.

Performance Improvements

v0.10.1 includes an important performance hotfix for the new shield system.

Certain CoA abilities can generate large bursts of health and aura events. Shield detection is now:

throttled
cached per unit
limited to roughly 5 absorb checks per second per unit
prevented from repeatedly rebuilding the shield graphic when nothing changed
no longer repeatedly calling unnecessary Show/Hide/SetPoint operations during event spam

This substantially reduces FPS drops while using high-event CoA abilities.

Saved Settings

Updating should preserve your existing:

spell assignments
per-character profiles
frame locations
raid group locations
minimap position
proc/charge bindings
buff tracking
display settings
Installation
Download the release ZIP.
Remove the existing CoAHealAssist folder from:
World of Warcraft\Interface\AddOns\
Extract the new CoAHealAssist folder into AddOns.
Start Ascension or type:
/reload
Useful Commands
/cha config
/cha frames
/cha clearslot 1-14
/cha tooltips on|off
/cha barbind <slot> both|proc|charge
/cha barmode <slot> both|proc|charge
/cha barunbind <slot>
/cha bardebug <slot>
/cha reset
/cha minimap reset
Notes

CoA Heal Assist is designed specifically around the behavior and limitations of Project Ascension – Conquest of Azeroth. Custom Ascension spells do not always expose the same information as standard Blizzard spells, so several systems use safe fallbacks and manual configuration where necessary.

Made by Overlord - Homeless Guild

Suggested GitHub release title

CoA Heal Assist v0.10.1 — Safe Mode, Shield Tracking & Performance Update

For the release asset, upload:

CoAHealAssist-v0.10.1.zip

give me an read me to add

Here’s a clean README.md you can paste directly into GitHub:

# CoA Heal Assist


**CoA Heal Assist** is a custom Healium-style healing addon built specifically for **Project Ascension: Conquest of Azeroth**.


It provides compact healing frames with configurable spell buttons, buff/HoT tracking, cleanse alerts, absorb/shield overlays, raid-group management, proc/charge support, and per-character layouts.


Made by **Overlord - Homeless Guild**


---


## Features


### Healium-Style Healing Frames
- Compact player rows
- Up to **14 configurable spell buttons**
- Icon-only spell layout
- Drag spells directly from the spellbook onto the healer bar
- Shift + Right-click a spell button to clear it
- Adjustable:
  - Button count
  - Button size
  - Button spacing
  - Frame scale


### Party & Raid Support
Supports separate visibility options for:


- Party
Proc & Charge Support

Custom Ascension abilities do not always expose proc and charge information through normal Blizzard APIs.

CoA Heal Assist includes manual action-bar binding support.

Bind an Action Bar Button

Hover the real Ascension action-bar button and use:

/cha barbind <slot> both

Available modes:

both
proc
charge

Examples:

/cha barbind 1 proc
/cha barbind 2 both
/cha barbind 3 charge
Change Binding Mode
/cha barmode <slot> both
/cha barmode <slot> proc
/cha barmode <slot> charge
Remove Binding
/cha barunbind <slot>
Debug Binding
/cha bardebug <slot>

Proc-ready abilities use a steady bright gold highlight instead of a pulsing effect.

Minimap Controls

The addon includes a movable minimap icon.

Left Click

Opens the Settings window.

Right Click

Shows or hides the entire healer UI.

Drag

Moves the minimap icon around the minimap.

UI Settings

Most addon controls are handled directly through the Settings window.

The main healer UI is intentionally kept clean and does not display unnecessary management buttons.

Settings include:

Show / Hide healer frame
Lock frame position
Show / Hide Frames
Reset Layout
Reset Minimap Position
Visible spell buttons
Button size
Button spacing
Frame scale
Spell tooltips
Buff/HoT icon visibility
Shield/Absorb overlay
Background visibility
Background transparency
Frame visibility options
Raid Group visibility
Tank / Pet / Friend frames
Background Transparency

The healer frames support configurable transparency.

Use Frame Background

Enable or disable the frame background entirely.

Background Transparency

Adjust the background from:

0%   = Fully transparent
100% = Fully visible

This applies to the Raid Group, Tank, and Pet frames.

Per-Character Profiles

CoA Heal Assist saves spell layouts and frame settings separately for each character.

This includes:

Spell assignments
Frame positions
Raid group positions
Tank frame position
Pet frame position
Minimap position
Button layout
Proc/charge bindings
Buff tracking
Display settings

A new character starts with a blank spell bar instead of inheriting another character's setup.

Ascension Safe Mode

Recent Conquest of Azeroth client updates caused some spellbook-related addon operations to trigger a native Ascension client assertion:

CharacterAdvancementBuildEntry::UpdatePointers:
entry #### not found

To reduce the risk of this crash, CoA Heal Assist uses a safer compatibility mode.

The addon avoids:

Automatic spellbook scanning during login
Automatic Scan All operations on startup
Aggressive custom spell-ID probing
Repeated advancement-related spellbook lookups

Saved spell configurations remain available.

Some custom CoA spell information may require manual configuration because of these safety restrictions.

Performance

CoA Heal Assist is designed to avoid heavy full-frame scanning.

Performance features include:

Event-driven updates
Cached aura information
Throttled shield checks
Cached action-bar bindings
Limited proc discovery
No full UI scans every frame
No constant spellbook scanning
Lightweight shared animation handling

Shield checks are limited to approximately 5 updates per second per unit instead of being queried for every health or aura event.

Installation
Download the latest release.
Extract the ZIP.
Copy the folder:
CoAHealAssist

into:

World of Warcraft\Interface\AddOns\

Your folder should look like:

Interface
└── AddOns
    └── CoAHealAssist
        ├── CoAHealAssist.lua
        └── CoAHealAssist.toc
Start Project Ascension.
Enable CoA Heal Assist in the AddOns menu.

If updating from an older version, replacing the addon folder will not normally erase your SavedVariables or character settings.

Slash Commands

Open Settings:

/cha config

Show / Hide frame:

/cha

Frame options:

/cha frames

Reset layout:

/cha reset

Reset minimap:

/cha minimap reset

Set visible spell buttons:

/cha buttons <1-14>

Set button size:

/cha buttonsize <22-48>

Set button spacing:

/cha spacing <0-12>

Clear a spell slot:

/cha clearslot <1-14>

Toggle spell tooltips:

/cha tooltips on
/cha tooltips off

Proc / Charge binding:

/cha barbind <slot> both|proc|charge
/cha barmode <slot> both|proc|charge
/cha barunbind <slot>
/cha bardebug <slot>

Show version:

/cha version
Notes

CoA Heal Assist is built specifically for Project Ascension: Conquest of Azeroth.

Because CoA uses many custom classes, spells, talents, action buttons, and aura systems, not every spell exposes information through standard World of Warcraft APIs.

The addon uses safe fallbacks and manual configuration where necessary to improve compatibility and reduce the risk of crashes or FPS loss.

If you encounter an error, please include:

CoA Heal Assist version
Full Lua error
Stack trace
What spell or action triggered it
Whether the problem stops when CoA Heal Assist is disabled
Current Version

CoA Heal Assist v0.10.1

Credits

Created by:

Overlord - Homeless Guild

For Project Ascension: Conquest of Azeroth
