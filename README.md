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

4) 20260623; https://masarapmabuhay.itch.io/game-off-2025-post-test3

**Key Lesson Learned:** 

Enemy monsters can now face directly downward or upward when walking, attacking or waiting idly. I had to update the code to clearly identify when the monster should do this instead of facing diagonally. I also had to update the animation frames, because whenever we rotate a monster in eight directions, its head appeared smaller when facing directly upward or downward.

Moreover, enemy monsters now have a new animation frame when the hero deals them damage.

**Unlocked Possibilities:**

We now have more animation frames that can be used as "bones" for various "skins." These can, of course, be further updated.

5) 20260624; work-in-progress

**Key Lesson Learned:** 

Creating variables inside a function that is reused in a loop appears to produce the wrong output. 

More specifically, in the function `executeWraithMonsterWalkingAnimation(...)`, I put the variables inside an array that each monster has and which can be identified using an ID. 

Previously:

`var bIsMonsterFacingUpOrDown=false;`<br/>
`var bIsMonsterFacingLeftOrRight=false;`<br/>
`var bIsMonsterFacingUp=false;`<br/>
`var bIsMonsterFacingLeft=false;`<br/>

Now:

`inputArrayWraithMonsterWithIdCount[MONSTER_IS_FACING_UP_OR_DOWN]=false;`<br/>
`inputArrayWraithMonsterWithIdCount[MONSTER_IS_FACING_UP]=false;`<br/>
`inputArrayWraithMonsterWithIdCount[MONSTER_IS_FACING_LEFT_OR_RIGHT]=false;`<br/>
`inputArrayWraithMonsterWithIdCount[MONSTER_IS_FACING_LEFT]=false;`<br/>
			
**Unlocked Possibilities:**

We can now add more animation effects when the hero hits the monster multiple times.

6) 20260625; https://masarapmabuhay.itch.io/game-off-2025-post-test4

**Key Lesson Learned:** 

I've added a combo count that automatically resets back to zero internally after 5 cycles without a successful melee attack. Whenever the hero is able to make a string of at least 3 hits to a monster facing directly toward him from his left or his right, it is pushed back and flies outward.

At the moment, the code isn't yet orderly such that the ON and OFF switches using a combination of `if` statements and variables aren't yet in one place, making it time-consuming to identify which to turn on and which to turn off in order to produce the correct output. 

I'll also still need to check that the computer correctly counts the damages that the hero deals to the monsters.

Meanwhile, I've removed the "START" button that momentarily appears when the app is loaded on a browser.

**Unlocked Possibilities:**

More animation frames can be added based on the combo count.

7) 20260626; https://masarapmabuhay.itch.io/game-off-2025-post-test5

**Key Lesson Learned:** 

I've updated the code to be more orderly, removing excess comments and other clutter. Because of this, the computer can now correctly count the damages that the hero deals to each monster.

However, since the combo count quickly resets to zero internally, I'll need to use another counter to identify the corresponding death animation to be used based on the combo count. I had thought about dealing damage such as `-3000` or `-2000` to identify the combo, but this would mess up the computer's correctly computed damage.

**Unlocked Possibilities:**

More death-related animation frames can be added based on the combo count that will be stored in another variable. The higher this count, the stronger-looking it should be.

# Additional Bug Fixes

3) 20260619;<br/> 
+updated: shaking to move the screen to the left and the right alternately; instead of only to the right so the margin now appears not only on the left, but also on the right;

6) 20260624;<br/> 
+fixed: portion of the code that makes monster chase the hero in `executeWraithMonsterWalkingAnimation`; appears to have been inadvertently deleted

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
