# Indomitable
*By Toothless#7854.*

<p align="center">
  <img src="https://i.imgur.com/Azv7Ii0.png"/>
</p>

Subtracts 1 from "Indomitable" counter. Prompts user to take a short or long rest if "Indomitable" counter is not greater than 0. 

### Setup
Run the command in the **Code** section. It will automatically setup counters and cvars.

### Personalization Options

**``!alias $alias_name$ embed...``** - Changes the name to run the command. Replace ``indomitable`` in the command in the **Code** section.

**``!csettings color $hex$``** - Colors all embeds this color.

**``!cvar embedimage true / false``** - Enables / disables whether a character's image is automatically embedded.

**``!cvar showpage true / false``** - Enables / disables whether subjects and page numbers are displayed.

### Code
```GN
!alias indomitable embed 
{{set_cvar_nx("embedimage", "true")}}
{{set_cvar("embedimage", "false") if str(embedimage) != "true" else ""}}
{{set_cvar_nx("showpage", "true")}}
{{set_cvar("showpage", "false") if str(showpage) != "true" else ""}}
{{set("pgSubject", "Fighter")}}
{{set("pgNum", "PHB 72")}}
{{set("counter", "Indomitable")}}
{{set("lvl", FighterLevel if exists("FighterLevel") else level)}} 
{{create_cc_nx(counter, 0, 1 if lvl < 13 else 2 if lvl < 17 else 3, "long", "bubble")}}
{{set("valid", 1 if get_cc(counter) > 0 else 0)}}
{{mod_cc(counter, -1) if valid else ""}} 
-title "<name> {{"uses" if valid else "attempted to use"}} {{counter}}!" 
-desc "{{"Beginning at 9th level, you can reroll a saving throw that you fail. If you do so, you must use the new roll, and you can’t use this feature again until you finish a long rest.\n\nYou can use this feature twice between long rests starting at 13th level and three times between long rests starting at 17th level." if valid else "You can’t use this feature again until you finish a long rest.\n\nYou can use this feature twice between long rests starting at 13th level and three times between long rests starting at 17th level. (``!g lr``)"}}" 
-f "{{counter}} | {{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))}}"
{{"-footer \"" + pgSubject + " | " + pgNum + "\"" if str(showpage) == "true" else ""}}
{{"-thumb <image>" if str(embedimage) == "true" else ""}}
-color <color>
```
