![](../images/line3.png)

### Changing Sky Texture

<sub>[previous](../post-process/README.md#user-content-post-process-volumes) • [home](../README.md#user-content-ue4-lighting)</sub>

![](../images/line3.png)

We will look at using an HDRI image to create the lighting the environment which is good for portfolio pieces.  We will also look at customizing clouds as the default clouds don't have much customization at first glance. Lets start by creating another level that uses the exposure in the post production volume to chnage the exposure in each room.

<br>

---


##### `Step 1.`\|`ITL`|:small_blue_diamond:

Lets change exposure in the post production volume rather than dynamically per frame.  Go to **Maps | UnlitLevel** and select  **Duplicate** and call the new level `UnlitLevelFixedExposure`.  Double click this new level to go to it.

![dupe unlit level and call it UnlitLevelFixedExposure ](images/unlitLevelFE.png)

![](../images/line2.png)

##### `Step 2.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: 

Go to all 4 post process volumes and change **Metering Mode** to `Manual`, and **Apply Physical Camera Exposure** to `true`.  Set the **Exposure Compenstion** for the back room to `2.6`, middle room to `.2` and front gazebo & global volume to `-1`.  Double check the exposure balls in each room and make adjustments as necessary.

![set exposure for each room](images/setFixedExposure.png)

![](../images/line2.png)

##### `Step 3.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

We want to increase the radius of belnding from one volume to another.  If you <kbd>Shift</kbd> select the **PostProcessVolumeBackRoom**, **PostProcessVolumeGazebo** and **PostProcessVolumeMiddleRoom** you can adjust the **Post Production Volume Settings | Blend Radius** to `300` (3 meters or ~ 10 feet).

![change blend radius](images/adjustBlendRadius.png)

![](../images/line2.png)

##### `Step 4.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Run the game, and make a determination, do you like the audo iris settings or do you prefer having a fixed exposure per room?  Which feels more like a game, which feels more cinematic?  If I was to do one more tweak would be to give a custom exposure to the hallway by the backroom which could use an exposure boost.  I personally prefer the fixed exposure.

https://user-images.githubusercontent.com/5504953/189629265-a132d73d-360f-47f3-9adb-431ae11c0eb1.mp4

![](../images/line2.png)

##### `Step 5.`\|`ITL`| :small_orange_diamond:

Lets look at **HDRI Backdrops**. The plugin for this feature allows for high-resolution environmental images to be used as a background and an input/light source to the skylight.  The **HDRI** image needs to be a `.hdr` format and include an image with 16 bit per channel images.  The added information allows the image to represent the range of tones we can see with the human eye.  A standar 8 bit image only has 256 shades of gray, where a 16 bit image can generate over 65,000 shades of gray. So for lighting, it produces a lot more subtlety and more acccurately represents the original scene.

First lets go to **Edit | Plugins** and search for the **HDRI Backdrop** plugin. You will have to **restart** the game, to load up the editor.

![turn on HDRI Backdrop plugin](images/addHDRIBackdrop.png)

![](../images/line2.png)

##### `Step 6.`\|`ITL`| :small_orange_diamond: :small_blue_diamond:

Press **File | New Level** and pick a new **Blank Level** and call it `HDRI`.

![HDRI level](images/hdriLevel.png)

![](../images/line2.png)

##### `Step 7.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Download [T_KiaraDawn.hdr](../Assets/T_KiaraDawn.hdr) and drag it into the **Textures | Supplied** folder.

![import hdri image](images/tKiara.png)

![](../images/line2.png)

##### `Step 8.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Open up **T_KiaraDawn** and set the **Level of Detail | Meip Gen Settings** to `NoMipmaps`.  Since this is surrounding us at all times we always want to use the highest resolution image and don't want the renderer to scale it.

![turn off mip map on export](images/noMips.png)

![](../images/line2.png)

##### `Step 9.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Press the **Add Actor | Lights | HDRI Backdrop** to the level.  Assign `T_KiaraDawn` to **Cube Mip Map** on the new HDRI Background light. Rotate around and we are surrounded by this high dynamic range spherical projection.

https://user-images.githubusercontent.com/5504953/190878735-57802e0d-372d-4512-918b-1df4b91c7cf2.mp4

![](../images/line2.png)

##### `Step 10.`\|`ITL`| :large_blue_diamond:

We can adust the **Projection Center | Z** to get to the original height of where the camera was located. The ground is are cue to when it is in focus and to scale. We can also adjust the **Size** and look at the horizon to flatten it.  The **Intensity** can be adjusted to adjust the amount of light is sent by the skylight that is built into the HDRI Backdrop blueprint.

https://user-images.githubusercontent.com/5504953/190878864-c57640c4-e965-4919-bb93-4fdab61a8be4.mp4


![](../images/line2.png)

##### `Step 11.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: 

Lets add a reflective ball to see if the sky reflects into objects in the scene.  We will also see if it casts a shadow.  Go to **Add Actor | Shapes | Sphere** and drag one into the scene.  Change the **Scale** of **X Y Z** to `3.0`.  Then drag **Materials | Supplied | MI_TestBall** onto the sphere.  Put it on the ground.

![adjust sun to match new sky sphere](images/addSilverSphere.png)

![](../images/line2.png)


##### `Step 12.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Go around the cube, and the sky perfectly reflects into the ball.  Notice though that it is not casting a shadow of the ball on the ground.

https://user-images.githubusercontent.com/5504953/190879315-75bc20e9-9fbd-4c0c-b6ed-dcb0ac024b14.mp4

![](../images/line2.png)

##### `Step 13.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now the only light we need in this outdoor scene is the sun.  So go to **Add Actor | Light | Directional Light** into the scene.

![add directional light](images/sunlight.png)

![](../images/line2.png)

##### `Step 14.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Press <kbd>Cntrl L</kbd> bot bring up the light widget and then adjust so that the sun points in the same direction as the sun in the sky sphere.  Now you can see that it casts a long shadow.

https://user-images.githubusercontent.com/5504953/190899513-923b13e9-1bef-437a-a806-3d5f9ef0fb95.mp4

![](../images/line2.png)

##### `Step 15.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: 

Zoom into the reflection ball on the sun (directional light) side and adjust the **Source Angle** to soften the early morning longer shadows and the **Source Soft Angle** to adjust the sharpness of the sun in the specular reflection in the ball.

![adjust light settings](images/softenLight.png)

![](../images/line2.png)

##### `Step 16.`\|`ITL`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Add some static meshes to the scene. 

![add meshes to game](images/addMeshes.png)

![](../images/line2.png)

##### `Step 17.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Position the camera close to a mesh and turn on and off **Path Tracing** (click on the **Lit** menu in the top left corner of the game scene). Look at the difference in the shadows, the path tracer has more subtle shadowns for the final render.

![path tracing](images/pathTracing.png)

![](../images/line2.png)

##### `Step 18.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now you can see that this might be useful for virtual production if you wanted to use a real world set as it would be quicker to photograph it than model it in its entirety.  This HDRI is also useful for turntables of your artwork in your portfolio.

https://user-images.githubusercontent.com/5504953/190900080-077c1021-382e-460f-9318-ddd5387d8f52.mp4

![](../images/line2.png)

##### `Step 19.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 20.`\|`ITL`| :large_blue_diamond: :large_blue_diamond:

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 21.`\|`ITL`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

![alt_text](images/.png)

| `lighting.reflections`\|`THE END`| 
| :--- |
| **That's All Folks!** Thanks for sticking around. That's it for this lesson. |


![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - HDRI and Customize Clouds"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../post-process/README.md#user-content-post-process-volumes)| [home](../README.md#user-content-ue4-lighting) | 
|---|---|
