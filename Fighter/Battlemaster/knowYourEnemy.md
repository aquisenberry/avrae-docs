# Know Your Enemy
*By Toothless#7854.*

<p align="center">
  <img src="https://i.imgur.com/9dzABzv.png"/>
</p>

Displays Strength, Dexterity, and Constitution score, AC, current hit points, total level, and fighter level.

### Setup
Run the command in the **Code** section. It will automatically setup counters and cvars.

### Personalization Options

**``!alias $alias_name$ embed...``** - Changes the name to run the command. Replace ``know`` in the command in the **Code** section.

**``!csettings color $hex$``** - Colors all embeds this color. Replace ``$hex$`` with a hex code. Do not include the hashtag (#).

**``!cvar embedimage true / false``** - Enables / disables whether a character's image is automatically embedded.

**``!cvar showpage true / false``** - Enables / disables whether subjects and page numbers are displayed.

### Multiclassing

If you are multiclassing and you are not using a DiceCloud sheet, run the following command, replacing ``$lvl$`` with your current fighter level.

```GN
!cvar FighterLevel $lvl$
```

**You must run this command every time you gain a fighter level.** If you do not do this, the alias will use your total level instead of your Fighter level. This may cause problems in your aliases.

### Usage

``!know``

### Code
```GN
!alias know embed 
{{set_cvar_nx("embedimage", "true")}}
{{set_cvar("embedimage", "false") if str(embedimage) != "true" else ""}}
{{set_cvar_nx("showpage", "true")}}
{{set_cvar("showpage", "false") if str(showpage) != "true" else ""}}
{{set("pgSubject", "Fighter")}}
{{set("pgNum", "PHB 73 - 74")}}
{{set("counter", "Know Your Enemy")}}
-title "<name> uses {{counter}}!" 
-desc "if you spend at least 1 minute observing or interacting with another creature outside combat, the DM tells you if the creature is your equal, superior, or inferior in regard to two of the following characteristics of your choice:" 
-f "STR | {{strength}}" 
-f "DEX | {{dexterity}}" 
-f "CON | {{constitution}}" 
-f "AC | {{armor}}" 
-f "Current HP | {{get_hp()}}" 
-f "Level (if any) | {{level}}" 
-f "Fighter Level (if any) | {{FighterLevel}}" 
{{"-footer \"" + pgSubject + " | " + pgNum + "\"" if str(showpage) == "true" else ""}}
{{"-thumb <image>" if str(embedimage) == "true" else ""}}
-color <color>
```
