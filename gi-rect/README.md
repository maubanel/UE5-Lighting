![](../images/line3.png)

### Global Illumination & Rect Light

<sub>[previous](../point-lights/README.md#user-content-point-lights) • [home](../README.md#user-content-ue5-lighting) • [next](../light-functions/README.md#user-content-light-functions)</sub>

![](../images/line3.png)

Unreal 5's big improvement is real-time global illumination with Lumen.  This is why we have not baked any light and set the mobility to movable to have **ALL** real time lights. 

>Lumen is Unreal Engine 5's fully dynamic global illumination and reflections system that is designed for next-generation consoles, and it is the default global illumination and reflections system. Lumen renders diffuse interreflection with infinite bounces and indirect specular reflections in large, detailed environments at scales ranging from millimeters to kilometers. - [UE5 Manual](https://docs.unrealengine.com/5.0/en-US/lumen-global-illumination-and-reflections-in-unreal-engine/)

<br>

---


##### `Step 1.`\|`ITL`|:small_blue_diamond:

Lets move on to the middle room.  Duplicate the four exposure spheres by holding the <kbd>Alt</kbd> key while moving the widget direction arrow.  If you press the <kbd>Shift</kbd> key as well you the camera will move with the exposure spheres.  and move them to the front part of the middle room in front of the statue. 

https://github.com/maubanel/UE5-Lighting/assets/5504953/b28bf8c6-9c1a-4fb0-b468-a89d4ef5e9a6

![](../images/line2.png)

##### `Step 2.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: 

Now lets look at the magic of Lumen.  We now have real time global illumination in the engine.  Select the **Directional Light** (Sun) and adjust the **Indirect Lighting Intensity**. This adjusts how much the indirect light bounces off surfaces to light up surrounding areas.  I increased to `50` to show off how much it can affect the lighting but put it back to `8` which is a good amount of indirect light.

https://github.com/maubanel/UE5-Lighting/assets/5504953/5b301034-52ff-40f0-8755-3d0f9c2bddc5

![](../images/line2.png)

##### `Step 3.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

You can turn **Lumen** off in **Project Settings** (for the whole game) or in the **Post Production Volume** for this level only. If you turn Lumen off in my case the lighting blooms out and becomes much flatter. This is the power of ray tracing and really makes the overall look more realistic and more dramatic.

https://github.com/maubanel/UE5-Lighting/assets/5504953/2671396d-d7fb-4181-8451-9fb3cdbdc989

![](../images/line2.png)

##### `Step 4.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now we have another powerful tool we can adjust on the various lights.  Select the **Sun** (Directional Light) and change the **Volumetric Scattering Intensity** to `100`.  You can see that the volumetric fog now picks up the light and it much more visible. Now I want to have a bit of dramatic fog inside so I liked a setting of `3.25`.

https://github.com/maubanel/UE5-Lighting/assets/5504953/cb0fc6a4-a8ef-4e5c-a9e5-cab86f28cc2d

![](../images/line2.png)

##### `Step 5.`\|`ITL`| :small_orange_diamond:

*Press* the <kbd>Play</kbd> button and now you have a moodier feel and really nice bloom where we have the sun pass in front of the camera as we turn.  The middle room is a bit brighter than before.

https://github.com/maubanel/UE5-Lighting/assets/5504953/568f3d78-5837-470d-9c5a-cf76b36c6414

![](../images/line2.png)

##### `Step 6.`\|`ITL`| :small_orange_diamond: :small_blue_diamond:

Now some of the torches there have flames. *Click* on the coals on the torch in front of the status.  *Double click* on **M_Fire_Inst** and then *double click* on its **Parent** material called **M_Fire**. *Connect* the output of the **Multiply** node to the **Emissive Color** node in the shader. Now press the <kbdA>pply</kbd>button and now we have a flame.  Look at it in the reflection of the metallic part at the base of the statue.

https://github.com/maubanel/UE5-Lighting/assets/5504953/0a16086d-d1cd-41a4-8fd5-24fe45071615

![](../images/line2.png)

##### `Step 7.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Look at the flames in the corner and you can see it in the reflection and does affect the Global Illumination.  Now the GI can be a bit noisy and there is a bit of grain that I see.  

https://github.com/maubanel/UE5-Lighting/assets/5504953/45c96841-c87b-4e94-8127-8f871ddb0f51

![](../images/line2.png)

##### `Step 8.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Press* the <kbd>Play</kbd> button and look at the middle room.  This is getting a bit better, but we can improve it some more.

https://github.com/maubanel/UE5-Lighting/assets/5504953/9f8ed025-8703-482c-b2be-5276d0b1392a

![](../images/line2.png)

##### `Step 9.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Select the stained glass window in the middle room that has the **MI_WestStainedGlass** material. Open up **MI_WestStainedGlass** and adjust the **Window Brightness**.  My sun is rising in the east so the west side window should be less bright. I liked a value of ~`0.05`.  Notice that it again glows and affects the near environment.

![adjust window brightness](images/adjustWindowBrightness.png)

![](../images/line2.png)

##### `Step 10.`\|`ITL`| :large_blue_diamond:

Now we could make this material translucent and use the sunlight coming through but this would be very expensive.  There is a light that will do the work for us that will make it look like sun is coming through this window.  Go to **Add Actor | Lighting | Rect Light** and pull it over the window.

![add rect light](images/addRectLight.png)


![](../images/line2.png)

##### `Step 11.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: 

Now move the exposure balls in front of the window.  

![rotate rect light](images/lightAdjustment.png)

![](../images/line2.png)

##### `Step 12.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Make sure the rect light is pointing inside the room (it only goes in one direction). In this case I need to rotate it on **Z** `180`°. Play the game and make any other adjustmets you would like! Put it right next to the glass so it lights the inner frame of the window.

https://github.com/maubanel/UE5-Lighting/assets/5504953/884753c8-4cfa-4737-8943-02ef35578535

![](../images/line2.png)

##### `Step 13.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

First select the **Rect Light** and adjust the **Attenuation Radius**.  Make it slightly larger than the room so the light affects the entire area. Adjust the **Intensity** and use the exposure balls as a reference for brightness.  Tune to your taste. 

Adjust the **Source Width** and **Source Height** so it is the exact size of the window.  Make sure the rear plane fits perfectly in the sill.  Then adjust the **Barn Door Length** and **Barn Door Angle** setting to create follow the countours of the window frame which acts as a barn door for the daylight.

![rotate rect light](images/adjustRectLight.png)

![](../images/line2.png)

##### `Step 14.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now the one unique item of the rect light is that you can use a texture that will change each pixel of the light to match the color of the texture.  In this case we will use the same texture of the window in the **Source Texture** and assign `T_StainedGlass_BCH`. Notice that it now lights up the scene in color!

https://github.com/maubanel/UE5-Lighting/assets/5504953/52515353-8e45-4201-8616-bf5b8ac8d6fb

![](../images/line2.png)

##### `Step 15.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: 

Now move the exposure spheres to the front of the window.  Notice the light is still white.  We could project the texture into a light function, but lets just tint the light and adjust the brightness.

https://github.com/maubanel/UE5-Lighting/assets/5504953/226f0ff9-9944-40e9-8719-61004f5f2b24

![](../images/line2.png)

##### `Step 16.`\|`ITL`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Now we repeat theis for the east side window.  Now in my case the sun is facing from the east so it will be brighter than the west side.  First select **MI_EastStainedGlass** and adjust the **Window Brightness**. I found `0.35` works well for my taste.

![adjust birghtness of east side stained glass material](images/repeatOtherSide.png)

![](../images/line2.png)

##### `Step 17.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Copy the first rect light, rotate it 180° and put it in the opposite side window.

https://github.com/maubanel/UE5-Lighting/assets/5504953/0fb2afce-cd61-44c2-ac69-fdc38f02aebd

![](../images/line2.png)

##### `Step 18.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Rename in **Outliner** the first rect light as `StainedGlassWestRectLight` and second as `StainedGlassEastRectLight`.  Create a new folder in **Lighting** called `MiddleRoom` and drag both rect lights in there.  

![copy rect window for other side](images/copyRotate.png)

![](../images/line2.png)

##### `Step 19.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Adjust the brightness of the second rect light.  It should be a lot brighter than the west side. Since this light was on the brighter side I also increased the **Indirect Lighting Intensity**.  This increases how much it affects to surrounding GI.  Play and look at the reflections and light that these two windows add to the scene.

https://github.com/maubanel/UE5-Lighting/assets/5504953/cf589da4-5c75-4515-92d7-71c8eaafdd15

![](../images/line2.png)

##### `Step 20.`\|`ITL`| :large_blue_diamond: :large_blue_diamond:

*Press* the <kbd>Play</kbd> button and look at the middle room and make any adjustements to the stained glass window.

https://github.com/maubanel/UE5-Lighting/assets/5504953/c88bdb41-255e-4840-8eee-057a855487e2

![](../images/line2.png)

##### `Step 21.`\|`ITL`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

Select the **File | Save All** then press the #<kbd>Revision Control</kbd> button and select **Submit Content**.  If you are prompted, select **Check Out** for all items that are not checked out of source control. Update the **Changelist Description** message and with the latest changes. Make sure all the files are correct and press the <kbd>Submit</kbd> button. A confirmation will pop up on the bottom right with a message about a changelist was submitted with a commit number. Quit Unreal and make sure your **Pending** tab in **P4V** is empty. **Submit** any work that is still in the editor.

![save all and submit to perforce](images/submitP4.png)


![](../images/line2.png)

##### `Step 22.`\|`ITL`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Sometimes not all files get submitted to Unreal especially for files that don't show up in the editor.  It is good practice one you submit in **Unreal** and quit the game to right click on the top most project folder and select **Reconcile Offline Work...**.

This will either give a message saying ther is nothing to reconcile or bring up a tab.  Make sure that these are **NOT** files in the **Intermediate** and **Saved** folders as these should be ignored from the `.p4ignore`.

If the files are in **Content** or **Configuration** then press the <kbd>Reconcile</kbd> button.  Then submit the changes with a message and press the <kbd>Submit</kbd> button.

![reconcile offline work](images/reconcile.png)


![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - ADD NEXT TITLE"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../point-lights/README.md#user-content-point-lights)| [home](../README.md#user-content-ue5-lighting) | [next](../light-functions/README.md#user-content-light-functions)|
|---|---|---|
