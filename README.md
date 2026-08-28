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

8) 20260627; work-in-progress

**Key Lesson Learned:** 

This version removes some of the animation frames like lying down to create a much more solid (not buggy-looking) experience.

9) 20260629; https://masarapmabuhay.itch.io/game-off-2025-post-test6

**Key Lesson Learned:** 

This version retains the combo count and the hit animation, while commenting out the rest. The code is also less cluttered in that I've put the conditions together in the same `if-else` statement, instead of just inserting them anywhere.

**Unlocked Possibilities:**

An easier-to-debug reusable artifact. 

10) 20260702; https://masarapmabuhay.itch.io/game-off-2025-post-test7

**Key Lesson Learned:** 

I've updated the animation frames which include walking diagonally and directly upward or downward. I've also added new boxing animation frames and sound. At the code level, the monster's AI still doesn't proactively align horizontally to the hero. In other words, their positions in the  `y-axis` aren't equal or very close to each other. For the time being, the monster may still look above (behind) or below (in front) of the hero just like the animation frames with the sword. The punching animation required an update in the code, such that the frames don't skip or change too quickly. As for the sound, I've set it to play once the last frame of the punching animation finishes.

**Unlocked Possibilities:**

More animation frames could be created using existing frames that are further edited. Examples of these include monsters with weapons like bow and arrow, knife, spear, etc.

11) 20260703; https://masarapmabuhay.itch.io/game-off-2025-post-test8

**Key Lesson Learned:** 

I've opted to create new boxer-related animation frames including when facing diagonally and directly upward or downward, instead of the monsters always facing left or right without diagonals. I've also updated the code to use these animation frames just like with the sword-weilding monster.

**Unlocked Possibilities:**

Drawing pixel art at 64x64px isn't too difficult, although it took me about two and a half hours to update the sprite sheet. Larger dimensions such as 128x128 would allow for more shadings and details in the image frames.

12) 20260704 and 20260705; https://masarapmabuhay.itch.io/game-off-2025-post-test9

**Key Lesson Learned:** 

I've updated the boxer monster's animation frames to reduce any noticeable pecularities when the hero moves around it so that it rotates, facing each of the eight directions. More specifically, I've made the body wider by at least 2 pixels when the monster's facing directly upward or downward.

**Unlocked Possibilities:**

While the oddities in the animation frames aren't too noticeable when the action is fast-paced, they do become apparent when the frames are reused and further modified.

13) 20260711; https://masarapmabuhay.itch.io/game-off-2025-post-test10

**Key Lesson Learned:** 

I'm currently updating the code to be able to fire the same projectile multiple times using the "F" key and mouse click. Right now, I reuse the one and only fireball available, such that if the hero casts it even though it hasn't gone past the screen's `width` and `height` dimensions yet, its `x` and `y` positions are immediately updated to where the hero is located. As a result, the hero could create a stream of fireballs that reach a distance farther than a melee attack. Also, I've taken out the stamina component that limits the amount of times the hero could cast this spell. Nonetheless, multiple fireballs available for use and stored in an array pool when not in use is ideal, only writing this code is prone to human error including spelling and syntax errors, meaning that it must be done in small steps, verifying if the app could run every time the programmer writes a new set of code; otherwise, in the likely event that the app won't run at all, it would be extremely difficult to find the cause of the error, especially since I'm using `Javascript`.

**Unlocked Possibilities:**

We can now make use of more projectiles that reach a distance farther than a melee attack.

14) 20260714; work-in-progress

**Key Lesson Learned:** 

I've again updated the animation frames, especially with regard to walking directly up and down as well as their idle equivalents. I've set the animation delay (`inputArrayWraithMonsterWithIdCount[MONSTER_ANIMATION_DELAY_COUNT_MAX]`) for walking directly up and down to be longer at `8` instead of `5`; otherwise, the movement would not look as fluid. 

Also, I realized that if there would be more of these customized delays, then a spreadsheet with the corresponding values would be necessary. While using the [2D Animation Tool](https://github.com/usbong/2danimationTool) that I developed back in 2023 proved helpful, actually seeing the animation frames changing as the monster faced a particular direction even while it moves according to its `x` and `y` coordinate positions is still crucial. I note that the animation frames for walking directly left or right don't appear logical even when I was developing the app back in Game Off 2025; however, speeding up the animation by reducing the delay per animation frame creates a somewhat acceptable walking sequence.

**Unlocked Possibilities:**

With more `bones` as guide, it would be faster to create the animation sequences from hereon.

15) 20260716; work-in-progress

**Key Lesson Learned:** 

