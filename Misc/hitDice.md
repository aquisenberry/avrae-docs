# Hit Dice
*By @Toothless#7854*

Displays text and page number for Hit Dice. Subtracts from Hit Dice counter and rolls hit dice, then adds result rolled to current hit points. Returns error if attempting to spend more hit dice than remaining.

### Prerequisites

A DiceCloud feature called "Hit Dice (``$die$``)", replacing ``$die$`` with the size of your Hit Die. Give it ``$name$Level`` uses, replacing ``$name$`` with the name of the class your Hit Die is from. Do not include ``short rest`` or ``long rest`` in your feature, as you only regain half your Hit Dice on a long rest.

*Example Name:* ``Hit Dice (d10)``  
*Uses:* ``FighterLevel``

Alternatively, run the following code, replacing ``$die$`` with the size of your Hit Die. 

```GN
!cc create "Hit Dice ($die$)" -min 0 -max level -type default
```

If you are multiclassing, run the following code instead, replacing ``$die$`` with the size of your Hit Die, and replacing ``$lvl$`` with the level of the class your Hit Die is from. **IMPORTANT:** Whenever you gain a level in this class, run this command again.

```GN
!cc create "Hit Dice ($die$)" -min 0 -max $lvl$ -type default
```

To regain hit dice, you can increment your counter using ``!cc Hit Dice ($die$) $num$``, replacing ``$die$`` with the size of your Hit Die, and replacing ``$num$`` with the number of Hit Dice you are regaining.

*Example:* ``!cc Hit Dice (d10) 2``

Alternatively, you can run the following alias. Usage is ``!hdr $die$ $num$``, replacing ``$die$`` with a die size (such as ``d10``), and ``$num$`` with a number, such as ``3``. An example of this is ``!hdr d10 3``.

```GN
!alias hdr embed 
{{mod_cc("Hit Dice (%1%)", %2%)}} 
-title "<name> regains spent Hit Dice!" 
-desc "At the end of a long rest, you regain spent Hit Dice, up to a number of dice equal to half your total number of them." 
-f "Hit Dice (%1%)|{{get_cc("Hit Dice (%1%)")}} / {{get_cc_max("Hit Dice (%1%)")}}" 
-footer "Adventuring | PHB 186" 
-color <color>
```

### Usage

``!hd <die> <num>``

``<die>`` - Die size (ex. ``d10``)  
``<num>`` - Number of hit dice you are expending (ex. ``2``)

*Example:* ``!hd d10 2``


### Code

```GN
!alias hd embed 
{{mod_cc("Hit Dice (%1%)", -%2%, True)}} 
{{set("heal", vroll("%2%%1%+"+str(constitutionMod*%2%)))}} 
{{set_hp(min(hp, heal.total + currentHp))}} 
-title "<name> takes a Short Rest!" 
-desc "A character can spend one or more Hit Dice at the end of a short rest, up to the character's maximum number of Hit Dice, which is equal to the character's level. 

For each Hit Die spent in this way, the player rolls the die and adds the character's Constitution modifier to it. The character regains hit points equal to the total." 
-f "Healing Recieved|{{heal}}" 
-f "Hit Points|{{get_hp()}} / {{hp}}" 
-f "Hit Dice (%1%)|{{get_cc("Hit Dice (%1%)")}} / {{get_cc_max("Hit Dice (%1%)")}}" 
-footer "Adventuring | PHB 186" 
-color <color>
```
