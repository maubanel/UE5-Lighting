![](../images/line3.png)

### SkyLight

<sub>[previous](../sky-fog/README.md#user-content-sky--fog) • [home](../README.md#user-content-ue5-lighting) • [next](../point-lights/README.md#user-content-point-lights)</sub>

![](../images/line3.png)

This is the final outdoor lighting effect we will look at.  It acts as the sky ambient light for an outdoor scene. We have both outdoor and indoor scenes so we will need the skylight. The [SkyLight](https://docs.unrealengine.com/5.0/en-US/sky-lights-in-unreal-engine/) also is used for reflections in the level.  

>The Sky Light captures the distant parts of your level and applies that to the scene as a light. That means the sky's appearance and its lighting/reflections will match, even if your sky is coming from atmosphere, or layered clouds on top of a skybox, or distant mountains. You can also manually specify a cubemap to use. - Unreal Manual

<br>

---

##### `Step 1.`\|`ITL`|:small_blue_diamond:

Go back to the editor and make sure you have opened up **Window | Env Light Mixer** and select a **SkyLight**.  Move it to the **Lighting** folder.  Make sure it's mobility is set to **Movable**.

![make skylight movable](images/addSkyLight.png)

![](../images/line2.png)

##### `Step 2.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: 

Now if you zoom way up and turn the eyeball on and off.  You will see that now the water reflects the sky and that the sky is lighting the scene (taking into account the clouds). Notice that when the directional light gets turned off that the lighting doesn't disappear.  The skylight is using a capture of the sky to light up the scene with soft indirect light.

https://user-images.githubusercontent.com/5504953/188761989-cf2176a2-6bec-4c56-a22c-d51d5dee114f.mp4

![](../images/line2.png)

##### `Step 3.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now you can go back to the **Directional Light** (Sun) and now go to **Atmosphere and Cloud | Cloud Shadows** so that the cloud casts shadows on the ground.  Notice that the ground does not go black like it did before because even though the clouds are blocking the sun, the sky is still lighting the scene (especially the blue parts).  You can see the shadow on the building really soften when we take the clouds into account.

https://user-images.githubusercontent.com/5504953/188763433-13739436-f804-4133-b0e8-e8939ce4db15.mp4

![](../images/line2.png)

##### `Step 4.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now in my case it darkened the scene.  I go back to the reference balls in the room and select the **Global Post Production Volume** adjust the **Exposure | Exposure Compensation** value to re-expose the room with the new settings.

![readjust exposure](images/readjustExposure.png)

![](../images/line2.png)

##### `Step 5.`\|`ITL`| :small_orange_diamond:

Now the eyeball in the **Outliner** only affects the editor.  So if you turn off the lights using the eyeball it doesn't affect the game, just the editor.  So if you hit play, those lights work again.

https://user-images.githubusercontent.com/5504953/188764426-325f47b9-5594-4436-bb26-4bd945466d14.mp4

![](../images/line2.png)

##### `Step 6.`\|`ITL`| :small_orange_diamond: :small_blue_diamond:

If you want to turn off a light in **both** the editor and in game you can turn off the switch for **Affects World**.  Select the **Sun** actor and turn the light on and off. This way you don't have to delete a light, you can just turn it off in the editor and it will not affect the world anymore in game or in editor.

https://user-images.githubusercontent.com/5504953/188778954-651a88dd-53ef-4f2e-81a4-f97cce879aa5.mp4

![](../images/line2.png)

##### `Step 7.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now if you go back to the gazebo and you turn off **Affects World** on the **Sky Light**, you can see the shadows goes from solid and crisp to light and blurry because of the effect of the sun being filtered through the clouds.  Look in the silver ball, the sky in the reflection also disappears.  Remember the skylight provides additional environmental lighting as well as reflections.

https://user-images.githubusercontent.com/5504953/188779547-0468efb6-767d-410f-8a6b-dde2b168a637.mp4

![](../images/line2.png)

##### `Step 8.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

The first option we will look at for the **SkyLight** is the **RealTime** setting. Move the silver ball outside the gazebo and look at the reflection.  Select the **Skylight**.  Turn on and off the **Real Time** toggle.

>The Real Time Capture mode provides dynamic and specular environment lighting, making possible dynamic time-of-day simulations with real-time reflections on scene elements. - Unreal manual

This way you will see the sky atmosphere, volumetric clouds and exponential height fog all get updated in real time during gameplay. Go to your silver reflective ball and look at the difference when turning real time on and off.  When you turn it off you can recapture your scene by pressing the <kbd>SkyLight | Recapture</kbd> button in the skylight actor.

https://user-images.githubusercontent.com/5504953/188846253-0fadf7da-de51-46a4-8169-79f04cde1e89.mp4

![](../images/line2.png)

##### `Step 9.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Our reflection has a black ring at the bottom when you move outside the building.  This is because the default setting is to reflect black from the lower hemisphere.  This is useful when using a cubemap where there is lighting information from the ground plane being cast.  But in our case we have no texture on a skydome, so we want to turn off **Lower Hemisphere is Solid Color**. In our case this gets rid of the black ring around the horizon. You also notice that the new water shader is not reflecting in the Unreal reflection volume.

>Lower Hemisphere is Solid Color determines whether all lighting from the lower hemisphere should be set to zero. This is useful to prevent leaking from the lower hemisphere. Advanced.

https://user-images.githubusercontent.com/5504953/188850009-8fb6b17d-a29c-4ae7-8edd-dd4b35d7a45c.mp4

![](../images/line2.png)

##### `Step 10.`\|`ITL`| :large_blue_diamond:

Move the silver ball back into its location with the other exposure balls. Now we can adjust the resolution of the map used for reflections. We can adjust the **Cubemap Resolution**.  We will use power of two numbers so go to 512 and 1024.  It looks better but we have no mirrored surfaces.  Now in this level I think the 128 resolution will suffice.

>Maximum resolution for the very top processed cubemap MIP. It also must be a power of 2 texture. - Unreal manual

https://user-images.githubusercontent.com/5504953/188872610-aa19055a-7b2c-4c18-8bf9-b6fc65f31a49.mp4

![](../images/line2.png)

##### `Step 11.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: 

Now the **SkyLight** is using the actual sky in the game.  We can also use an **HDR** 360 capture to project instead.  I have included a few samples including this outdoor scene.  This way you can use an actual 360 photo from an existing sight to recreate the ambient lighting from that area at that time of day. 

![outdoor hdr photo](images/outdoorScene.png)

![](../images/line2.png)


##### `Step 12.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

You can match real life locations really quickly this way.  It will also affect the sky in the reflection. Go to the **SkyLight** and select **Source Type** and  choose `SLS Specified Cubemap`. Adjust the **Intensity Scale** as the scene is too dark.  Switch between the three HDR's and look how the ambient lighting changes brightness and color as well as the reflection changing.

https://user-images.githubusercontent.com/5504953/188874768-91f4cb40-4b42-48c0-aba6-2bf64d5068f5.mp4

![](../images/line2.png)

##### `Step 13.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Change the **Intensity Scale** back to `1.0`, the **Source Type** to `SLS Capture Scene` and the **Real Time Capture** back to `true`. We will use our existing sky as our lighting and reflection source.

![put cubemap back to original settings](images/returnSettings.png)

![](../images/line2.png)

##### `Step 14.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Select the **File | Save All** then press the <kbd>Source Control</kbd> button and select **Submit Content**.  If you are prompted, select **Check Out** for all items that are not checked out of source control. Update the **Changelist Description** message and with the latest changes. Make sure all the files are correct and press the <kbd>Submit</kbd> button. A confirmation will pop up on the bottom right with a message about a changelist was submitted with a commit number. Quit Unreal and make sure your **Pending** tab in **P4V** is empty. **Submit** any work that is still in the editor.

![save all and submit to perforce](images/submitP4.png)


![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Point Light"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../sky-fog/README.md#user-content-sky--fog)| [home](../README.md#user-content-ue5-lighting) | [next](../point-lights/README.md#user-content-point-lights)|
|---|---|---|