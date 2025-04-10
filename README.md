# aardplugins
Bartoc the Inquisitive's plugins for MUSHclient Aardwolf

ALL PLUGINS WIP UNLESS MARKED OTHERWISE


InquisitorDatabase
-

Creates a SQLite3 database of NPC weaknesses using data from the Interrogate skill.

Features complete:
- Intercepts "kill" commands to attempt Interrogating the target before attacking if Interrogate is off cooldown.
- When Interrogate is successful, generates a unique key of area + room + mob shortname and stores all information revealed by the Interrogate skill to a sqlite database.
- Handles mob immunities by overriding relevant resists to 100

Feature goals:
- When attacking a mob, attempt to look it up in the database and plugin broadcast its stats if found.
- Generate a sorted list of the mob's weaknesses to post in its database entry (more efficient to do it once on capture than on-demand later)
- Attempt lookup of mobs before interrogation to skip captured mobs.
- Sync local sqlite database with BigQuery to crowdsource data.
- Mark roomchars with a flag if they haven't been captured yet.
- Oracle's "look" command reveals a weakness (maybe up to four?). Capture Oracle info to database to improve crowdsourcing, but mark entries as "incomplete" to be overwritten by canonical Interrogates.
- Bonus stretch feature: create and maintain a separate database to catalogue all fountains within Aardwolf, solely for the purpose of fulfilling Bartoc's desire to make heinous cocktails in her Decanter.

Database columns in order: 
- uniqid, partial, name, room, zone, level, guild, subclass, identical, hp, alignment, bash, pierce, slash, acid, air, cold, disease, earth, energy, fire, holy, light, electric, magic, mental, negative, poison, shadow, sonic, water


StylishMode
-

Inspired by FFXIII and named after the Arcsys fighting game control scheme.
While fighting, automatically uses the best abilities available.

Features complete:
- Drawing from the practiced spells available to you at your level, use a skill or cast a spell every combat turn based on a defined rotation.
- Use different sets of abilities based on mob hp %.
- Debuff enemies without duplicating afflictions.
- Open and walk through doors after you bump into them - attempt to knock locked doors.

Feature goals:
- Smarter spellup function.
- Re-equip weapons after disarmed.
- Attempt to dispel debuffs afflicted on you.
- After combat, recover by drinking potions.
- Drink from your drink container when you get hungry/thirsty.
- Portal alias to get portal from bag, equip, enter, equip previous held item, put portal back in bag.
- Automatically add acquired keys to keyring.
- Integrate InquisitorDB data to smart target weaknesses and change behavior based on mob class.
- Support custom rotations.
- Tracks debuffs received or inflicted.
- Automatically disable all features when idle or fighting a player to fulfill anti-botting criteria. Remove program defaults and require user-defined rotations?


Where2Grind
-

Provides a concise, live-updating window listing popular places to grind at your level.

Features complete:
- On load in or levelup, automatically sends mobdeaths for a range around your level and coallates the results by area in a miniwindow.
- Provides an area "density" rating - how many different mobs are listed in mobdeaths for that area.

Feature goals:
- Toggle between good, evil, or alignment-agnostic modes.
- Clickable hyperlink in table to runto area.
- Config for the relative range of levels to capture.
- Sort table by lower range of mobs found.
- Potentially integrate Crowley's cutils Table function for cleaner output.
- Support config for displaying & sorting by average level instead of level range.
- Support config for sorting by mob density.

Bartoc's Utilities
-

Miscellaneous aliases and helper functions Bartoc uses. Staging ground for testing code before it's spun off into an independent plugin.

Aliases:
- pib *  -  "put in bag"  -  puts item in Bag of Aardwolf
- gfb *  -  "get from bag"  -  gets item from Bag of Aardwolf
- lib *  -  "look in bag"  -  looks in Bag of Aardwolf
- rest  -  "rest in the field"  -  if in the field, attempts to make a fire and camp before resting.


Future Planned Plugins
-

SpellupBar - compresses lengthly, verbose spellup dialogue to a loading bar.

Master Interface - turn miniwindows into tabs. Combines minimap, exits, room description, graffiti, room npcs, objects into a single elegant window. Integrates with InquisitorDB to automatically show real level and alignment on room npcs. Adds maps.gaardian hyperlinks for current area.

Market Board plugin - filter by category to tabs, click to appraise. Easy bid. Price tracking of average sale prices?

Inventory - graphical sorted inventory with tabs.

GraphicBattle - elegant battle readout compressing the battle log to a simplified graphical interface. Adds damagetype sprites and visual debuff tracking.
