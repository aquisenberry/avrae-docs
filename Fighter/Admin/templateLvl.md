# Alias Name (Lvl)
*By Toothless#7854*

<p align="center">
  <img src="https://i.imgur.com/WXZh8HG.png"/>
</p>

A description of what the alias/snippet does. This alias/snippet uses the cvar ``FighterLevel``.

### Usage

``!nameLvl``

### Setup
Run the command in the **Code** section. It will automatically setup counters and cvars.

### Code
```GN
!alias nameLvl embed
{{set_cvar_nx("embedimage", "true")}}
{{set_cvar("embedimage", "false") if str(embedimage) != "true" else ""}}
{{set_cvar_nx("showpage", "true")}}
{{set_cvar("showpage", "false") if str(showpage) != "true" else ""}}
{{set("pgSubject", "Subject")}}
{{set("pgNum", "PHB #")}}
{{set("counter", "Name (Lvl)")}}
{{set("lvl", FighterLevel if exists("FighterLevel") else level)}}
-title "<name> uses {{counter}}!"
-desc "This is a test alias to demonstrate the format of documentation. Your FighterLevel is {{lvl}}."
{{"-footer \"" + pgSubject + " | " + pgNum + "\"" if str(showpage) == "true" else ""}}
{{"-thumb <image>" if str(embedimage) == "true" else ""}}
-color <color>
```

### Personalization Options

**``!alias $alias_name$ embed...``** - Changes the name to run the command. Replace ``nameLvl`` in the command in the **Code** section.

**``!csettings color $hex$``** - Colors all embeds this color. Replace ``$hex$`` with a hex code. Do not include the hashtag (#).

**``!cvar embedimage true / false``** - Enables / disables whether a character's image is automatically embedded.

**``!cvar showpage true / false``** - Enables / disables whether subjects and page numbers are displayed.

### Multiclassing

If you are multiclassing and you are not using a DiceCloud sheet, run the following command, replacing ``$lvl$`` with your current fighter level.

```GN
!cvar FighterLevel $lvl$
```

**You must run this command every time you gain a fighter level.** If you do not do this, the alias will use your total level instead of your Fighter level. This may cause problems in your aliases.