I've further updated the animation frames. I noticed that the diagonal movement toward the top-right was off by a few pixels, such that the movement toward the top-left was markedly more fluid-looking and not jerking. Moreover, I had to rearrange the four frames, so that the frame count in the sequence for when the monster opens and closes his feet isn't the same when moving toward the top-right and the top-left directions. 

**Unlocked Possibilities:**

While having these animation sequences readily at hand makes development faster, it's still easy to commit human errors when positioning the image inside the frame as well as when assigning its order in the sequence. Even being off by only `1` pixel results in a jerking animation sequence that is most apparent when the dimensions are small such as when the image frame is only `64x64px` big.

16) 20260717; work-in-progress

**Key Lesson Learned:** 

I updated the lumbar area of the monster's back for the animation frames moving diagonally toward the top-right and the top-left. It's now less jiggly than before. Meanwhile, the upper body still moves partially sideways as it should. I've also updated the monster's arms when moving directly upward to show a more pendulum-like swing, using [AnatomyLab's 3D Animation Walk Cycle](https://www.youtube.com/shorts/NS-GBLpBxLg) as additional reference, and made the feet swing backward higher. Finally, the animation frames for walking directly left and right still appear acceptable as they are.

**Unlocked Possibilities:**

While there are still many more animation and images frames to do including those for the effects and font styles, I think that what I have right now are definitely better than what I had made during Game Off 2025. I also note that the animations appear less cartoony at the moment. 

17) 20260718; work-in-progress

**Key Lesson Learned:** 

I've again updated the lumbar area of the monster's back for the animation frames moving diagonally toward the top-right and the top-left to be less awkward-looking than before. Further, while the upper body appears to have more joints and thus produces less stiffness in the movement, one of the legs doesn't seem to have more than one joint that could rotate, making their movement less natural-looking. Nonetheless, the effect might still be acceptable at the moment.

I've also updated the animation frames for moving directly downward, while facing toward the screen. The animation frames for the leg had a delay caused by frame #1, wherein both legs and feet are together. Moreover, I've made the leg swing a little more like when the monster moves directly upward.

**Unlocked Possibilities:**

We now have better animation sequences that would save us more time during development if they are reused regularly.

18) 20260719; work-in-progress

**Key Lesson Learned:** 

Adding knee joints creates a more natural-looking animation sequence, markedly different from the marching animations of the prior versions. Right now, the animation frames for moving toward the top-left and the top-right as well as the ones for the bottom-left and the bottom-right now have additional knee joints. I note that when the animations aren't scaled bigger, they may at times look awkward, as though the monster has a stump or a bent leg.

**Unlocked Possibilities:**

We can now show the monster's back while walking a lot more confidently than before thanks to the improvements. Of course, I'll likewise need to update the ones for moving toward the screen, as a result of this good outcome.

19) 20260720; work-in-progress

**Key Lesson Learned:** 

Adding knee joints creates a more natural-looking animation sequence, markedly different from the marching animations of the prior versions. Right now, the animation frames for moving toward the top-left and the top-right as well as the ones for the bottom-left and the bottom-right now have additional knee joints. I note that when the animations aren't scaled bigger, they may at times look awkward, as though the monster has a stump or a bent leg.

**Unlocked Possibilities:**

We can now show the monster's back while walking a lot more confidently than before thanks to the improvements. Of course, I'll likewise need to update the ones for moving toward the screen, as a result of this good outcome.

20) 20260722; https://masarapmabuhay.itch.io/game-off-2025-post-test11

**Key Lesson Learned:** 

I've updated the code to auto-identify which punching animation frames should be used for the hero by adding a small offset in the `y-axis` when determining whether to face directly to the left/right or face diagonally downward. Previously, the hero could punch facing directly to the left, even though the monster is still a few pixels below him, such that a diagonal punching animation would have been more apt.

Meanwhile, I've also updated the animation frames to look less robotic, although I haven't yet added any idle animations.

**Unlocked Possibilities:**

We now have a more forgiving `collision detection` system that uses offsets to coincide with what we can expect to see on screen. Previously, I had opted to allow for a more lenient use of `hit boxes` at the expense of a slight discrepancy in what is actually visible on screen, that is, the player at times may still appear a little bit far to hit the monster despite being able to deal damage. This, however, can be solved by adding more animation effects.

21) 20260723; https://masarapmabuhay.itch.io/game-off-2025-post-test12

**Key Lesson Learned:** 

I've removed one pixel near the knees to create a sense of movement even when the characters are `idle`. Otherwise, when all the characters are only standing still, the scene appears to lack movement. I've also lowered the left arm when the characters are facing directly downward to make them look less flat or without depth. 

At the code level, this means that when the character's state is `idle`, the animation count is cycled between `0` and `1` using the `%` or modulo operator to be able to swap between the two frames.

**Unlocked Possibilities:**

There's now more movement among the characters even when they're only standing.

