
# Persona 5 Cheat Table

A cheat table for __Persona 5__, a game developed by Atlus, for use while playing on RPCS3.

## Prerequisites

* Latest Cheat Engine version + Big Endian Types.
* Latest RPCS3 master.
* Persona 5. This table has been tested with NPEB02436.

## Installation

1. Download and install Cheat Engine (or use the portable version).
2. Install Big Endian Types in Cheat Engine.
3. Clone or download this repository.

## Usage

1. Open RPCS3 and launch `Persona 5`.
2. Open Cheat Engine and load `rpcs3-p5.CT`.
3. If prompted, allow the main table script to run.
4. Enable the table via the `[ENABLE]` script at the top.

---

## Table Contents

### Internal Stuff

Internal table records.

### Tools

Miscellaneous utilities.

#### Experience Calculator

By entering a value in the level field, you can get the _minimal required experience_ to reach that level for a given persona or party member.

#### Name Changer

Using this tool, you can change the Hero's first and last name, as well as your group name.

This tool limits you to the available characters for names in the English release of the game as the game might crash when using an invalid character.

#### Compendium Unlocker

Click the checkbox to unlock or lock a persona in the compendium.

__WARNING:__ Locking a persona and then unlocking it would reset all persona stats.

#### Randomized Encounter Music

To use the script, follow these steps:

__Step 1:__ Add the following patch (modified from TGE's original one) to your Persona 5 `patch.yml` file, **above the `PPU-<hash>` segment**:

``` yml
p5_RandomizedEncounterMusicCE: &p5_RandomizedEncounterMusicCE
    - [ be32, 0x0063ACE4, 0x48B44B87 ]
    - [ be32, 0x0063ACE8, 0x4806CCBB ]
    - [ be32, 0x00B44B84, 0x2C1F012C ]
    - [ be32, 0x00B44B88, 0x41820008 ]
    - [ be32, 0x00B44B8C, 0x4E800020 ]
    - [ be32, 0x00B44B90, 0x4806CCCB ]
    - [ be32, 0x00B44B94, 0x4863ACEA ]
```

__Step 2:__ Add the following to your Persona 5 `patch.yml` file, **under the `PPU-<hash>` segment**:

``` yml
    - [ load, p5_RandomizedEncounterMusicCE ] # Enabled via Cheat Engine
```

__Step 3:__ Restart the game for the `patch.yml` changes to take effect.

__Step 4:__ Enable the _Randomized Encounter Music_ tool via the `[ENABLE]` scripts in the cheat table.

### Party Stats

Edit stats relating to party members:

* _HP, SP:_ Should be obvious.
* _Ailments:_ Various ailment flags.
* _Level, EXP_:
  * Only relevant to the Hero.
  * Use the _Experience Calculator_ in the _Tools_ section to get correct values for these entries.
  * Editing the level is not recommended, instead edit the EXP, then enter and win a battle to initiate the game's level-up process.
  * **Party member's level and EXP are tied to their persona's level and EXP**.
* _Buff Status_: Flags that determine whether a buff is active or not.
* _Buff Direction_: Determines a buff's direction (e.g. ATK+ or ATK-).
* _Buff Duration_: The amount of turns in which a buff is active.
* _Persona_: A collection of the combatant's persona. Note that only the hero can have more than one persona, however all party members (and enemies) use the same data structure and so the table accounts for that. Available stats for each persona include:

  * _Level, EXP_: Should be obvious. These also represent each party member's (but not the Hero's, see above) Level and EXP.
  * _Skills_: Should be obvious.
  * _Stats_: Should be obvious.

* _Equip_: Equipped gear.
* _Bullets:_ Should be obvious.
* _HP Gain, SP Gain_: The HP and SP gained from training. Normally can only be increased by the Hero, however you can set these manually for other party members and their HP and SP will increase accordingly.

### Inventory

Items are grouped in the table as they are grouped in the game's memory.

### General

Contains various game stats that didn't fit in any other category: Money, Romance, Batting, Training, Fishing and Palace stats.

You can also edit time related values:

* To repeat a day's first timeslot, during an event, set `Day Timeslot` to `3`.
* To repeat a day's second timeslot, during an event, set `Day Timeslot` to `5`.

Editing the day count itself, `Day #`, is highly discouraged.

### Trophy Counters

Various trophy counters that track when a trophy is unlocked.

__This is particularly helpful to track the progress of the "Passionate Listener" trophy.__ Contrary to popular belief, this trophy only tracks lines spoken _during combat_ using _either navigator_.

### Compendium

Allows you to edit persona records in the compendium.

You can also unlock or lock persona records using the [Compendium Unlocker](#compendium-unlocker).

### Confidants

Allows you to edit both the confidant’s current rank and the confidant's affinity (determines whether the confidant will rank up the next time you meet with them).

Changing a confidant's rank via the table is not recommended, instead change the affinity and then initiate a rank up in game.

### Social Stats

Edit the Hero's Knowledge, Charm, etc.

Numbers in parentheses indicate how many points are needed to level up a stat per each possible level.

| Stat        | Level 2 | 3  | 4   | 5   |
|-------------|--------:|---:|----:|----:|
| Knowledge   | 34      | 82 | 126 | 192 |
| Charm       | 6       | 52 | 92  | 132 |
| Proficiency | 12      | 34 | 60  | 87  |
| Guts        | 11      | 29 | 57  | 113 |
| Kindness    | 14      | 44 | 91  | 136 |

* 1 note - 2 points.
* 2 notes - 3 points.
* 3 notes - 5 points.

### Enemies

When in battle, enable this record to view enemy stats.

This record does not auto-update, so you'd have to toggle the record to see newly summoned enemies.
