# Precision Attack
*By Toothless#7854*

<p align="center">
  <img src="https://i.imgur.com/03zO7Qf.png"/>
</p>

Subtracts 1 from "Superiority Dice" counter. Rolls superiority die for attack bonus.

### Usage

``!precision [attack_roll]``

Adds superiority die to attack roll if given.

### Setup
Run the command in the **Code** section. It will automatically setup counters and cvars.

### Code

```GN
!alias precision embed
{{set_cvar_nx("embedimage", "true")}}
{{set_cvar("embedimage", "false") if str(embedimage) != "true" else ""}}
{{set_cvar_nx("showpage", "true")}}
{{set_cvar("showpage", "false") if str(showpage) != "true" else ""}}
{{set("pgSubject", "Fighter")}}
{{set("pgNum", "PHB 74")}}
{{set("counter", "Superiority Dice")}}
{{set("lvl", FighterLevel if exists("FighterLevel") else level)}}
{{create_cc_nx(counter, 0, 4 if lvl < 7 else 5 if lvl < 15 else 6, "short", "bubble")}}
{{set("valid", 1 if get_cc(counter) > 0 else 0)}}
{{mod_cc(counter, -1) if valid else ""}}
{{set("sd", "8" if lvl < 10 else "10" if lvl < 18 else "12")}}
{{set("atk", "%1%")}}
{{set("validAtk", atk.isdigit())}}
{{set("roll", vroll((atk + " + " if validAtk else "") + "1d" + str(sd)))}}
-title "<name> {{"uses" if valid else "attempted to use"}} Precision Attack!"
-desc "{{"When you make a weapon attack roll against a creature, you can expend one superiority die to add it to the roll.\n\nYou can use this maneuver before or after making the attack roll, but before any effects of the attack are applied." if valid else "A superiority die is expended when you use it. You regain all of your expended superiority dice when you finish a short or long rest. (``!g sr``)"}}"
{{"-f \"Attack " + ("Roll" if validAtk else "Bonus") + "  | " + str(roll) + "\"" if valid else ""}}
-f "{{counter}} | {{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))}}"
{{"-footer \"" + pgSubject + " | " + pgNum + "\"" if str(showpage) == "true" else ""}}
{{"-thumb <image>" if str(embedimage) == "true" else ""}}
-color <color>
```

### Personalization Options

**``!alias $alias_name$ embed...``** - Changes the name to run the command. Replace ``precision`` in the command in the **Code** section.

**``!csettings color $hex$``** - Colors all embeds this color. Replace ``$hex$`` with a hex code. Do not include the hashtag (#).

**``!cvar embedimage true / false``** - Enables / disables whether a character's image is automatically embedded.

**``!cvar showpage true / false``** - Enables / disables whether subjects and page numbers are displayed.

### Multiclassing

If you are multiclassing and you are not using a DiceCloud sheet, run the following command, replacing ``$lvl$`` with your current fighter level.

```GN
!cvar FighterLevel $lvl$
```

**You must run this command every time you gain a fighter level.** If you do not do this, the alias will use your total level instead of your Fighter level. This may cause problems in your aliases.
