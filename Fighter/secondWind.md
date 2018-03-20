# Second Wind
*By Toothless#7854.*

<p align="center">
  <img src="https://i.imgur.com/nscoFzW.png"/>
</p>

Subtracts 1 from "Second Wind" counter. Regains hit points equal to 1d10 + your fighter level. Displays current and max hit points after regaining. Displays "Second Wind" counter. Prompts user to take a short or long rest if "Second Wind" counter is not greater than 0. 

### Setup
Run the command in the **Code** section. It will automatically setup counters and cvars.

### Personalization Options

**``!alias $alias_name$ embed...``** - Changes the name to run the command. Replace ``secondWind`` in the command in the **Code** section.

**``!csettings color $hex$``** - Colors all embeds this color.

**``!cvar embedimage true / false``** - Enables / disables whether a character's image is automatically embedded.

**``!cvar showpage true / false``** - Enables / disables whether subjects and page numbers are displayed.

### Code
```GN
!alias secondWind embed 
{{set_cvar_nx("embedimage", "true")}}
{{set_cvar("embedimage", "false") if str(embedimage) != "true" else ""}}
{{set_cvar_nx("showpage", "true")}}
{{set_cvar("showpage", "false") if str(showpage) != "true" else ""}}
{{set("pgSubject", "Fighter")}}
{{set("pgNum", "PHB 72")}}
{{set("counter", "Second Wind")}}
{{set("lvl", FighterLevel if exists("FighterLevel") else level)}} 
{{create_cc_nx(counter, 0, 1, "short", "bubble")}}
{{set("valid", 1 if get_cc(counter) > 0 else 0)}}
{{mod_cc(counter, -1) if valid else ""}} 
{{set("heal", vroll("1d10+"+str(lvl)))}} 
{{mod_hp(heal.total, False) if valid else ""}} 
-title "<name> {{"uses" if valid else "attempted to use"}} {{counter}}!" 
-desc "{{"On your turn, you can use a bonus action to regain hit points equal to 1d10 + your fighter level. Once you use this feature, you must finish a short or long rest before you can use it again." if valid else "Once you use this feature, you must finish a short or long rest before you can use it again. (``!g sr``)"}}" 
{{"-f \"Healing Recieved | " + str(heal) + "\"" if valid else ""}}
{{"-f \"Hit Points | " + str(get_hp()) + " / " + str(hp) + "\"" if valid else ""}}
-f "{{counter}} | 〇" 
{{"-footer \"" + pgSubject + " | " + pgNum + "\"" if str(showpage) == "true" else ""}}
{{"-thumb <image>" if str(embedimage) == "true" else ""}}
-color <color>
```
