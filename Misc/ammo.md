# Ammunition
*By Toothless#7854.*

<p align="center">
  <img src="https://i.imgur.com/LumNmww.png"/>
</p>

<p align="center">
  <img src="https://i.imgur.com/5QA2Yxi.png"/>
</p>

``ammo`` subtracts 1 from "Ammo" counter and adds 1 to "Used Ammo" counter on attack. ``!collect`` adds half of "Used Ammo" counter to "Ammo", then sets "Used Ammo" to 0. 

### Usage

``![attack|a] [atk_name=list] ammo``

``!collect``

### Setup
Run the snippet or the alias in the **Code** section. It will automatically setup counters.

### Code
```GN
!snippet ammo
{{set_cvar_nx("showpage", "true")}}
{{set_cvar("showpage", "false") if str(showpage) != "true" else ""}}
{{set("pgNum", "PHB 146")}}
{{set("counter", "Ammo")}}
{{set("counter2", "Used Ammo")}}
{{set("existsAmmo", cc_exists(counter))}}
{{create_cc_nx(counter, 0)}}
{{create_cc_nx(counter2, 0)}}
{{"" if existsAmmo else set_cc(counter, 20)}}
{{set("valid", 1 if get_cc(counter) > 0 else 0)}}
{{mod_cc(counter, -1) if valid else ""}}
{{mod_cc(counter2, 1) if valid else ""}}
{{"" if valid else "-immune a -immune e -immune i -immune o -immune u"}}
{{"" if valid else "-phrase \"**Ammunition.** You can use a weapon that has the ammunition property to make a ranged attack only if you have ammunition to fire from the weapon." + (" (" + pgNum + ") " if str(showpage) == "true" else "") + "\""}}
-f "{{counter}} ⏐ {{counter2}} | {{get_cc(counter)}} ⏐ {{get_cc(counter2)}}"
```

```GN
!alias collect embed
{{set_cvar_nx("embedimage", "true")}}
{{set_cvar("embedimage", "false") if str(embedimage) != "true" else ""}}
{{set_cvar_nx("showpage", "true")}}
{{set_cvar("showpage", "false") if str(showpage) != "true" else ""}}
{{set("pgSubject", "Weapons")}}
{{set("pgNum", "PHB 146")}}
{{set("counter", "Ammo")}}
{{set("counter2", "Used Ammo")}}
{{set("existsAmmo", cc_exists(counter))}}
{{create_cc_nx(counter, 0)}}
{{create_cc_nx(counter2, 0)}}
{{"" if existsAmmo else set_cc(counter, 20)}}
{{set("used", max(0, get_cc(counter2)))}}
{{set("collected", floor(used / 2))}}
{{set("ammoRoll", vroll(str(get_cc(counter)) + " + " + str(collected)))}}
{{set("valid", used != 0)}}
{{mod_cc(counter, collected)}}
{{set_cc(counter2, 0)}}
-title "<name> {{"collects" if valid else "attempted to collect"}} their ammunition!"
-desc "{{"At the end of the battle, you can recover half your expended ammunition by taking a minute to search the battlefield." if valid else "You do not have any expended ammunition to recover."}}"
{{"-f \"" + counter2 + " | " + str(used) + "\"" if valid else ""}}
{{"-f \"" + counter + " | " + str(ammoRoll) + "\"" if valid else ""}}
{{"-footer \"" + pgSubject + " | " + pgNum + "\"" if str(showpage) else ""}}
{{"-thumb {}".format(image) if str(embedimage) == "true" else ""}}
-color <color>
```

### Personalization Options

**``!alias $alias_name$ embed...``** - Changes the name to run the command. Replace ``collect`` in the command in the **Code** section.

**``!csettings color $hex$``** - Colors all embeds this color. Replace ``$hex$`` with a hex code. Do not include the hashtag (#).

**``!cvar embedimage true / false``** - Enables / disables whether a character's image is automatically embedded.

**``!cvar showpage true / false``** - Enables / disables whether subjects and page numbers are displayed.

**``!snippet $snippet_name$ ...``** - Changes the name to run the command. Replace ``ammo`` in the command in the **Code** section.
