![](../images/line3.png)

### Baked Lighting

<sub>[previous](../light-functions-ii/README.md#user-content-light-functions-ii) • [home](../README.md#user-content-ue5-lighting) • [next](../baked-lighting-ii/README.md#user-content-baked-lighting-ii)</sub>

![](../images/line3.png)

Now Nanites and Lumen are amazing but they do require high end PC's.  They also do not work in VR yet or on lower power devices like cel phones.  For games that can't use nanites and lumen, lighting is done in a completely different manner, with a combination of real and baked lights.  This is by **NO MEANS** an exhaustive guide to how to make bake lights work well, but a quick intro so that you are familiar with the primary concept. We will also look at the final light a **[Directional Light](https://docs.unrealengine.com/5.0/en-US/directional-lights-in-unreal-engine/)** and **[IES](https://docs.unrealengine.com/5.0/en-US/using-ies-light-profiles-in-unreal-engine/)** lighting profiles.

<br>

---

##### `Step 1.`\|`ITL`|:small_blue_diamond:

Lets load up a level that has no nanites in it.  Double click on **Maps | UnlitLevelNoNanite**
![alt_text](images/bakedLightingLevel.png)

![](../images/line2.png)

##### `Step 2.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: 

It is bright, as we are not in manual exposure. Drop in a **Visual Effect | Post Process Volume**.

![add post process volume](images/addPostProcessVolume.png)

![](../images/line2.png)

##### `Step 3.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

We want it to effect the entire level so set the **Infinite Extent (Unbound)** to `true`. This way all our changes will affect the entire level.

![set unbound](images/unbound.png)

![](../images/line2.png)

##### `Step 4.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Lets get back to manual exposure.  Go to **Lens | Exposure** and adjust the **Metering Mode** to `Manual`, the **Exposure Compensation** to `1.0` and **Apply Physical Camera Exposure** to `true`.

![turn on full manual camera](images/manualExposure.png)

![](../images/line2.png)

##### `Step 5.`\|`ITL`| :small_orange_diamond:

Go to **Window | Env Light Meter** and click on the <kbd>Create Sky Light</kbd>, <kbd>Create Atmospheric Light 0</kbd>, <kbd>Create Sky Atmosphere</kbd>, kbd>Create Volumetric Cloud</kbd> and <kbd>Create Height Fog</kbd>. 

![add 5 lights](images/dragLightingInRoom.png)

https://user-images.githubusercontent.com/5504953/189499355-fc1c7569-8a48-457f-9869-bcc9fa6c2965.mp4

![](../images/line2.png)

##### `Step 6.`\|`ITL`| :small_orange_diamond: :small_blue_diamond:

Put all of the 5 lights/sky/effects in a **Lighting** folder in the **Outliner**.

![put 5 lights in lighting folder](images/lightingFolder.png)

![](../images/line2.png)

##### `Step 7.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Set the **Directional Light** and **SkyLight** to `Static`.

>Lights that have their Mobility set to Static are lights that cannot be changed or moved in any way during runtime. They are precomputed using Lightmass when a lighting built is performed. Static Lights store their data in textures called Lightmaps that are applied to geometry in the Level. Once the lighting build is complete, these lights have no further impact on performance.<br><br>Static Meshes with their Mobility set to Movable and Skeletal Meshes do not integrate (or blend) fully with Static Lighting. However, when a light build takes place, lighting data is stored in Volumetric Lightmaps or the Indirect Lighting Cache to assist in lighting and grounding these movable objects within a statically lit area.<br><br>Of the three light mobilities, Static Lights tend to have medium quality, lowest mutability, and the lowest performance cost. [Unreal Manual](https://docs.unrealengine.com/5.0/en-US/static-light-mobility-in-unreal-engine/)

https://user-images.githubusercontent.com/5504953/189499629-d88a146c-213b-4e2a-8fb4-15b43085c5d9.mp4


![](../images/line2.png)

##### `Step 8.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

The scene is still dark so go select the **Directional Light** and adjust the **Intensity** until you can see the sky properly.

![adjust directional light intensity](images/daylightDRValue.png)

![](../images/line2.png)

##### `Step 9.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Reasess the exposure in the post production volume. 

https://user-images.githubusercontent.com/5504953/189499754-857b6440-cab5-4bc8-b0e8-262b027d39ba.mp4


![](../images/line2.png)

##### `Step 10.`\|`ITL`| :large_blue_diamond:

**DO NOT DO THIS**.  This is the old way of baking lights that is slow and uses the CPU.  Unreal has implemented a more effective way, but we need to activate a **Plugin**.

![do not build lights](images/oldBuiildLighting.png)

##### `Step 11.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: 

Open up **Edit | Plugins** and select the **GPU Lightmass** plugin.  Accept the warning message and press the <kbd>Restart Now</kbd> button. It will take time to rebuild all the shaders.

![add gpu lightmass plugin](images/gpuLightMassPlugin.png)


##### `Step 12.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Now the **Build** menu has a **GPU Lightmass** selection.  Now selct the GPU Lightmass. 

![select gpu lightmass](images/gpuLightmass.png)

![](../images/line2.png)

##### `Step 13.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

First we need to turn off **Viewport Realtime** to get the maximum speed for the bake. Then press the **Build Lighting** button. 

https://user-images.githubusercontent.com/5504953/189500520-d2b52fea-94d8-491f-aade-0e687ffa175f.mp4

![](../images/line2.png)

##### `Step 14.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now our static meshes do not have dynamic lights but the lighting has been baked into the textures. Go back to the **Post Processing Volume** and make any needed changes to **Exposure**.

![alt_text](images/readjustExposure.png)

![](../images/line2.png)

##### `Step 15.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: 

Play game and notice all reflective surfaces are black.  We have Lumen turned off so it is no longer being used for reflections.

https://user-images.githubusercontent.com/5504953/189500693-b1eca194-9cf7-4d33-b41b-dca70051625e.mp4

![](../images/line2.png)

##### `Step 16.`\|`ITL`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Add a **Sphere Reflection Volume**.

>Reflection Capture Actors are probes that can be placed around the world to capture a static image of the area they cover. This reflection method reprojects the captured cubemap onto surrounding reflective materials. It is a low-cost method of reflections with no runtime performance cost. - [Unreal Manual](https://docs.unrealengine.com/5.0/en-US/reflections-captures-in-unreal-engine/). 

This is a much lower cost solution to using Lumen to do this at runtime.

![play game no reflections](images/sphereReflection.png)

![](../images/line2.png)

##### `Step 17.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/buildReflectoins.png)

![](../images/line2.png)

##### `Step 18.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/adjustSunlight.png)

![](../images/line2.png)

##### `Step 19.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

https://user-images.githubusercontent.com/5504953/189500913-d49cf52d-a63f-4f40-9602-ea54fda42c40.mp4

![](../images/line2.png)

##### `Step 20.`\|`ITL`| :large_blue_diamond: :large_blue_diamond:

![alt_text](images/goInBackRoom.png)


![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Baked Lighting II"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../light-functions-ii/README.md#user-content-light-functions-ii)| [home](../README.md#user-content-ue5-lighting) | [next](../baked-lighting-ii/README.md#user-content-baked-lighting-ii)|
|---|---|---|
