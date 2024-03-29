![](../images/line3.png)

### Point Lights

<sub>[previous](../skylight/README.md#skylight) • [home](../README.md#user-content-ue4-lighting) • [next](../gi-rect/README.md#user-content-global-illumination--rect-light)
![](../images/line3.png)

Lets look at adding light to the flames and embers throughout the level. We will add a static light for the embers and a dynamic one for the flames to add a bit of a realistic flicker. This will be using  a point light.  This is any light source like a lamp or flame that radiates light in all direction. 

<br>

---

| `point.lights`\|`UE4 Lighting`| 
| :--- |
| :floppy_disk: &nbsp; &nbsp; For the embers with no flame we will use a point light. This is a light that radiates equally in all directions. *[Point Lights](https://docs.unrealengine.com/4.27/en-US/BuildingWorlds/LightingAndShadows/LightTypes/Point/) work much like a real world light bulb, emitting light in all directions from the light bulb's tungsten filament. However, for the sake of performance, Point Lights are simplified down emitting light equally in all directions from just a single point in space.* |


##### `Step 1.`\|`ITL`|:small_blue_diamond:

Lets turn on another emissive material in the level that is used to represent the embers on the top of the torches.  Open up **M_FirePit** and connect the output of the **Multiply** node to the **Emissive Color** node in the main shader. 

Press the <kbd>Apply</kbd> and <kbd>Save</kbd> buttons.

![connect multiply to emissive in m_fire_pit](images/EmissiveFirePit.png)

![](../images/line2.png)

##### `Step 2.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: 

Now open up **M_FirePit_Inst_Glow** material instance and increase the **Glow** scalar to a very large number.  Notice that the color gets lighter as it gets brigher.

Now you should see an ember in every lantern except for one on the gazebo. The material is not a light so even though the emissive channel does affect the GI it is not acting like a light.  So we also want to add a point light that reflects what the fire is doing in this scene.

https://github.com/maubanel/UE5-Lighting/assets/5504953/877811c9-4264-473e-b340-c6f206b8aa14

![](../images/line2.png)

##### `Step 3.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now you should see some of the torches in the level are glowing.  Lets add a Point Light to light up the surrounding. Now these materials send a light but not enough. If we use too much glow it will be noisy in the game and the color will get too hot for the amount of ligh We should add a point light (a radiating light like a light bulb).

![torches glowing](images/TorchesGlow.png)

![](../images/line2.png)

##### `Step 4.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

So press the **Add Actor** button and select a **Light | Point Light** and drag it on top of the lantern.  Position it just inside the center of the embers.  Change the **Light Color** to match the orange of the glow and set the **Intensity** to an appropriate level that radiates subtly on the edge of the column.  Drag it into the **Lighting** folder and name it `Ember Glow`. Set the mobility to **Movable**.

![torches glowing](images/addPointLight.png)

##### `Step 5.`\|`ITL`| :small_orange_diamond:

Center the light inside the torch.  Adjust the height so that the right amount of shadow emanates from the edges of the torch. Now lets adjust the **Attenuation Radius**.  This is the distance the light will travel before it no longer affects the world.  It is the distance a light travels before its light drops to 0.  It is indicated with the light colored sphere.  The smaller the more performant and the more lights we can place.  Since this is just an ember I set mine to `130` cm.

https://github.com/maubanel/UE5-Lighting/assets/5504953/145f19ed-b3e4-4ff1-93e6-78c5448a422b

![](../images/line2.png)

##### `Step 6.`\|`ITL`| :small_orange_diamond: :small_blue_diamond:

I also set the **Source Radius**.  This is how large and what shape is the light emanating from.  It is the entire coal bed so I set mine to `27`. This is the inner yellow sphere. This not only affects how large a radius the light is emitted from, but it also shows up in the reflection.  Move the silver ball close to the light and see how the glow grows with the source radius.  Now the **Soft Source Radius** affects how soft the light is and since this is an ember and not a flame it looks a bit bright so we will soften the radius of the light.  This is easiest to see in the silver ball. I went really soft with the soft source as it is a glowing ember and not a light.

https://github.com/maubanel/UE5-Lighting/assets/5504953/7ea1bc80-40be-44c0-840b-c840ff959d87

![](../images/line2.png)

##### `Step 7.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now we need to pick the color. Move to a glow without the light and use the color picker to pick an orangy hue.

![torches glowing](images/useColorPicker.png)

![](../images/line2.png)

##### `Step 8.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now adjust the light intensity.  Turn it on and off with **Affect World**.  Remember this is just an ember so it should be a *really subtle* glowing light.  It radiates in all directions making it suitable for a point light. So a value of `0.1` or `0.2` is not out of the question.

https://github.com/maubanel/UE5-Lighting/assets/5504953/7157374b-e96e-4d36-90c4-dbeecdf2f568

![](../images/line2.png)

##### `Step 9.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Press* the <kbd>Play</kbd> button and look at the light you created.  Notice the effect is quite subtle which is exactly what we want.  It is an ember and not a raging flame, so the light should be sublte.

https://github.com/maubanel/UE5-Lighting/assets/5504953/a9bbc683-4547-44d0-87d1-12a9e7a2e068

![](../images/line2.png)

##### `Step 10.`\|`ITL`| :large_blue_diamond:

lt drag another copy of the ember light to each lantern that either has an ember. You should hvae a total of 7 lights on the gazebo. Make 6 copies and place them inside each burning ember. There is one stand that has neither and we will not place a light here. 

https://github.com/maubanel/UE5-Lighting/assets/5504953/316e3de1-239b-4ccb-97ac-4d4d0442702e

![](../images/line2.png)

##### `Step 11.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: 

Now lets organize the outliner a bit.  Put the 4 exposure balls inside a folder called `Exposure Reference`.

![add folder for exposure balls](images/putBallsInFolder.png)

![](../images/line2.png)

##### `Step 12.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

In the **Lighting** folder create a folder called **Gazebo**. Name the lights appropriately, I have named them **EmberGlowPointLight** and move them into the new folder.

![add folder for exposure balls](images/nameLights.png)

![](../images/line2.png)

##### `Step 13.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Select the **File | Save All** then press the #<kbd>Revision Control</kbd> button and select **Submit Content**.  If you are prompted, select **Check Out** for all items that are not checked out of source control. Update the **Changelist Description** message and with the latest changes. Make sure all the files are correct and press the <kbd>Submit</kbd> button. A confirmation will pop up on the bottom right with a message about a changelist was submitted with a commit number. Quit Unreal and make sure your **Pending** tab in **P4V** is empty. **Submit** any work that is still in the editor.

![save all and submit to perforce](images/submitP4.png)

![](../images/line2.png)

##### `Step 14.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Sometimes not all files get submitted to Unreal especially for files that don't show up in the editor.  It is good practice one you submit in **Unreal** and quit the game to right click on the top most project folder and select **Reconcile Offline Work...**.

This will either give a message saying ther is nothing to reconcile or bring up a tab.  Make sure that these are **NOT** files in the **Intermediate** and **Saved** folders as these should be ignored from the `.p4ignore`.

If the files are in **Content** or **Configuration** then press the <kbd>Reconcile</kbd> button.  Then submit the changes with a message and press the <kbd>Submit</kbd> button.

![reconcile offline work](images/reconcile.png)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Global Illumination and Rect Light"> -->
![next up next tile](images/banner.png)

![](../images/line.png)


| [previous](../skylight/README.md#skylight)| [home](../README.md#user-content-ue4-lighting) | [next](../gi-rect/README.md#user-content-global-illumination--rect-light)|
|---|---|---|
