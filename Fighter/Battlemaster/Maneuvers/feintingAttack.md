# Feinting Attack
*By Toothless#7854*

<p align="center">
  <img src="https://i.imgur.com/ABloj1w.png"/>
</p>

Subtracts 1 from "Superiority Dice" counter. Adds advantage and Superiority Die to attack and damage roll.

### Usage

``![attack|a] [atk_name=list] feinting``

### Setup
Run the command in the **Code** section. It will automatically setup counters and cvars.

### Code
```GN
!snippet feinting
{{set_cvar_nx("showpage", "true")}}
{{set_cvar("showpage", "false") if str(showpage) != "true" else ""}}
{{set("pgNum", "PHB 74")}}
{{set("counter", "Superiority Dice")}}
{{set("lvl", FighterLevel if exists("FighterLevel") else level)}}
{{create_cc_nx(counter, 0, 4 if lvl < 7 else 5 if lvl < 15 else 6, "short", "bubble")}}
{{set("valid", 1 if get_cc(counter) > 0 else 0)}}
{{mod_cc(counter, -1) if valid else ""}}
{{set("sd", "8" if lvl < 10 else "10" if lvl < 18 else "12")}}
{{"adv" if valid else ""}}
{{"-d1 \"1d" + sd + " [feinting]\"" if valid else ""}}
-phrase "**Feinting Attack.** {{"You have advantage on your next attack roll against that creature this turn." if valid else "A superiority die is expended when you use it. You regain all of your expended superiority dice when you finish a short or long rest. (``!g sr``)"}} {{"(" + pgNum + ") " if str(showpage) == "true" else ""}}[{{get_cc(counter)}} / {{get_cc_max(counter)}}]"
```

### Personalization Options

**``!snippet $snippet_name$ ...``** - Changes the name to run the command. Replace ``feinting`` in the command in the **Code** section.

**``!csettings color $hex$``** - Colors all embeds this color. Replace ``$hex$`` with a hex code. Do not include the hashtag (#).

**``!cvar showpage true / false``** - Enables / disables whether subjects and page numbers are displayed.

### Multiclassing

If you are multiclassing and you are not using a DiceCloud sheet, run the following command, replacing ``$lvl$`` with your current fighter level.

```GN
!cvar FighterLevel $lvl$
```

**You must run this command every time you gain a fighter level.** If you do not do this, the alias will use your total level instead of your Fighter level. This may cause problems in your aliases.
