**This document is OUTDATED. For individual aliases, please see the Fighter folder.**

# Fighter

Avrae is a powerful D&D 5E Discord bot used to make rolls and streamline playing online. This list includes commands (aliases and snippets) for the fighter class.

## Creating a Fighter

First, [create a character sheet](#creating-a-character). 

Now, scroll down and find the commands you want. You do not need to use every command here, but many automate tasks such as counter tracking and regaining hit points such as Second Wind. They also include a description and a page number to find each feature.

### Quick Build

You can set up your fighter aliases quickly by clicking this [link](#creating-a-quick-fighter) and following the directions there.

### Setting up a Command

After finding a command you want, if you have a DiceCloud sheet and you linked your features to your counters as described in [Creating a Character](#creating-a-character), follow the instructions in the DiceCloud section. 

If you have any other sheet, or you have DiceCloud and you do not want to link your features, follow the instructions in the Alternative box.

#### DiceCloud

Create a feature with the name and number of uses stated in the **Prerequisites** box. Copy and paste the text exactly. 

In the description box of your feature, make sure the phrase stated for the command is there. For instance, if you have the Second Wind ability, and the Recharge section says to include the phrase ``short rest``, double-check to make sure it is there. If it is not, add it.

Then, send the command in the **Code** box. If there are two code blocks, send the text in the DiceCloud box.

#### Alternative

Copy the command in the **Prerequisites** box. Fill out any fields the description asks of you. Send the completed command.

Then, send the text in the **Code** box. If there are two code blocks, use the Alternative box.

### Changing Command Name

To change the command name, replace the word following ``alias`` or ``snippet`` such as ``bsw`` in ``!alias bsw ...``. To use an alias, type the command name, such as ``!bsw``. To use a snippet, type ``!a $weapon$ $snippet$``, replacing ``$weapon$`` with a weapon on your character sheet, and ``$snippet$`` with the name of your snippet.

### Multiclassing with Alternative Sheets

If you are multiclassing with a non-DiceCloud sheet, run the following command, replacing ``$flvl$`` with your current fighter level.

```GN
!cvar FighterLevel $flvl$
```

If there are two boxes of code, use the DiceCloud box instead of the Alternative box. **IMPORTANT: *In addition, whenever you gain a level in fighter, run the command again, replacing*** ``$flvl$`` ***with your new fighter level.***

This will update all of your aliases with your new fighter level.

### (Optional) Color

You can also set up a color by sending the following code to Avrae, replacing ``$hex$`` with a [color hex code](https://www.webpagefx.com/web-design/color-picker/). Do not include the hashtag (#). You do not need to run this for commands to function properly.

```GN
!multiline
!csettings color $hex$
!cvar color $hex$
```

## The Fighter Table

| Level | Proficiency Bonus | Features | Cantrips Known | Spells Known | 1st | 2nd | 3rd | 4th |
|-------|-------------------|---------------------------------------------------|----------------|--------------|-----|-----|-----|-----|
| 1st | +2 | [Hit Dice (d10)]((#hit-dice-\(d10\))), [Fighting Style](#fighting-style), [Second Wind](#second-wind) | — | — | — | — | — | — |
| 2nd | +2 | [Action Surge](#action-surge) | — | — | — | — | — | — |
| 3rd | +2 | [Martial Archetype](#martial-archetype) | 2 | 3 | 2 | — | — | — |
| 4th | +2 | [Ability Score Improvement](#ability-score-improvement) | 2 | 4 | 3 | — | — | — |
| 5th | +3 | [Extra Attack](#extra-attack) | 2 | 4 | 3 | — | — | — |
| 6th | +3 | [Ability Score Improvement](#ability-score-improvement) | 2 | 4 | 3 | — | — | — |
| 7th | +3 | [Martial Archetype feature](#martial-archetype) | 2 | 5 | 4 | 2 | — | — |
| 8th | +3 | [Ability Score Improvement](#ability-score-improvement) | 2 | 6 | 4 | 2 | — | — |
| 9th | +4 | [Indomitable](#indomitable) | 2 | 6 | 4 | 2 | — | — |
| 10th | +4 | [Martial Archetype feature](#martial-archetype) | 3 | 7 | 4 | 3 | — | — |
| 11th | +4 | [Extra Attack (2)](#extra-attack) | 3 | 8 | 4 | 3 | — | — |
| 12th | +4 | [Ability Score Improvement](#ability-score-improvement) | 3 | 8 | 4 | 3 | — | — |
| 13th | +5 | [Indomitable (two uses)](#indomitable) | 3 | 9 | 4 | 3 | 2 | — |
| 14th | +5 | [Ability Score Improvement](#ability-score-improvement) | 3 | 10 | 4 | 3 | 2 | — |
| 15th | +5 | [Martial Archetype feature](#martial-archetype) | 3 | 10 | 4 | 3 | 2 | — |
| 16th | +5 | [Ability Score Improvement](#ability-score-improvement) | 3 | 11 | 4 | 3 | 3 | — |
| 17th | +6 | [Action Surge (two uses)](#action-surge), [Indomitable (three uses)](#indomitable) | 3 | 11 | 4 | 3 | 3 | — |
| 18th | +6 | [Martial Archetype feature](#martial-archetype) | 3 | 11 | 4 | 3 | 3 | — |
| 19th | +6 | [Ability Score Improvement](#ability-score-improvement) | 3 | 12 | 4 | 3 | 3 | 1 |
| 20th | +6 | [Extra Attack (3)](#extra-attack) | 3 | 13 | 4 | 3 | 3 | 1 |

# Class Commands

As a fighter, you have the following aliases and snippets.

## Hit Dice (d10)

Displays text and page number for Hit Dice. Subtracts from Hit Dice counter and rolls hit dice, then adds result rolled to current hit points. Returns error if attempting to spend more hit dice than remaining.

#### Prerequisites

**DiceCloud Feature Name:** ``Hit Dice (d10)``  
**Uses:** ``FighterLevel``  
**Recharge:** Do not include the words ``short rest`` or ``long rest`` in your feature, as you only regain half your Hit Dice on a long rest.

Alternatively, run the following code, replacing ``$flvl$`` with your current fighter level. **IMPORTANT: *Whenever you gain a level in fighter, run this command again.***

```GN
!cc create "Hit Dice (d10)" -min 0 -max $flvl$ -type default
```

To regain hit dice, you can run the following alias. 

``!hdr <die> <num>``

``<die>`` - Die size (ex. ``d10``)  
``<num>`` - Number of hit dice you are regaining (ex. ``5``)

*Example:* ``!hdr d10 5``

```GN
!alias hdr embed 
{{mod_cc("Hit Dice (%1%)", %2%)}} 
-title "<name> regains spent Hit Dice!" 
-desc "At the end of a long rest, you regain spent Hit Dice, up to a number of dice equal to half your total number of them." 
-f "Hit Dice (%1%)|{{get_cc("Hit Dice (%1%)")}} / {{get_cc_max("Hit Dice (%1%)")}}" 
-footer "Adventuring | PHB 186" 
-color <color>
```

#### Usage

``!hd <die> <num>``

``<die>`` - Die size (ex. ``d10``)  
``<num>`` - Number of hit dice you are expending (ex. ``2``)

*Example:* ``!hd d10 2``


#### Code

```GN
!alias hd embed 
{{mod_cc("Hit Dice (%1%)", -%2%, True)}} 
{{set("heal", vroll("%2%%1%+"+str(constitutionMod*%2%)))}} 
{{set_hp(min(hp, heal.total + currentHp))}} 
-title "<name> takes a Short Rest!" 
-desc "A character can spend one or more Hit Dice at the end of a short rest, up to the character's maximum number of Hit Dice, which is equal to the character's level. 

For each Hit Die spent in this way, the player rolls the die and adds the character's Constitution modifier to it. The character regains hit points equal to the total." 
-f "Healing Recieved|{{heal}}" 
-f "Hit Points|{{get_hp()}} / {{hp}}" 
-f "Hit Dice (%1%)|{{get_cc("Hit Dice (%1%)")}} / {{get_cc_max("Hit Dice (%1%)")}}" 
-footer "Adventuring | PHB 186" 
-color <color>
```

## Second Wind

Displays text and page number for Second Wind. Rolls 1d10 + your fighter level and adds the result to your current hit points. Subtracts 1 from Second Wind counter. Returns error if Second Wind is already used.

#### Prerequisites

**DiceCloud Feature Name:** ``Hit Dice (d10)``  
**Uses:** ``FighterLevel``  
**Recharge:** Include the words ``short rest`` in your feature

Alternatively, run the following code.

```GN
!cc create "Second Wind" -min 0 -max 1 -reset short -type bubble
```

To reset your Second Wind, type ``!g [shortrest|sr]`` or ``!g [longrest|lr]``.

#### Code

If your sheet is on DiceCloud, use the **DiceCloud** box. Otherwise, use the **Alternative** box.

###### DiceCloud

```GN
!alias bsw embed 
{{set("counter", "Second Wind")}} 
{{mod_cc(counter, -1, True)}} 
{{set("lvl", FighterLevel)}} 
{{set("heal", vroll("1d10+"+str(lvl)))}} 
{{set_hp(min(hp, heal.total + currentHp))}} 
-title "<name> uses {{counter}}!" 
-desc "On your turn, you can use a bonus action to regain hit points equal to 1d10 + your fighter level. Once you use this feature, you must finish a short or long rest before you can use it again." 
-f "Healing Recieved|{{str(heal)}}" 
-f "Hit Points|{{get_hp()}} / {{hp}}" 
-f "{{counter}}|〇" 
-footer "Fighter | PHB 72" 
-color <color>
```

###### Alternative

```GN
!alias bsw embed 
{{set("counter", "Second Wind")}} 
{{mod_cc(counter, -1, True)}} 
{{set("lvl", level)}} 
{{set("heal", vroll("1d10+"+str(lvl)))}} 
{{set_hp(min(hp, heal.total + currentHp))}} 
-title "<name> uses {{counter}}!" 
-desc "On your turn, you can use a bonus action to regain hit points equal to 1d10 + your fighter level. Once you use this feature, you must finish a short or long rest before you can use it again." 
-f "Healing Recieved|{{str(heal)}}" 
-f "Hit Points|{{get_hp()}} / {{hp}}" 
-f "{{counter}}|〇" 
-footer "Fighter | PHB 72" 
-color <color>
```

## Action Surge

Displays text and page number for Action Surge. Subtracts 1 from Action Surge counter. Returns error if no uses of Action Surge left.

#### Prerequisites

**DiceCloud Feature Name:** ``Action Surge``  
**Uses:** ``1+floor(FighterLevel/17)``  
**Recharge:** Include the words ``short rest`` in your feature

Alternatively, run the following code, replacing ``$uses$`` with the number of Action Surge uses you have.

```GN
!cc create "Action Surge" -min 0 -max $uses$ -reset short -type bubble
```

To reset your Action Surge, type ``!g [shortrest|sr]`` or ``!g [longrest|lr]``.

#### Code

```GN
!alias bas embed 
{{set("counter", "Action Surge")}} 
{{mod_cc(counter, -1, True)}} 
-title "<name> uses {{counter}}!" 
-desc "On your turn, you can take one additional action on top of your regular action and a possible bonus action. Once you use this feature, you must finish a short or long rest before you can use it again." 
-f "{{counter}}|{{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))}}" 
-footer "Fighter | PHB 72" 
-color <color>
```

## Indomitable

Displays text and page number for Indomitable. Subtracts 1 from Indomitable counter. Returns error if no uses of Indomitable left.

#### Prerequisites

**DiceCloud Feature Name:** ``Indomitable``  
**Uses:** ``1+floor(FighterLevel/13)+floor(FighterLevel/17)``  
**Recharge:** Include the words ``long rest`` in your feature

Alternatively, run the following code, replacing ``$uses$`` with the number of Indomitable uses you have.

```GN
!cc create "Indomitable" -min 0 -max $uses$ -reset long -type bubble
```

To reset your Indomitable, type ``!g [longrest|lr]``.

#### Code

```GN
!alias bi embed 
{{set("counter", "Indomitable")}} 
{{mod_cc(counter, -1, True)}} 
-title "<name> uses {{counter}}!" 
-desc "Beginning at 9th level, you can reroll a saving throw that you fail. If you do so, you must use the new roll, and you can’t use this feature again until you finish a long rest." 
-f "{{counter}}|{{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))}}" 
-footer "Fighter | PHB 72" 
-color <color>
```
