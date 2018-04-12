# Relentless
*By Toothless#7854.*

<p align="center">
  <img src="https://i.imgur.com/0jsOfYs.png"/>
</p>

Rolls initiative. Adds 1 to "Superiority Dice" counter if "Superiority Dice" counter equals 0.

### Usage

``!relentless``

### Setup
Run the command in the **Code** section. It will automatically setup counters and cvars.

### Code
```GN
!alias relentless c init
{{set_cvar_nx("embedimage", "true")}}
{{set_cvar("embedimage", "false") if str(embedimage) != "true" else ""}}
{{set_cvar_nx("showpage", "true")}}
{{set_cvar("showpage", "false") if str(showpage) != "true" else ""}}
{{set("pgSubject", "Fighter")}}
{{set("pgNum", "PHB 74")}}
{{set("counter", "Superiority Dice")}}
{{set("valid", 1 if get_cc(counter) == 0 else 0)}}
{{mod_cc(counter, 1) if valid else ""}} 
-phrase "**Relentless.** {{"When you roll initiative and have no superiority dice remaining, you regain one superiority die." if valid else "You must have no superiority dice remaining to regain one superiority die."}} [{{get_cc(counter)}} / {{get_cc_max(counter)}}]{{" (" + pgNum + ")" if str(showpage) == "true" else ""}}"  
```

### Personalization Options

**``!alias $alias_name$ embed...``** - Changes the name to run the command. Replace ``relentless`` in the command in the **Code** section.

**``!csettings color $hex$``** - Colors all embeds this color. Replace ``$hex$`` with a hex code. Do not include the hashtag (#).

**``!cvar embedimage true / false``** - Enables / disables whether a character's image is automatically embedded.

**``!cvar showpage true / false``** - Enables / disables whether subjects and page numbers are displayed.