22) 20260727; https://masarapmabuhay.itch.io/game-off-2025-post-test13

**Key Lesson Learned:** 

I've added a total of `16` coins that the hero could collect. Actually, there are `17` because one is used as a display icon to indicate how many the hero has collected so far. Moreover, this item could be replaced with a fruit or some other object. At the code level, I opted not to create a `double array` to reduce the amount of code that I'd have to write and check for human errors, thereby speeding up the development. Still, if this item would behave in a more complex way just like with the monsters that attack the hero, then it would be necessary to create a `double array` for this as well. 

I've also updated the code to determine where the hero will be facing based on the `iDeltaX`, which is the `x` position of the point where the user clicked the mouse. Previously, without the `offset`, even a few pixels to the left of the hero's center in the `x` axis resulted to the hero facing to the right. 

**Unlocked Possibilities:**

We can make the items appear every time the hero hits or eliminates a monster. The monsters in this case could be thought of as boxes that could be destroyed just like with the boxes in [Crash Bandicoot](https://www.youtube.com/watch?v=pSHj5UKSylk), which the developers had put in order to fill up the vacant space, provide a choice to players who're willing to take on a challenge to be able to get a reward in exchange for the risk, among other things. 

23) 20260728; https://masarapmabuhay.itch.io/game-off-2025-post-test14

**Key Lesson Learned:** 

I've added the coins in the array of items checked in `updateArrayActorsZIndex()`, so that they will be automatically drawn above or behind the hero and the monsters, the latter in this case don't pick them up. I also note that I added an extra `32px` in the height in [coin.png](https://github.com/usbong/game-off-2025post-test/blob/main/html_application/assets/images/coin.png), because the aforementioned function uses the object's height to determine which should be above which. Further, the extra space is transparent.

Next, I updated the hero's sprite sheet to use the arms in the `idle` state when walking diagonally. Meanwhile, I've kept the arms swinging when the hero moves directly toward the left, right, top and bottom. I note that even a pixel's difference can cause unintended jerking.

24) 20260729; https://masarapmabuhay.itch.io/game-off-2025-post-test15

**Key Lesson Learned:** 

I still haven't been able to get the automated reading of an external `.txt` file to work in Javascript. If the user selected the file himself, then the content of the file could be read. However, this is an additional step that I prefer to avoid. I've also re-verified the use of the `iframe`, whose contents, which are taken from an external `src` file, could be read using HTML, but cannot be obtained using Javascript for security reasons and such.

I've thus gone ahead with making do with putting the contents of this external input file in the main `.html` file instead. Right now, I'm displaying on screen the current `x` and `y` positions of the hero. These will be useful in computing for the `viewport` to identify which monsters, items and other objects should be shown on screen based on where the `viewport` is currently located in relation to the entire stage. This means that those that aren't inside the `viewport` don't need to be shown nor updated needlessly. I note that `margins` should be added as well, so that the objects don't simply pop into the `viewport`. 

**Additional Note:**

In Javascript, as well as in Java, the `y` axis is inverted, such that `(0,0)` for `(x,y)` is at the top-left. In most cases, we will use `(0,0)` or the `anchor` to identify the positions of the objects, instead of putting it at the exact center of the object to make the computations easier. Therefore, an object's center would be computed as `(0+myObjectWidth/2,0+myObjectHeight/2)`.

**Unlocked Possibilities:**

By adding the basic foundations of a side-scrolling engine, the stage could be made larger than the default `width` and `height` which are currently set to `640px` by `360px` respectively.

25) 20260730; https://masarapmabuhay.itch.io/game-off-2025-post-test16

**Key Lesson Learned:** 

I've added [background image tiles](https://github.com/usbong/game-off-2025post-test/blob/main/html_application/assets/images/countInverted.png). There are 16 all in all, each having a size of `128x128` pixels (`width`x`height`). I note that the tiles are a lot bigger than the hero and the monsters, which are `64x64` pixels.

**Unlocked Possibilities:**

The other tiles are already outside the `viewport`. We will need to move the `viewport` to be able to see the rest of the tiles. We'll also need to see if there will be lags or other execution errors when we do this. At the moment, the entire [`countInverted.png`](https://github.com/usbong/game-off-2025post-test/blob/main/html_application/assets/images/countInverted.png) tile sheet is only 22.9KB.

26) 20260801 and 20260802; https://masarapmabuhay.itch.io/game-off-2025-post-test17

**Key Lesson Learned:** 

I've added basic horizontal scrolling wherein the monsters, items and the background tiles move accordingly based on the hero's movement in the `x` axis. The portion of the stage that is currently viewable scrolls as soon as the hero's `x` position goes beyond `60%` of the viewport, which is `640x360px` (`widthxheight`). Because of this, I've been able to make the entire stage larger than the viewport by adding two more background tile columns, each having `128px` for a total of `256px`. The entire stage, therefore, is now `896x360px`. 

