# Improved War Magic
*By Toothless#7854.*

<p align="center">
  <img src="https://i.imgur.com/ZDfbAh6.png"/>
</p>

Displays text for Improved War Magic on attack.

### Usage

``![attack|a] [atk_name=list] improved``

### Setup
Run the command in the **Code** section. It will automatically setup cvars.

### Code
```GN
!snippet improved
{{set_cvar_nx("showpage", "true")}}
{{set_cvar("showpage", "false") if str(showpage) != "true" else ""}}
{{set("pgNum", "PHB 75")}}
-phrase "**Improved War Magic.** Starting at 18th level, when you use your action to cast a spell, you can make one weapon attack as a bonus action. {{"(" + pgNum + ")" if str(showpage) == "true" else ""}}"
```

### Personalization Options

**``!snippet $snippet_name$ ...``** - Changes the name to run the command. Replace ``improved`` in the command in the **Code** section.

**``!csettings color $hex$``** - Colors all embeds this color. Replace ``$hex$`` with a hex code. Do not include the hashtag (#).

**``!cvar showpage true / false``** - Enables / disables whether subjects and page numbers are displayed.
