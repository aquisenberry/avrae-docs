# Fighter
*By silverbass#2407*

**Hit Dice:** ``!cvar hd d10`` & ``!cc create "Hit Dice" -reset none -max <level> -min 0``

| Level | Proficiency Bonus | Features                    | Cantrips Known | Spells Known | 1st | 2nd | 3rd | 4th |
|:-----:|:-----------------:|-----------------------------|:--------------:|:------------:|:---:|:---:|:---:|:---:|
| 1st   | +2                | [Fighting Style](#fighting-style), [Second Wind](#second-wind) | —              | —            | —   | —   | —   | —   |
| 2nd   | +2                | [Action Surge](#action-surge) | —              | —            | —   | —   | —   | —   |
| 3rd   | +2                | [Martial Archetype](#martal-archetype)           | 2              | 3            | 2   | —   | —   | —   |
| 4th   | +2                | [Ability Score Improvement](#ability-score-improvement) | 2              | 4            | 3   | —   | —   | —   |
| 5th   | +3                | [Extra Attack](#extra-attack)              | 2              | 4            | 3   | —   | —   | —   |
| 6th   | +3                | [Ability Score Improvement](#ability-score-improvement) | 2              | 4            | 3   | —   | —   | —   |
| 7th   | +3                | [Martial Archetype feature](#martal-archetype)   | 2              | 5            | 4   | 2   | —   | —   |
| 8th   | +3                | [Ability Score Improvement](#ability-score-improvement) | 2              | 6            | 4   | 2   | —   | —   |
| 9th   | +4                | [Indomitable](#indomitable)                 | 2              | 6            | 4   | 2   | —   | —   |
| 10th  | +4                | [Martial Archetype feature](#martal-archetype)   | 3              | 7            | 4   | 3   | —   | —   |
| 11th  | +4                | [Extra Attack (2)](#extra-attack)            | 3              | 8            | 4   | 3   | —   | —   |
| 12th  | +4                | [Ability Score Improvement](#ability-score-improvement) | 3              | 8            | 4   | 3   | —   | —   |
| 13th  | +5                | [Indomitable (two uses)](#indomitable)      | 3              | 9            | 4   | 3   | 2   | —   |
| 14th  | +5                | [Ability Score Improvement](#ability-score-improvement) | 3              | 10           | 4   | 3   | 2   | —   |
| 15th  | +5                | [Martial Archetype feature](#martal-archetype)   | 3              | 10           | 4   | 3   | 2   | —   |
| 16th  | +5                | [Ability Score Improvement](#ability-score-improvement) | 3              | 11           | 4   | 3   | 3   | —   |
| 17th  | +6                | [Action Surge (two uses)](#action-surge), [Indomitable (three uses)](#indomitable)   | 3              | 11           | 4   | 3   | 3   | —   |
| 18th  | +6                | [Martial Archetype feature](#martal-archetype)   | 3              | 11           | 4   | 3   | 3   | —   |
| 19th  | +6                | [Ability Score Improvement](#ability-score-improvement) | 3              | 12           | 4   | 3   | 3   | 1   |
| [20th](#creating-a-quick-fighter)  | +6                | [Extra Attack (3)](#extra-attack)             | 3              | 13           | 4   | 3   | 3   | 1   |

## Fighting Style
### Archery
Modify your character sheet to have a +2 to hit on attack rolls with ranged weapons.

### Defense
Modify your character sheet to have a +1 bonus to AC if they are wearing armor.

### Great Weapon Fighting
Modify your character sheet to such that the damage dice uses the ``ro1ro2`` tag.  
*Example:* ``1d12ro1ro2 + 4 [slashing]``

### Protection
**Alias:**  
```
!alias protection embed -title "<name> uses the Protection Fighting Style!" -desc "When a creature you can see attacks a target other than you that is within 5 feet of you, you can use your reaction to impose disadvantage on the attack roll. You must be wielding a shield." -thumb <image>
```
**Use With:** ``!protection``

### Two-Weapon Fighting
Modify your character sheet to have an "Offhand Attack", and add your ability modifier to the damage on that attack.

## Second Wind

**Custom Counters Required:** ``!cc create "Second Wind" -min 0 -max 1 -type bubble -reset short``  
**Alias:**
```
!alias 2nd embed {{set("counter", "Second Wind")}} {{mod_cc(counter, -1, True)}} {{set("heal", vroll("1d10+"+str(level)))}} {{set_hp(min(hp, heal.total + currentHp))}} -title "<name> uses {{counter}}!" -desc "On your turn, you can use a bonus action to regain 1d10 + {level} HP. Once you use this feature, you must finish a short or long rest before you can use it again. *(PHB 72)*" -f "Healing Recieved|{{str(heal)}}" -f "Hit Points|{{get_hp()}} / {{hp}}" -f "{{counter}}|〇" -color <color> -thumb <image>
```
**Use With:** ``!2nd``

## Action Surge

**Custom Counters Required:** ``!cc create "Action Surge" -min 0 -max 1 -type bubble -reset short`` Change the ``1`` to ``2`` at level 17.  
**Alias:**
```
!alias asurge embed {{set("counter", "Action Surge")}} {{mod_cc(counter, -1, True)}} -title "<name> uses {{counter}}!" -desc "On your turn, you can take one additional action on top of your regular action and a possible bonus action. Once you use this feature, you must finish a short or long rest before you can use it again. (PHB 72)" -f "{{counter}}|〇" -color <color> -thumb <image>
```
**Use With:** ``!asurge``

## Martial Archetype
At 3rd level, you choose an archetype from the list available that you strive to emulate in your combat styles and techniques. The archetype you choose grants you features at 3rd level and again at 7th, 10th, 15th, and 18th level.
* [Arcane Archer]()
* [Battle Master]()
* [Cavalier]()
* [Champion]()
* [Eldritch Knight]()
* [Purple Dragon Knight (Banneret)]()
* [Samurai]()

## Ability Score Improvement
Modify your character sheet to increase one ability score by 2, or increase two ability scores by 1. As normal, you can't increase an ability score above 20 using this feature.

If your DM allows the use of feats, you may instead take a feat. (<---insert hyperlink to Feat page)  

## Extra Attack
When you take a turn in combat, you can attack twice, instead of once, whenever you take the Attack action on your turn.

The number of attacks increases to three when you reach 11th level in this class and to four when you reach 20th level in this class.

You can roll multiple attacks in Avrae at once using the ``-rr #`` command.  
*Example:* ``!init attack <target> Longsword -rr 2``

## Indomitable
**Custom Counters Required:** ``!cc create "Indomitable" -min 0 -max 1 -type bubble -reset long``  Change the ``1`` to ``2`` at level 13, and to ``3`` at level 17.  
**Alias:**
```
!alias indomitable embed {{set("counter", "Indomitable")}} {{mod_cc(counter, -1, True)}} -title "<name> uses {{counter}}!" -desc "Beginning at 9th level, you can reroll a saving throw that you fail. If you do so, you must use the new roll, and you can’t use this feature again until you finish a long rest. *(PHB 72)*" -f "{{counter}}|{{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))}}" -color <color> -thumb <image>
```
**Use With:** ``!indomitable``


# Creating a Quick Fighter

To quickly make a level 20 fighter, copy and paste the alias below. This section requires some understanding of the underlying syntax used by Avrae, and may not be suitable for beginners.    
```
!multiline
!cvar hd d10
!cc create "Hit Dice" -reset none -max <level> -min 0
!cc create "Second Wind" -min 0 -max 1 -type bubble -reset short
!alias 2nd embed {{set("counter", "Second Wind")}} {{mod_cc(counter, -1, True)}} {{set("heal", vroll("1d10+"+str(level)))}} {{set_hp(min(hp, heal.total + currentHp))}} -title "<name> uses {{counter}}!" -desc "On your turn, you can use a bonus action to regain 1d10 + {level} HP. Once you use this feature, you must finish a short or long rest before you can use it again. *(PHB 72)*" -f "Healing Recieved|{{str(heal)}}" -f "Hit Points|{{get_hp()}} / {{hp}}" -f "{{counter}}|〇" -color <color> -thumb <image>
!cc create "Action Surge" -min 0 -max 2 -type bubble -reset short
!alias asurge embed {{set("counter", "Action Surge")}} {{mod_cc(counter, -1, True)}} -title "<name> uses {{counter}}!" -desc "On your turn, you can take one additional action on top of your regular action and a possible bonus action. Once you use this feature, you must finish a short or long rest before you can use it again. (PHB 72)" -f "{{counter}}|〇" -color <color> -thumb <image>
!cc create "Indomitable" -min 0 -max 3 -type bubble -reset long
!alias indomitable embed {{set("counter", "Indomitable")}} {{mod_cc(counter, -1, True)}} -title "<name> uses {{counter}}!" -desc "Beginning at 9th level, you can reroll a saving throw that you fail. If you do so, you must use the new roll, and you can’t use this feature again until you finish a long rest. *(PHB 72)*" -f "{{counter}}|{{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))}}" -color <color> -thumb <image>
```
* To make a fighter of level 1, remove everything past the ``!alias 2nd ...``  
* To make a fighter of level 2-8, remove everything past the ``!alias asurge...`` and adjust the ``-max 2`` to ``-max 1``
* To make a fighter of level 9-12, adjust the ``-max 2`` to ``-max 1`` for the ``!cc create "Action Surge"...`` and adjust the ``-max 3`` to ``-max 1`` for the ``!cc create "Indomitable"...``
* To make a fighter of level 13-16, adjust the ``-max 2`` to ``-max 1`` for the ``!cc create "Action Surge"...`` and adjust the ``-max 3`` to ``-max 2`` for the ``!cc create "Indomitable"...``
* To make a fighter of level 17-20, copy the entire ``!multiline`` as is.