**Unlocked Possibilities:**

To create an even larger stage, the viewport must be updated, so that the hero's position is at its center. Also, while the viewport only scrolls horizontally to the right at the moment, it is, of course, also possible to make the viewport scroll to the left given the correct equation to compute.

27) 20260801 and 20260802; https://masarapmabuhay.itch.io/game-off-2025-post-test17

**Key Lesson Learned:** 

I've fixed the problem with the hero suddenly moving rapidly when the user mouse-clicks the same point in the coordinate system. However, after leveling up and if the user chooses the `speed-up` option, these sudden bursts of dashing movement would reappear.

Next, when the hero reaches the right-most part of the screen, he is transitioned to the left-most part of the screen again, and all the items as well as the monsters are re-generated. I note here that I've added a fading transition that gradually sets the value of the `opacity` of the tint canvas from `1` to `0`.

**Unlocked Possibilities:**

While the current version only loops, at the code level, I think that the key elements of the game are already present. At this point, I'd want to point out that the size of the hero and the monsters could be further increased given that the hero now moves a lot slower by default to not cause any dizzying effect due to the background also moving. This task would require updating the code and the animation frames, the latter, I expect, would take a substantial amount of time. 

28) 20260803; https://masarapmabuhay.itch.io/game-off-2025-post-test18

**Key Lesson Learned:** 

I've increased the `width` of the entire stage from only `640px` to `1152px`. Also, the viewport which moves based on the hero's movement can now go to the left instead of only to the right. I note here having noticed an `acceleration` occurring at certain times, and having provided a fix, which I've detailed in the section below on `Additional Bug Fixes`.

I initially wanted to get up to as much as `1280px` and more, but encountered difficulty in moving the viewport along with the hero, because the hero has to have an actual position in relation to the entire stage as well as another position that is displayed in relation to the viewport. Therefore, while the hero should ideally be seen to be moving only at the center of the viewport, in reality, he's already moving much further within the entire stage. Moreover, due to my having used multiple variables including `mainImageTileHeroBody`, `mainImageTile` and others, finding which one actually moved the hero's position on screen became a lot more time-consuming.

**Unlocked Possibilities:**

The size of the stage is now larger than the viewport. The hero could go left or right and scroll the viewport accordingly. The size of the stage also reminds me of 2D fighting games from Capcom and SNK back in the 90s to the early 2000s. 

29) 20260804; https://masarapmabuhay.itch.io/game-off-2025-post-test19

**Key Lesson Learned:** 

I found a jerking behavior when the hero moves diagonally toward the top-left or the top-right. I’ve moved the pertinent animation frames by a pixel or two to resolve this issue.

Next, I’ve updated the code, so that when the hero casts a “fireball” by pressing the “F” key and doing a left mouse-click, he could still move around even before the fireball goes out of screen or hits a monster. Moreover, the fireball currently explodes upon hitting a monster, instead of continuously moving forward. Also, it now moves slower at a speed of `6` instead of `10`.

I would certainly want to get the stage’s width to be much larger and resolve any more errors such as in the explosion animation, but I’ll already stop here for now.

**Unlocked Possibilities:**

The entire stage could be made larger vertical-wise, and the items as well as the monsters could be procedurally generated. At present, there aren’t any walls yet though. 

30) 20260805; https://masarapmabuhay.itch.io/game-off-2025-post-test20

**Key Lesson Learned:** 

I've added movement of the viewport on the `y-axis`, such that the total `width` and `height` of the entire stage is now `1152px` x `640px`. Moreover, I've added a delay in the hero's steps, making him appear heavier. This update also led to another set of updates in the hero's existing animation delays to compensate for the said extra delay.

I've also added a stamina cost when casting the fireball, the same cost when doing a melee attack. In addition, the hero has to press and hold the `F` key first in order to cast this fireball.

**Unlocked Possibilities:**

The entire stage is bigger now and while the gameplay is less fast-paced, it's certainly faster than a purely turn-based game.

31) 20260806; https://masarapmabuhay.itch.io/game-off-2025-post-test21

**Key Lesson Learned:** 

This update tests the new set of background tiles that I've made to show an isometric view of the stage. The pattern may look simple, but the pieces do form the outlines of the walls and the doors of the stage. I also note here that the characters appear slightly bigger, and while I know that the `scale` function in Javascript can create a better image quality than the one in Gimp, the computations for the collision detection would get messed up and would need to be recomputed accordingly. This is why I had opted to create a larger sprite image sheet for the "big boss" in Game Off 2025, instead of using Javascript's `scale` function. Still, if the scale would be only small and won't necessarily be double the original size, then Javascript's function would be worth checking out.

