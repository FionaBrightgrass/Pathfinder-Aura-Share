![image](https://i.imgur.com/K82oBFy.png)


----------------This is for: Pathfinder 1E-------------------------------
Pathfinder Aura Share: Automates the sharing of buffs between tokens. This makes handling auras easier. The conditions for automating the auras are listed in the notes below. (It's pretty simple)

-----If you enjoy this mod-----
------Feel free to tip!--------
https://ko-fi.com/cactuarcrunch


Manifest URL: https://github.com/FionaBrightgrass/Aura-Share/raw/main/module.json


--------Cliff Notes--------
_create the following:
-Item Type: Buff
-Dictionary Flag: "radius" & value > 0
....the buff  now auto shares
_optional:
-Boolean Flag: "shareInactive"    __share the buff even if it is toggled off. Great for buffs that only impact allies.
-Boolean Flag: "shareEnemies"     __share the aura with enemies (instead of allies). Typically combined with shareInactive.
-Boolean Flag: "shareNeutral"     __share the aura with targets with neutral disposition.

![image](https://i.imgur.com/zRj6ITb.png)


----------------------Steps----------------------
Add a buff to a PF1E actor. Name it whatever you'd like.

Give the buff/aura a Dictionary Flag of "radius" with a value greater than 0.

It will auto copy to other tokens except with:
The new buff name becomes: Aura Name (Source Actor's Name)
"radius" is set to 0 on the recipient 

optional: Give the aura a Boolean Flag of shareInactive to allow sharing of disabled auras. 
optional: Give the aura a Boolean Flag of shareEnemies to target enemies instead of allies. Combine this with shareInactive for enemies only. 



----------Conditions for Applying Auras-------------------
_Adds the buff to allies if:
-The source actor has a buff with a radius > 0.
-The buff is enabled, OR if the source actor's buff has the "shareInactive" Boolean flag.

_Adds the buff to allies when:
-They enter range (either actor can move).
-The buff is toggled on.
-A Token is created in the scene, and allies are in range.
-The aura actor's HP rises above 0.

Adds the buff to enemies if:
-The buff also has a "shareEnemies" Boolean Flag. Note: You typically would combine this with "shareInactive" so that the buff doesn't hurt the source actor.
 
Adds the Buff when:
-A new buff has a radius set to > 0 and the token moves or the buff is toggled. Best to create it on the actor then add to scene.
-The buff is toggled on.
-A token with an aura buff is added to the scene. (radius > 0)
-The actor's HP increases over 0, and the actor was previously dead.
-An actor moves into range of the buff.

Deactives the buff when:
-The source moves out of range.
-The recipient moves out of range.
-The source disables the buff, and the buff does not have the "alliesOnly" Boolean Flag
-The source's HP falls below zero, unless: It has the Diehard feat -OR- Unconscious Auras is toggled OFF in the menus.

Removes the buff when:
-the source is deleted.





---------------Updates------------
(v1.5.0)  Most stuff runs async now. Auras don't "delete" off of sheets, they just toggle inactive now. (performance reasons.)
(v1.3.2)  Actors with an item, buff, etc named "Diehard" will now continue to share their auras when below 0 HP.
(v1.3.1)  Delete Token, Create Token are now working. Deleting a token removes inherited buffs. Tokens hitting negative HP now triggers immediately.
(v1.2.7)  Delete Token hooks have once again been disabled. They were causing a bug with stacking buff icons.
(v1.2.0)  Using the shareEnemies Boolean Flag on an aura will switch it to only impact enemies.* 
          *Combine this with ShareInactive or it will still impact the original token.
(v1.0.10) Code cleanup to improve readability and speed up processing of auras.




--------Potential Changes in Future Updates---------
-To Fix: Renaming an aura will not remove the old buff from a token. Rename auras on the character sheet before the token is placed on the scene.