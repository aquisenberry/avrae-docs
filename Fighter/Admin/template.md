# Alias Name
*By Toothless#7854*

<p align="center">
  <img src="https://i.imgur.com/80PZHL9.png"/>
</p>

A description of what the alias/snippet does.

### Usage

``!name``

### Setup
Run the command in the **Code** section. It will automatically setup counters and cvars.

### Code
```GN
!alias name embed
{{set_cvar_nx("embedimage", "true")}}
{{set_cvar("embedimage", "false") if str(embedimage) != "true" else ""}}
{{set_cvar_nx("showpage", "true")}}
{{set_cvar("showpage", "false") if str(showpage) != "true" else ""}}
{{set("pgSubject", "Subject")}}
{{set("pgNum", "PHB #")}}
{{set("counter", "Name")}}
-title "<name> uses {{counter}}!"
-desc "This is a test alias to demonstrate the format of documentation."
{{"-footer \"" + pgSubject + " | " + pgNum + "\"" if str(showpage) == "true" else ""}}
{{"-thumb <image>" if str(embedimage) == "true" else ""}}
-color <color>
```

### Personalization Options

**``!alias $alias_name$ embed...``** - Changes the name to run the command. Replace ``name`` in the command in the **Code** section.

**``!csettings color $hex$``** - Colors all embeds this color. Replace ``$hex$`` with a hex code. Do not include the hashtag (#).

**``!cvar embedimage true / false``** - Enables / disables whether a character's image is automatically embedded.

**``!cvar showpage true / false``** - Enables / disables whether subjects and page numbers are displayed.