Moreover, I've set the hero's starting position to be at the center instead of the top-left corner, even though I still haven't gotten the viewport to move while keeping the hero fixed at the center in this version of the prototype. The purpose of this is to supposedly create an even larger map. Also, because of this update, the viewport's `x` and `y` positions could turn negative. 

I've also made use of the right mouse-click as an alternative to the "F" key and left mouse-click combination to do the fireball. Previously, during Game Off 2025, I had opted to not use the right mouse-click at all, because some people might not be using this button given their setup; however, I find the right mouse-click and the scroll wheel on the mouse both indispensable nowadays.

**Unlocked Possibilities:**

Now that we have a isometric tile pattern, we can create an isometric view of the stage. Collision detection, among other things, should come next.

32) 20260807 and 20260808; https://masarapmabuhay.itch.io/game-off-2025-post-test22

**Key Lesson Learned:** 

I've added an offset in the `x` and `y` positions of the background image tiles since the viewport's own `x` and `y` positions could turn negative.

Moreover, I've done tests to get the hero fixed at the center of the viewport when he moves more than half of the viewport's `width` and `height`. I found that while the hero moves as expected visually, object interaction including collision detection fails when the hero has moved beyond the viewport's center. 

After analysis, I note here that I use `mainImageTile` for many of the computations including the collision detection that occurs in the entire stage, not just the viewport, such that while the position of `mainImageTileHeroBody`, another object I use for the hero's displayed position, remains at the center, the `x` and `y` positions of `mainImageTile`, namely `mainImageTilePosX` and `mainImageTilePosY` respectively, move farther and farther away, causing the miscalculations.

Therefore, I plan to put the difference between the two objects, `mainImageTile` and `mainImageTileHeroBody`, in terms of `x` and `y` in a variable that would be added to `mainImageTilePosX` and `mainImageTilePosY` as an `offet` during computation in order to solve this problem.

**Unlocked Possibilities:**

The hero can already move around the entire stage with no apparent problems in the collision detection whatsoever. However, the size of the current stage, which is at `10x6` background tiles or `1280px` x `768px`, can still be made larger as long as the hero could remain at the center after passing half of the viewport's `width` and `height`, which are only `640px` and `360px` respectively.

33) 20260807 and 20260808; https://masarapmabuhay.itch.io/game-off-2025-post-test22

**Key Lesson Learned:** 

I've tested whether using the computed distance between the `x` and `y` positions of the `mainImageTile` and the `mainImageTileHeroBody` would resolve the problem that occurs when the hero has gone over half of the viewport's `x` and `y` positions. I found that I could get the fireballs to launch in the correct position, where `mainImageTileHeroBody` is, instead of `mainImageTile`; however, while the hero does stay walking at the center, he also keeps on going back to his initial `x` and `y` positions back when the viewport hasn't yet moved at all upong doing another left-mouse click. 

**Unlocked Possibilities:**

Although I haven't yet gotten my plan to work, the current basic side-scrolling engine is already usable. I also admit to having caught myself just wandering around the stage and casting fireballs at the constantly reappearing enemies while thinking about the problem at hand.

34) 20260809; https://masarapmabuhay.itch.io/game-off-2025-post-test23

**Key Lesson Learned:** 

I've opted to verify increasing the `width` and `height` of both the viewport and the stage as a whole, instead of putting in more time into getting the hero to move correctly at the viewport's center. Right now, here are their values:

```
var iStageMaxWidth=2560;
var iStageMaxHeight=1440;
	
var iViewportMaxWidth=1280;
var iViewportMaxHeight=720;
```

When the viewport is made larger, the hero could go an even farther distance within the stage. 

**Unlocked Possibilities:**

I've added the `Fullscreen button` on the itch.io settings as a test, even though, just like with prior Game Off tournaments, I couldn't yet get the browser to automatically zoom to my intended value without ruining my DIY game engine's collision detection, among other things that calculate the positions of the objects.

35) 20260810; work-in-progress

**Key Lesson Learned:** 

