<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Actor & Light Mobility

<sub>[previous](../light-functions/README.md#user-content-light-functions) • [home](../README.md#user-content-ue4-lighting) • [next](../)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Lets take a more in depth look at what happens when we adjust actor mobility for meshes as well as lights. These all have dramatic impacts on the look and performance of our game.

> The [Mobility](https://docs.unrealengine.com/4.26/en-US/Basics/Actors/Mobility/) setting controls whether an Actor will be allowed to move or change in some way during gameplay. This primarily applies to Static Mesh Actors and Light Actors. - Unreal Manual

<br>

---


##### `Step 1.`\|`ITL`|:small_blue_diamond:

OK, lets look at static lights and static objects.  

> For [Static Mesh Actors](https://docs.unrealengine.com/4.26/en-US/Basics/Actors/Mobility/), this means they will have their shadows contribute to pre-calculated lightmaps using Lightmass to generate and process them. This mobility makes them ideal for structural or decorative meshes that never need to relocate during gameplay. Note, however, that their Materials can still be animated.

> For [Light Actors](https://docs.unrealengine.com/4.26/en-US/Basics/Actors/Mobility/), this means it will contribute to pre-calculated lightmaps using Lightmass. They will illuminate the scene for Static and Stationary Actors and for Movable ones, use an indirect lighting method (like Indirect Lighting Samples or Volumetric Lightmaps) to illuminate these dynamic objects.

Add a **Light | Spot Light** to the scene in the middle room to the left of the doorway to the back hallway. and keep the default values.  Set the **Mobility** to `Static`. Place it high enough that the player can walk under it. 

Create a new folder called **Mobility** and put the actor in it and rename it as `StaticSpotLight`.

![alt_teadd spot light to room and set to static](images/StaticLight.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Add a **All Classes | Text Render** node and change the text to `Static Light`.  Place and rotate it on top of the spotlight.  Call it `SaticLightText` and change the render color to a shade of yellow.  Change the size to something larger such as `64`.

![add text render class for static light title](images/StaticLightText.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Add four **Cubes** under the light and place them in an interesting manner.  Change the **Scale** to `0.5` on the **XYZ** axes. Make sure the mobibility is set to **Static**.  Add a **M_StoneBrickWall** material to each cube.  Press the <kbd>Build</kbd> button to rebuild the static lights in the scene (including the one we just added)

![add 4 half size cubes and make sure they are static build lighting](images/GroupOfFourCubes.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Play the game and look at the lighting on the boxes and the shadow cast on the floor.  Look at how nicely the shadow dithers.

https://user-images.githubusercontent.com/5504953/131712876-bf8b114b-faa0-4b4f-87b1-dc4a9022f805.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`ITL`| :small_orange_diamond:

Now the lighting on the cubes and the shadow on the ground are baked.  If we move the actors the lighting disappears on the cubes and the shadow stays on the ground.  This is because the build process baked those shadows into the lightmaps.

The static meshes for pieces that we never animate and do not get affected by physics should be set to static.  That way we get terrific shadows baked into the ground.

https://user-images.githubusercontent.com/5504953/131713084-f6f3b6a6-7851-4713-ab79-779d671321d9.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`ITL`| :small_orange_diamond: :small_blue_diamond:

If you are happy with how the four cubes look you can select all four **Cubes** in the **World Outliner** and right click then select **Merge Actors**.

![merge 4 box actors](images/MergeActors.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Leave all the defaults the same and in the **Merge Actors** pop-up select **Merge**.

![press merge button](images/MergeActors2.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 10.`\|`ITL`| :large_blue_diamond:

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 11.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: 

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>


##### `Step 12.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 13.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 14.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 15.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: 

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 16.`\|`ITL`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 17.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 18.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 19.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 20.`\|`ITL`| :large_blue_diamond: :large_blue_diamond:

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 21.`\|`ITL`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

![alt_text](images/.jpg)

___


<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - ADD NEXT TITLE">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../light-functions/README.md#user-content-light-functions)| [home](../README.md#user-content-ue4-lighting) | [next](../)|
|---|---|---|
