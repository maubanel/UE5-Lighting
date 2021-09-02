<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Rays and Lights

<sub>[previous](../reflection/README.md#user-content-reflection-captures) • [home](../README.md#user-content-ue4-lighting) • [next](../)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Lets look at adding some light shafts that interact with the sund and fog. Lets also look at some more lights to make our level really shine!

In the center room next to the gazebo we will want lights that resemble sun coming in through the windows. We are placing directional lights to act like ambient sunlight in the room. Also on the other side of the room we will use rect lights to light the inside frame with ambient light without affecting the room.

<br>

---


##### `Step 1.`\|`ITL`|:small_blue_diamond:

To make the outdoors look a lot more dramatic lets add some lens effects.  Go to the **Sun** (directional light) and turn on **Light Shaft Occlusion** and **Light Shaft Bloom**.  Look at how the sun picks up the fog and makes it look much more like we are on the ocean.

![alt_text](images/LighShafts.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

You can play with the settings and see different results.  But we essentially get some nice rays!

https://user-images.githubusercontent.com/5504953/131884060-ce78d8f6-1a10-47b2-9d0e-d3f1ac560bbe.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now lets go to the outside right of the building (looking from the Gazebo) to the large window in the middle room.  Normally in the day light would be coming in.  But since the sun isn't pointing here it is not contributing much light.  Lets add a spot light and rotate and point it at the window.

Change the color to a sky color and adjust the attenuation radius (look inside the room) so it affects the whole room.  I lowered the intensity to `3.0` lumens.  Also, since this is the sun I set **Use Inverse Square** falloff to `false`.  This stops the light from falling off like a house light as this is the sun whose fall off is too small for our eye to see.

![alt_text](images/AddFirstSpotlight.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now I adjusted the brightness as since this is opposite the sun's direction I lowered it to `1.0` lumens.  I still get a bit more detail in the inside architecture that is nice!

![alt_text](images/ThreeSpotlights.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`ITL`| :small_orange_diamond:

Put the spotlight in the **Lighting** folder. I played the game and ran around.  In my case, my character was not casting any extra shadows due to this light so I changed it to **Static**.  This way it doesn't take any more real time and is baked.  Press the <Build> button to rebuild the lights.

![make light static](images/MovedFolderStatic.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`ITL`| :small_orange_diamond: :small_blue_diamond:

Duplicate the light and move it to the next window.

![dupe light and move to next window](images/SecondWindowLight.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Make two lights set to `0.1` lumens and a very narrow **Outer Core Angle** for the two lights for the small windows above the large ones. 

![two more small lights](images/NarrowerTopLights.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now I get some very subtle fill lighting indoors that adds a bit more detail to my scene.

![lit dark side of room](images/DarkSideLight.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

I don't like the very dark area when we enter the middle room.  It has no light going to the player.  I added a spotlight from the ceiling to give this area a bit of light.

https://user-images.githubusercontent.com/5504953/131890978-dd445c22-d6e4-444a-88bd-10c7c5a9d4c5.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 10.`\|`ITL`| :large_blue_diamond:

I like the lighting effect, it is subtle but I can see the player.  Now one side effect I really don't like is the sharp shadow.  For ambient light this is way to sharp.  Lets fix that.

![sharp shadow in hallway](images/ShadowTooSharp.png)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 11.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: 

On the light adjust the **Shadow Resolution Scale**. I used a cube to test it and found `.2` about right.


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

| [previous](../reflection/README.md#user-content-reflection-captures)| [home](../README.md#user-content-ue4-lighting) | [next](../)|
|---|---|---|