I again attempted to figure out why the hero seemed to move faster than the viewport could move. While looking at the [code](https://github.com/usbong/blue-sapphire-galaxy-java-nogl/blob/main/javaNoGL/src/UsbongMain.java#L4944) I wrote a year or so ago, I was somehow reminded that I was able to solve this problem before, only what would frequently come to mind is that I got it to work as long as the hero is always at the center of the viewport. Not that it's fundamentally flawed or anything like that, given that most old and recent 2D games seem to do just that, but perhaps I wanted to try to see for myself if I could improve it even further.

I did find a crucial hint to the cause of the problem though: I'm using two types of variables, whole integers (`int`) and another with fractions. In particular, I use `mainImageTilePosX` and `mainImageTileProjectilePosX` to move the hero and, along with him, the viewport whenever the user does a left-click with the mouse. While `mainImageTilePosX` could be, for example, `1`, `mainImageTileProjectilePosX` could get something like `1.6`. This is why the viewport always seems to be unable to catch up with the hero's position.

I will need more time to find out how to really get it to work, but for now this is what I've learned today. By the way, I used the following lines of code with the modulo (`%`) operator to measure the difference. This would output whole numbers, while the one for `mainImageTileProjectilePosX` would give me numbers with fractions.

```
if (mainImageTilePosX%1>0) {
	alert(mainImageTilePosX);
}
```

**Unlocked Possibilities:**

Being able to get the hero to remain at the center while moving around the stage means that the stage could be made even larger than only double the viewport's `width` and `height` max. Most Japanese 2D games in the 90s appear to have made use of this technique until the arrival of the Sony PlayStation and the Sega Saturn when there were more action games using an isometric point of view that came out. Unfortunately, perhaps due to the configuration of the D-pad, and even with the introduction of the analog stick, most of these games weren't as financially successful as was initially expected. 

36) 20260813; https://masarapmabuhay.itch.io/game-off-2025-post-test24

**Key Lesson Learned:** 

I've returned the width and height values to `640px` and `360px` respectively, while putting the editable variables in the `init()` function, just in case I'd want to change them again.

The new feature in this version is the addition of three extra hero bodies, which move according to the hero's movement in a train-like fashion. I was thinking about the Sega Dreamcast game, ChuChu Rocket!, which I remember seeing in magazines like Gamers' Republic back in around the 2000s. 

After trying to use a delay to get the extra hero bodies to not be exactly where the hero is at, I ended up checking instead where the hero's body is currently at and moving the extra hero body's `x` and `y` positions accordingly. Also, instead of setting the extra hero body's position where the hero is located immediately, which resulted in an odd display behavior, where the extra hero body is seen in one location and then immediately in another, I opted to simply increase or decrease the extra hero body's position incrementally using the `stepX` and `stepY`. I note here that the display error is likely caused by multiple threads doing the display and another the logic part of the code separately or non-linearly, thereby causing a `race condition`, such that the display could at times be correct, while other times not.

Finally, I added two extra hero bodies besides the first one. More could be added, of course, given that the power of present-day computer processors could already allow `2147483647` z-index values on modern web browsers, says Google AI Overview.

**Unlocked Possibilities:**

Extra bodies that move in a train-like fashion.


37) 20260814-20260816; work-in-progress

**Key Lesson Learned:** 

I've updated the viewport's movement according to what I understand my [code](https://github.com/usbong/blue-sapphire-galaxy-java-nogl/blob/main/javaNoGL/src/UsbongMain.java#L4944) a year or so ago did; however, the result is the same: `mainImageTile`'s `x` and `y` positions appear to move so much faster than moving the viewport and the monsters in the stage did.

Furthermore, simply measuring how far the hero moved with respect to the viewport's `x` and `y` positions, or just measuring the difference between the viewport's previous and current `x` and `y` positions, didn't solve the problem.

I also tried using non-whole numbers to compute the positions, but with no success.  

In the end, I'm taking too long to get this to work. 

**Unlocked Possibilities:**

I can work on other useful elements for my DIY engine and set this part aside for later.

38) 20260817-20260819; https://masarapmabuhay.itch.io/game-off-2025-post-test25

**Key Lesson Learned:** 

I've finally gotten the viewport to center on the hero, while still moving the objects and the monsters along with the viewport's movements accordingly.

I learned that I needed to not anymore update`mainImageTile`'s `x` and `y` positions, which the monsters and the other objects on the stage base their movements. Instead, I've opted to update the viewport's `x` and `y` positions, namely `iCurrViewportX` and `iCurrViewportY` respectively, according to the mouse's positions, which are `newMainImageTileProjectilePosX` and `newMainImageTileProjectilePosY`, after the user clicks the target location. 

Moreover, their values would have fractions, such that doing the following instead of using `parseInt(...)` solved the problem of getting a messed up display of the objects that included the background tiles, which I thought was related to the z-index, but wasn't, apparently.

```
fActorPosX=parseFloat(arrayActors[iCount].style.left);
fActorPosY=parseFloat(arrayActors[iCount].style.top);
```

Finally, I'm not using the `isTileInsideViewport(...)` function at all at the moment, unlike in my prior [code](https://github.com/usbong/blue-sapphire-galaxy-java-nogl/blob/main/javaNoGL/src/UsbongMain.java#L4944) in Java. 

**Unlocked Possibilities:**

