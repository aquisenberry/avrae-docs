# Feats

Not all of the feats found in the PHB, XGtE, EEPC, and UA releases are presented here, as many consist of having advantage in certain particular situations, or offering some passive effect. Instead, we have created aliases for some of the feats that have *active*, *noticable* effects.
* [Defensive Duelist](#defensive-duelist)
* [Durable](#durable)
* [Elemental Adept](#elemental-adept)
* [Great Weapon Master](#great-weapon-master)
* [Healer](#healer)
* [Heavy Armor Master](#heavy-armor-master)
* [Inspiring Leader](#inspiring-leader)

## Defensive Duelist
*By silverbass#2407*

**Alias:**     
```GN
!alias defend multiline
!embed -title "<name> uses the Defensive Duelist Feat!" -desc "When you are wielding a finesse weapon with which you are proficient and another creature hits you with a melee attack, you can use your reaction to add your proficiency bonus to your AC for that attack, potentially causing the attack to miss you." -f "New AC|<armor> + <proficiencyBonus> = {{proficiencyBonus + armor}}" -thumb <image>
!i hp "<name>" mod %1%
```
**Use With:**  
``!defend [damage-from-triggering-attack]`` While in combat (``!init begin``), ONLY IF the To-Hit was less than your AC + Proficiency.

## Durable
*By silverbass#2407*

**Alias:**  
```GN
!alias durable embed {{set("oldDice", "%1%")}} {{set("oldTotal", "%2%")}} -title "<name>'s makes use of their durability!" -desc "When you roll a Hit Die to regain hit points, the minimum number of hit points you regain from the roll equals twice your Constitution modifier (minimum of 2)." -f "Old Healing|{{oldDice+str(hd)}} = ``{{oldTotal}}``" -f "New Healing|{{str(constitutionMod*2*%1%)}}" -f "Current HP: | {{min(hp, (constitutionMod*2*%1% - int(oldTotal) + currentHp))}}/{{hp}}{{set_hp(min(hp, (constitutionMod*2*%1% - int(oldTotal)) + currentHp))}}" -color <color> -thumb <image>
```
**Use With:**  
``!durable [#dice-under-2xComMod] [#sum-of-dice-under-2xConMod]`` After taking a short rest (using ``!shortrest``)

## Elemental Adept
*By silverbass#2407*

**Alias:**  
```GN
!alias adept embed -title "Elemental Adept <name> Focuses their Spell!" -desc "Spells you cast ignore resistance to damage of the chosen type. In addition, when you roll damage for a spell you cast that deals damage of that type, you can treat any 1 on a damage die as a 2." -f "Additional Damage|{{%1%}}" -color <color> -thumb <image>
```
**Use With:**  
``!adept [#-ones-rolled]``

## Great Weapon Master
**Snippet:**  
``!snippet gwm -b -5 -d 10``  
**Use With:**  
``![init attack] [target] [weapon] gwm``

## Healer
*By silverbass#2407*

**Custom Counters Required:**  
``!cc create "Healer's Kit" -min 0 -max 10``  
**Alias:**  
```GN
!alias heal multiline
!embed {{mod_cc("Healer's Kit", -1, True)}} -title "<name> Uses a Healer's Kit to Tend {{"%1%".strip("\"'")}}!" -desc "As an action, you can spend one use of a healer's kit to tend to a creature and restore 1d6+4 hit points to it, plus additional hit points equal to the creature's maximum number of Hit Dice. The creature can't regain hit points from this feat again until it finishes a short or long rest." -f "Healing|{{str(vroll("1d6 + 4 + %2%"))}}" -color <color> -thumb <image>
!cc "Healer's Kit" 0
```
**Use With:**  
``!heal [target] [target-max-#-hit-dice]``

## Heavy Armor Master
*By silverbass#2407*

**Alias:**  
```GN
!alias ham multiline
!embed -title "<name> Deflects the Some of the Strike!" -desc "While you are wearing heavy armor, bludgeoning, piercing, and slashing damage that you take from nonmagical weapons is reduced by 3." -color <color> -thumb <image>
!i hp "<name>" mod 3
```
**Use With:**  
``!ham`` While in combat (``!init begin``), after being hit with bludgeoning, piercing, and slashing damage from nonmagical weapons.

## Inspiring Leader
*Toothless#7854 had something for this.*

