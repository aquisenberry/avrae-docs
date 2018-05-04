# Eldritch Strike
*By Toothless#7854.*

<p align="center">
  <img src="https://i.imgur.com/lbPAs2g.png"/>
</p>

Displays text for Eldritch Strike on attack.

### Usage

``![attack|a] [atk_name=list] eldritch``

### Setup
Run the command in the **Code** section. It will automatically setup cvars.

### Code
```GN
!snippet eldritch
{{set_cvar_nx("showpage", "true")}}
{{set_cvar("showpage", "false") if str(showpage) != "true" else ""}}
{{set("pgNum", "PHB 75")}}
-phrase "**Eldritch Strike.** When you hit a creature with a weapon attack, that creature has disadvantage on the next saving throw it makes against a spell you cast before the end of your next turn. {{"(" + pgNum + ")" if str(showpage) == "true" else ""}}"
```

### Personalization Options

**``!snippet $snippet_name$ ...``** - Changes the name to run the command. Replace ``eldritch`` in the command in the **Code** section.

**``!csettings color $hex$``** - Colors all embeds this color. Replace ``$hex$`` with a hex code. Do not include the hashtag (#).

**``!cvar showpage true / false``** - Enables / disables whether subjects and page numbers are displayed.