This side-scrolling engine places the hero at the center, thereby allowing for a much larger stage than only double the viewport's `width` and `height`. Still, the prior version is still useful for when the stage need not be too big and the developer would prefer that the hero could move away from the center of the viewport much more than the updated engine.

39) 20260817-20260819; https://masarapmabuhay.itch.io/game-off-2025-post-test25

**Key Lesson Learned:** 

I've made the coins move automatically toward the hero when the hero is nearby. I've also updated the hero's breath animation, such that it only appears when the hero is moving directly toward the left or right, and set both its `x` and `y` to `-999999` otherwise. This number is to be kept in mind especially when creating the size of the stage, so that the hero doesn't inadvertently walk toward that point. Previously, I was setting `visibility` to `hidden`, but I learned that this creates strange behavior when the object is knowingly or unknowingly accessed when its `visibility` is currently `hidden`. As for the hero's bouncing extra bodies, I've put my notes in the `Additional Bug Fixes` section.

**Unlocked Possibilities:**

I've further improved the side-scrolling engine, so that the hero's extra bodies don't bounce up or down or shake left and right. Items like the coins now automatically move toward the hero to make them easier to pick up, reminiscent of the "Lego Batman 2: DC Super Heroes" for the PS3, a game that I played with my nephew, but never got to finish after we reached the maze in the park.

40) 20260817-20260819; https://masarapmabuhay.itch.io/game-off-2025-post-test25

**Key Lesson Learned:** 

In this version, the hero now stops more quickly when the target `x` and `y` positions that the user clicked are near his starting point, and then walks further as the target is set farther from where the hero is located.

I've also stopped the extra bodies from moving toward the hero's exact position if the target destination is where the hero is already at or very near. This is to prevent excess movements when the hero himself is clicked.

**Unlocked Possibilities:**

As I was updating the code, I found that I could set the hero to face diagonally even though he appears to be moving more directly toward the left, right, up or down. However, I've kept the code to make the hero still face directly left or right when he should.

41) 20260820-20260827; https://masarapmabuhay.itch.io/game-off-2025-post-test26

**Key Lesson Learned:** 

I've set the coins to not automatically approach the hero anymore. I'll need to create an `array` for each of them just to set whether the hero himself has approached them or not; if so, they'll have to go to the hero's position all the way through in order to prevent any coins from "hanging" or attaching themselves to the hero without disappearing.

I've again updated the `if-else` conditions to determine whether the hero was clicked, meaning that the extra bodies shouldn't need to move; I found that this part of the code had been conflicting with the collision detection to determine whether the hero would attack a monster or not. Right now, I've set the hit boxes to be more lenient in that the monsters could be attacked even though there might still be a noticeable amount of space between them and the hero.

**Unlocked Possibilities:**

I've been polishing the engine gameplay-wise, so that there's no movement or some other action that would get halted whatsoever; however, I admit that there are still plenty of other things that I'll need to add. Examples of which are the walls and the doors. 

42) 20260820-20260827; https://masarapmabuhay.itch.io/game-off-2025-post-test26

**Key Lesson Learned:** 

I've updated what I could given the time. I lost my internet connectivity as I was using Google's search engine to look up PhilWeb and other related online gaming businesses in which Filipino tycoons invest. Having said this, I've added a change in the background color when the user hovers on any of the two choices available while in the `Game Over` state.

I've also forcibly made the hero face the monster that he's hit, given that the currently lenient collision detection system allows the hero to hit the monster even while he's facing the other direction. At the moment, monsters that have hit the hero don't do this.

Finally, I've made the coin icon show its full face, rather than whatever animation frame it happens to show once the hero enters the `Game Over` state. Furthermore, the life and mana bars aren't anymore removed.

**Unlocked Possibilities:**

I've made little improvements that could be further improved to create a more animated-rich aesthetic.

43) 20260820-20260827; https://masarapmabuhay.itch.io/game-off-2025-post-test26

**Key Lesson Learned:** 

Playing the prototype over and over lets me figure out what else to add or improve. I've been updating the code to make sure that the hero is facing the monster when he throws a punch. Along the way, I thought of adding strafing by pressing the `Ctrl` key while moving the hero around. Previously, I was trying out the `Shift` key until I couldn't get rid of the default menu window whenever I did a right-click with the mouse. Here effectively using on-off switches in the form of `if-else` conditions as well as knowing where to put them were crucial, something which software programs were made to do better than the electronics hardware of old. Nowadays, robot action figures from China appear to make use of even more `articulation` and if-else conditions than ever before.

Afterward, I added custom fonts that I'm still updating in order to make sure that each character in the sentences would be aligned. I'm still also adding the non-capital letters. I note here that drawing the sentences continuously upon every update by reusing font images in an array pool creates a noticeable lag that affects the other objects on the stage.

