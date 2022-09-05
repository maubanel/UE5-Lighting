![](../images/line3.png)

### Directional Light & Exposure

<sub>[previous](../setting-up/README.md#user-content-setting-up) • [home](../README.md#user-content-ue4-lighting) • [next](../point-lights/README.md#user-content-point-lights)</sub>

![](../images/line3.png)

Lets get ready to start lighting the scene. Before we can begin we need to add the sky sphere, light up the water and add two types of fog fog.  We will also add a post processing volume to kill the auto iris so that we can light the level with a fixed exposure. We will rotate the sun to match the skybox. This will set up the very basics of the scene for this level.

<br>

---

##### `Step 1.`\|`ITL`|:small_blue_diamond:

Since most of this scene is lit by sun through openings in this structure we will add a **Place Actors | Lights | Directional Light** to the level.  Ensure the mobility is **Stationary** and we will explain this later.

The placement is irrelevant of where you put the light in the level.  It will light the entire scene.  It lights at an infinite distance (which for us is essentially how the sun behaves, it doesn't fall off like an artificial light). The position is not important.  The light shafts are parallel so the shadows are proportianal.

> The [**Directional Light**](https://docs.unrealengine.com/5.0/en-US/directional-lights-in-unreal-engine/) simulates light that is being emitted from a source that is infinitely far away. This means that all shadows cast by this light will be parallel, making this the ideal choice for simulating sunlight.  - Unreal Manual

![add directional light to scene](images/addDirectionalLight.png)

![](../images/line2.png)

##### `Step 2.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: 

Now the sun's XYZ position in the scene doesn't matter but its rotation does.  It changes the angle of the sun (directional light).  Pressing <kbd>Cntrl L</kbd> allows you to rotate the angle (or if that doesn't work you can use the rotation gizmo).  Pick one where the sun is coming into the porch with longer shadows.

https://user-images.githubusercontent.com/5504953/188311367-23c0e83a-3d1b-41ac-936a-15c9d23f02b2.mp4

![](../images/line2.png)

##### `Step 3.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

We will also add a folder called `Lighting` to the **World Outliner**. We will rename the light to `Sun` and move it inside the new **Lighting** folder.

![rename directional light](images/renameSun.png)

![](../images/line2.png)

##### `Step 4.`\|`ITL&G`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now go to **File | Project Settings** and look for **Default RHI** and it should be set to `DirectX 12`.  We need this for Lumen to work properly.  We will look at some Ambient Occlusion settings that can make up for not having hardware raytracing, so we can enable **Generate Mesh Distance Fields**. Set **Use Hardware Ray Tracing when available**.  This will use hardware raytracing when there a a GPU that supports it like all RTX NVidia cards do. And finally, Unreal originally had scalar values for light and did not use real world values (which is critical for architectural visualization and film) but also better to use going forward as the numbers have meaning.  Go to **Extend default luminance range in Auto Exposure settings** to `true`.  Now these changes will require you to restart so press the <kbd>Restart Now</kbd> button.  Now take short break as it will take a while to recompile all of your shaders.

![alter default settings in UIE5](images/newSettings.png)

![](../images/line2.png)

##### `Step 5.`\|`ITL`| :small_orange_diamond:

Now in Unreal 4 we relied on baked lighting to get good performance out of Unreal.  With Lumen and Nanites we can now have real time global illumination which looks great.  So we no longer have to bake lights.  Lets go to the **Directional Light** and set **Mobility** to `Movable`.

![change directional light to movable](images/movableLight.png)

![](../images/line2.png)

##### `Step 6.`\|`ITL`| :small_orange_diamond: :small_blue_diamond:

We don't want the auto iris exposure built in the game affect our lighting settings.  It is hard to light when it opens up to iris to light the scene. Move the camera to and from the front porch to the hallway and you can see that it compensates (like our eyes do or auto exposure on your camera).

So lets go add a **Volumes | Post Process Volume** to the level.  Go to **Post Process Volume Settings | Infinite Extent** and tick the box to `true`.  We want to have this volume affect every object in the world even if it falls outside this box. This allows us to appy effects to the entire level.

![add ppv and set to unbound](images/GlobalPostProcessV.png)

![](../images/line2.png)

##### `Step 7.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Call it `GlobalPostProcessingVolume` and move it to the **Lighting** folder. 

![rename ppv adding global](images/GlobalPostProcessV.png)

![](../images/line2.png)

##### `Step 8.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now when you move the camera to and from the hallway look at the sides and the back.  You can see that the exposure is compensating just like our eyes do when moving from outdoors to indoors or vice versa.  For lighting we want to remove it, then turn it back on when we are done.  Look carefully at the game and see if you can spot it?

https://user-images.githubusercontent.com/5504953/188335700-99b05a27-ff06-4e8c-8ce7-94eca7f6d8dc.mp4

![](../images/line2.png)

##### `Step 9.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now go to the sun and see that is is only putting out an **Intensity** of `10.0 lux`.  The real sun  would put out [120,000](https://en.wikipedia.org/wiki/Daylight) lux on the brightest day all the way down to 1,000 lux on overcast days. to the **GlobalPostProductionVolume | Lens | Exposure** and set **Metering Mode** to `Manual`.  And turn on **Apply Physcis Camera Exposure** to `true`. This only applies to a manual exposure setting. Now the scene gos dark.  Go back to the **Sun** directional light and adjust the exposure all the way up to `120000`.

https://user-images.githubusercontent.com/5504953/188335980-055ac744-c9a9-4fa2-bb39-4e5fd2e9ab8c.mp4

![](../images/line2.png)

##### `Step 10.`\|`ITL`| :large_blue_diamond:

Turn down the **Intensity** of the **Sun** to `90 000 lux`.

![sun 90k lutz](images/90klutz.png)

![](../images/line2.png)

##### `Step 11.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: 

Now before we can properly set the exposure we should have a range of spheres in the level that has white, black, mid gray and a reflective ball for the specular and reflections.  Go to **Materials | Supplied** and select **M_Basic** and right mouse click to select `Create Material Instance`.  Call this new instance `MI_GrayScale`. 

![create material instance grayscale from m_basic](images/materialInstance1.png)

![](../images/line2.png)


##### `Step 12.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :
 
Now middle gray that we use in photograph as a grey card is at [18% gray](https://en.wikipedia.org/wiki/Gray_card). This mid gray is a good reference for white balance and finding the middle ground.  So our **R G B** are all `.18`, we have minimal **Specular** with `.1` and a very high roughness with `.908`.  So there is not much specularity, just mid gray.   

![water and sky in game](images/greyCardPBR.png)

![](../images/line2.png)

##### `Step 13.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now add a  **Place Actors | Shapes | Sphere** and make the **Scale** `0.65` on **X Y Z**.  Make it a bit smaller.  Place it half in sun and half in shadow and drag the **MI_GrayScale** material you just created.

![set gray scale](images/grayScale.png)

![](../images/line2.png)

##### `Step 14.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 
 
Now right click on **MI_GrayScale** and select duplicate and make a `MI_White`, duplicate again and make a `MI_Black`, and duplicate a final time and make a `MI_TestBall`.  

**MI_White** is an **R G B** of `.9` which is very bright snow.  There is no pure white in nature so `0.9` is about as high as we want to go.  Make the **Specular** `.5`, leave the **Metallic** at `0` and change the **Roughness** to `.75`.

For **MI_Black** use **R G B** of `.05` which is very dark latex paint.  There is no pure dark in nature so `.05` is about as low as we want to go.  Make the **Specular** `.5`, leave the **Metallic** at `0` and change the **Roughness** to `.75`.

For **MI_Ball_Test** use **R G B** of `.9` which is very bright.  Make the **Specular** `.7`, and change the **Metallic** to `1` and change the **Roughness** to `.05`.

Now stack 4 ballls with white at the bottom, then gray, then black and silver at the top.  Create a folder called **Exposure Reference** and name the ball's accordingly. Make sure all the new materials are assigned.

![add three more balls](images/addThreeMoreBalls.png)

![](../images/line2.png)

##### `Step 15.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: 

Now we can finally set the exposure.  Go back to the **GlobalPostProcessVolume** and when we the **Lens | Exposure** section's **Exposure Compensation** up we blow out the white, if we turn it down too low we go out to black.  We want to see good definition of the different brightness in the shade and in the light.  Pick a middle ground value that works for you.  `-1.64` works best for me to tone down the brightness.

https://user-images.githubusercontent.com/5504953/188338730-7ad547c5-51c9-45be-8147-36f5959c7f39.mp4

![](../images/line2.png)

##### `Step 16.`\|`ITL`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Now there are two more settings for the directional light we want to look at. Lets highlight the **Sun** directional light and adjust the **Source Angle**.  `0` is completely sharp shadows with a hard edge and anything above 0 increase the [penumbra])(https://nineplanets.org/penumbra-shadow/).  The more clouds the larger the penumbra, and the less clouds with very clear air the crisper the shadows.  If you look at the specular in the silver ball the sun also gets more diffuse the larger the number.

You can also adjust the **Soft Source Angle**.  This affects mostly the specular.  Look at the reflection ball and it softens the lights sources.  I liked a **Source Angle** of `3.28` and a **Source Soft Angle** of `1.68`.

https://user-images.githubusercontent.com/5504953/188339500-3b148242-a80a-4ba1-a077-382c042615e2.mp4

![](../images/line2.png)

##### `Step 17.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now you can also change between the engine doing the shadows through software or through ray tracing if you have a ray tracing gpu.  Go to the **Sun** directional light and select **Cast Ray Traced Shadows**.  Switch between **Use Project Settings** and **Enabled**.  YOu can see there is some noise in the ray traced shadows by they are a bit more detailed and subtle.

https://user-images.githubusercontent.com/5504953/188353653-4173684f-bd9a-4381-8c49-209331c0ace1.mp4

![](../images/line2.png)

##### `Step 18.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Press* the <kbd>Play</kbd> button and run around.  Now our exposure is good for the bright end of the front porch but is too dark inside.  We will address that next.

https://user-images.githubusercontent.com/5504953/188353839-975604cb-cd71-40ba-9c2d-580806d8ef38.mp4

![](../images/line2.png)

##### `Step 19.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Select the **File | Save All** then press the <kbd>Source Control</kbd> button and select **Submit Content**.  If you are prompted, select **Check Out** for all items that are not checked out of source control. Update the **Changelist Description** message and with the latest changes. Make sure all the files are correct and press the <kbd>Submit</kbd> button. A confirmation will pop up on the bottom right with a message about a changelist was submitted with a commit number.

![save all and submit to perforce](images/submitP4.png)


![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Sky and Fog> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../setting-up/README.md#user-content-setting-up)| [home](../README.md#user-content-ue4-lighting) | [next](../point-lights/README.md#user-content-point-lights)|
|---|---|---|
