# GitHub x ITCH.IO 

This is a code-level post-test analysis of [Game Off 2025: Blue Sapphire Galaxy: Outer Waves](https://masarapmabuhay.itch.io/outer-waves), a work of fiction created for Game Off 2025 with the theme WAVES, in preparation for Game Off 2026.

### ITCH.IO: PROTOTYPES

1) 20260616; https://masarapmabuhay.itch.io/game-off-2025-post-test0

**Key Lesson Learned:** 

When the object is set to `hidden` visibility, attempting to access elements inside it results to unexpected behavior. Use `checkVisibility()` to verify. The function returns `true` if the object is currently `visible` (not `hidden`).

**Unlocked Possibilities:**

It's now possible to hit multiple enemies with the melee attack, although they have to be in the exact same position, or have unnoticeable difference in position.

Meanwhile, the "F" fireball can now hit multiple enemies in its path after commenting out `resetFireballProjectile()`. The technique could be used to create a wider area of enemies that can be hit using melee attacks. 

Note that the image object for the fireball exploding animation must also be increased to more than `1` and put inside an `array` image pool.

2) 20260618; https://masarapmabuhay.itch.io/game-off-2025-post-test1

**Key Lesson Learned:** 

When an object like an enemy is to be reused again and put in a different `x` and `y` positions, setting both these positions to `-1000`, which is not viewable on the canvas, prevents the object from appearing in its previous position when its `visibility` is again set to `visible`.

Note that this should be done before setting the object's `visibility` to `hidden`.

**Unlocked Possibilities:**

It's now possible to reuse the same object multiple times and put in different positions.

3) 20260619; https://masarapmabuhay.itch.io/game-off-2025-post-test2

**Key Lesson Learned:** 

I've opted to update the collision detection hit box from `iImageFrameHeightLarge/2` and `iImageFrameWidthLarge/2` to `iImageFrameHeightLarge` and `iImageFrameWidthLarge`. 

This adds more leeway when targeting a monster to launch an attack, such that the hero attacks instead of walking pass the monster if the target based on the mouse's position when it's clicked isn't too far from the enemy.

In the same way, monsters would attack the hero if he's in the same field of view and doesn't attack first. Previously, monsters would at times only end up walking and not attacking at all. 

Still, at certain angles, such as diagonal, it may appear that the hero's weapon is still too far to supposedly hit the enemy. This, however, could be fixed by adding more animation effects. 

**Unlocked Possibilities:**

The game's now a lot easier, because the hero is also a lot more powerful.

# Additional Bug Fixes

3) 20260619;<br/> 
+updated: shaking to move the screen to the left and the right alternately; instead of only to the right so the margin now appears not only on the left, but also on the right;

## Select Software Development Productivity Tools

1) MS Paint

2) https://www.gimp.org/

3) https://www.gbstudio.dev/

4) https://www.audacityteam.org/

## Related link

1) https://philnits.org/

## Open Source Software License

Copyright 2026 USBONG

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0
  
Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.

@company: USBONG<br/>
@author: SYSON, MICHAEL B., et al.<br/>
@website address: http://www.usbong.ph<br/>