**Unlocked Possibilities:**

My DIY engine now has more basic components that would be useful when building any type game. Still, I admit that the engine and its sample prototype could hardly be called a game yet.

44) 20260828; https://masarapmabuhay.itch.io/game-off-2025-post-test27

**Key Lesson Learned:** 

I've been adding more letters in the font image tile set, which now include letters in lower case. I note that I had to write code to automatically reduce the space between the characters including the one for the space to make them more compact, as well as bring down letters such as "g" and "j" in terms of their `y-axis` positions.

**Unlocked Possibilities:**

My handwriting on the computer using GIMP surprisingly appears cartoony, something that I could certainly use in a cartoony game that I'd want to share with family and friends. 

# Additional Bug Fixes

1) 20260619;<br/> 
+updated: shaking to move the screen to the left and the right alternately; instead of only to the right so the margin now appears not only on the left, but also on the right;

2) 20260624;<br/> 
+fixed: portion of the code that makes monster chase the hero in `executeWraithMonsterWalkingAnimation`; appears to have been inadvertently deleted

3) 20260704 and 20260705;<br/>
+fixed: bug when the hero continuously presses the attack button on a target monster even though he's exhausted all his stamina, thereby causing the monster to not change animation frames anymore, eventually leading to the monster's sudden death. The former was related to the value of `MONSTER_ANIMATION_INVINCIBLE_COUNT` found in the monster's walking and attacking animation functions, which prevented the animation counters from getting continuously counted. I've opted to simply remove this counter.

4) 20260729 and 20260730;<br/>
+fixed: bug when `New Game` is selected. It was due to using this code in `setCoinPosition(iInputX, iInputY, iCount)`:<br/>

```
if (coinImage.style.visibility=="visible") {
  return;
}
```

I've removed it, because it throws an error when `coinImage.style.visibility` is already `hidden`.<br/>
Alternatively, `checkVisibility(...)` could be modified as follows:<br/>

```
//reference: Google AI Overview; MDN Web Docs
const bIsVisible = coinImage.checkVisibility({
  visibilityProperty: true // Checks for visibility: hidden or collapse<br/>
});
```

Incidentally, I found that I was using `var hasInitMapLocation` twice, with one already at the global level. There should only be one `var hasInitMapLocation`. The rest should use `hasInitMapLocation` to be clear.

5) 20260801 and 20260802;<br/>
+fixed: bug that causes hero to suddenly dash at certain moments.  As it turns out, it was related to the value of `newMainImageTileProjectilePosX` after computing it based on `stepX` and the angle (whether its positive or negative) from the hero's current position toward his new position according to the point where the user clicked the mouse. If the maximum `stepX` is `2`, in most cases, the computed value of `newMainImageTileProjectilePosX` doesn't reach `2`. However, when it does, such as when the same point is clicked, the hero moves noticeably more rapidly. <br/>
+updated: the `y` position of the `drawHeroLifeBar(...)` and `drawHeroManaBar(...)`, so that they're not too low with respect to the image of the hero's head.

6) 20260803;<br/>
+fixed: partly the bug that causes the hero to move twice as fast when moving to the left; I simply did `newMainImageTileProjectilePosX/2` when the value is `negative`, although I'm not too certain why I needed to do so. Meanwhile, moving the viewport along with the hero makes the hero also move twice as fast. To partly solve this, I made the viewport move just when the hero's `x` position passes `iStageMaxWidth/10` where `iStageMaxWidth=640` pixels. At the moment, `stage` means the default viewport size, and not the expanded stage, which is now at `1152px` instead of `640px`.

7) 20260805;<br/>
+fixed: fireball explosion not displayed in the correct position when the hero simultaneously moves and the viewport along with it. This took me longer to fix due to the pertinent object variable for this animation image wasn't yet initialized as I had thought. The current code size has increased to `23,610` lines of code. Performing `code refactoring` will be necessary.

8) 20260808;<br/>
+fixed: the z-index of effects like the fireball explosion getting put behind the coins by not including actors with type `EFFECT_ARRAY_ACTOR_ROLE_TYPE` in the list of actors whose z-index values are to be interchanged. I also note here that as the number of actors increases, certain objects like those for showing the hero's image and status bars could get displayed incorrectly;

9) 20260818;<br/>
+fixed: extra bodies shaking when the hero's main body moves directly to the left, right, up and down by setting all `parseInt(...)` functions to `parseFloat(...)` and using `mainImageTileStepX` and `mainImageTileStepY` as the offsets in order to eliminate any event that the extra bodies would be bounced up and down or moved left and right repeatedly due to the `if-else` conditions, which would always push the hero over the allotted limit before it's again pushed the other way.

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
