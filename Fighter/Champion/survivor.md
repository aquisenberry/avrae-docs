# Survivor
*By Toothless#7854.*

<p align="center">
  <img src="https://i.imgur.com/mcYvM42.png"/>
</p>

Regains hit points equal to 5 + your Constitution modifier. Does not give any benefit if user has more than half of their hit points or at 0 hit points.

### Setup
Run the command in the **Code** section. It will automatically setup counters and cvars.

### Personalization Options

**``!alias $alias_name$ embed...``** - Changes the name to run the command. Replace ``survivor`` in the command in the **Code** section.

**``!csettings color $hex$``** - Colors all embeds this color.

**``!cvar embedimage true / false``** - Enables / disables whether a character's image is automatically embedded.

**``!cvar showpage true / false``** - Enables / disables whether subjects and page numbers are displayed.

### Code
```GN
!alias survivor embed 
{{set_cvar_nx("embedimage", "true")}}
{{set_cvar("embedimage", "false") if str(embedimage) != "true" else ""}}
{{set_cvar_nx("showpage", "true")}}
{{set_cvar("showpage", "false") if str(showpage) != "true" else ""}}
{{set("pgSubject", "Fighter")}}
{{set("pgNum", "PHB 73")}}
{{set("counter", "Survivor")}}
{{set("valid", 1 if get_hp()<=(hp/2) and get_hp() > 0 else 0)}}
{{set('heal', 5+constitutionMod if valid else 0)}}
{{mod_hp(heal, False) if valid else ""}} 
-title "<name> {{"uses" if valid else "attempted to use"}} {{counter}}!"
-desc "{{"At the start of each of your turns, you regain hit points equal to 5 + your Constitution modifier if you have no more than half of your hit points left. You don’t gain this benefit if you have 0 hit points." if valid else "You must have no more than half of your hit points left. You don’t gain this benefit if you have 0 hit points."}}"
-f "Healing Recieved|{{"( " if valid == 0 else ""}}5 + {constitutionMod}{{" ) × 0" if valid == 0 else ""}} = ``{{heal}}``" 
-f "Hit Points|{{get_hp()}} / {{hp}}" 
{{"-footer \"" + pgSubject + " | " + pgNum + "\"" if str(showpage) == "true" else ""}}
{{"-thumb <image>" if str(embedimage) == "true" else ""}}
-color <color>
```
