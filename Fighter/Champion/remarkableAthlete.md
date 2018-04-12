# Remarkable Athlete
*By Toothless#7854.*

<p align="center">
  <img src="https://i.imgur.com/A4oqCM9.png"/>
</p>

Displays Strength score, Strength modifier, and running long jump distance.

### Usage

``!remarkable``

### Setup
Run the command in the **Code** section. It will automatically setup cvars.

### Code
```GN
!alias remarkable embed
{{set_cvar_nx("embedimage", "true")}}
{{set_cvar("embedimage", "false") if str(embedimage) != "true" else ""}}
{{set_cvar_nx("showpage", "true")}}
{{set_cvar("showpage", "false") if str(showpage) != "true" else ""}}
{{set("pgSubject", "Fighter")}}
{{set("pgNum", "PHB 72")}}
{{set("counter", "Remarkable Athlete")}}
-title "<name> uses {{counter}}!" 
-desc "When you make a running long jump, the distance you can cover increases by a number of feet equal to your Strength modifier." 
-f "Strength Score | {{strength}}"
-f "Strength Modifier | {{strengthMod}}"
-f "Running Long Jump | {{strength + strengthMod}} ft."
{{"-footer \"" + pgSubject + " | " + pgNum + "\"" if str(showpage) == "true" else ""}}
{{"-thumb <image>" if str(embedimage) == "true" else ""}}
-color <color>
```

### Personalization Options

**``!alias $alias_name$ embed...``** - Changes the name to run the command. Replace ``remarkable`` in the command in the **Code** section.

**``!csettings color $hex$``** - Colors all embeds this color. Replace ``$hex$`` with a hex code. Do not include the hashtag (#).

**``!cvar embedimage true / false``** - Enables / disables whether a character's image is automatically embedded.

**``!cvar showpage true / false``** - Enables / disables whether subjects and page numbers are displayed.
