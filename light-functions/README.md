![](../images/line3.png)

### Light Functions

<sub>[previous](../point-lights/README.md#user-content-point-lights) • [home](../README.md#user-content-ue4-lighting) • [next](../mobility/README.md#user-content-actor--light-mobility)</sub>

![](../images/line3.png)

Now we have a back room with no incidental window light and just flames.  So lets add a point light with a light function that will exaggerate the indirect light of the flames.  A light function material allows us to alter what a light does. In this case it will be to change the intensity to look like flickering fire light.

<br>

---

##### `Step 1.`\|`ITL`|:small_blue_diamond:

Lets create a new **Material** in the **Materials** folder.  Click on <kbd>+ Add</kbd> and select a new **Material** and call it `FL_Flicker`. Open up the material and click on the Material node.  Change the **Material Domain** to `Light Function`.  This will turn off all the pins except for emission (as you cannot use any texture effects on the light - just affect the luminance).  

![hook up multiply to emissive in m_fire](images/flFlickerLightFunction.png)

![](../images/line2.png)

##### `Step 2.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: 

Add a **Time** node to animate the light with.  This returns time in milliseconds. Then add a Sine node that converts that value into a sine.  If you know what a sine wave is, it will return a value between -1 and 1.  Connect the pins and send the output of the **Sine** node to the **Emissive Color** node in the material.

![add time and sign to node](images/timeSign.png)

![](../images/line2.png)

##### `Step 3.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

You will notice that since it goes from -1 to 1 that half of the time it is is completely off, less than 0.  Lets fix that.

https://user-images.githubusercontent.com/5504953/189472736-de500525-1eb0-4796-8961-b3672cac7b77.mp4


![](../images/line2.png)

##### `Step 4.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

If we add an **Abs** node at the end before the shader we will make sure the value is always positive.  This absolute node returns a positive unsigned value regardless of the sign passed in. So '-.5` becomes `.5`.  Notice how it changes the shape of the curve.

![add abs node](images/addABS.png)

![](../images/line2.png)

##### `Step 5.`\|`ITL`| :small_orange_diamond:

Now the value is always positive. Now the problem the light goes to `0`.  We want it to flicker but not turn off completely.

https://user-images.githubusercontent.com/5504953/189472860-bd3d5456-5aa1-4b4e-91ed-060f455d2d6e.mp4

![](../images/line2.png)

##### `Step 6.`\|`ITL`| :small_orange_diamond: :small_blue_diamond:

So lets shift the whole curve up by .5.  So at the end put an **Add** node and set the **Value** to `0.5`.  This changes the range of the absolute sine from `.5` to `1.5`.

![add m_flickerflame material](images/addpoint5.png)

![](../images/line2.png)

##### `Step 7.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now the issue is that we have shifted the value, it is flickering too slowly.

https://user-images.githubusercontent.com/5504953/189473173-ea5cf95a-fd72-4698-b7e0-d86cd2b5b804.mp4

![](../images/line2.png)

##### `Step 8.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

 So lets multiply the time node to speed up the flicker. Set the **Default Value** to `3.0` to triple the speed.

![triple the speed of the flicker](images/mutliplyTime.png)

![](../images/line2.png)

##### `Step 9.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now it flashes much quicker.  But it is a constant curve.  Flickering should be an assymetrical flashing, so a straight absolute sine wave is to perfect.  We need to add more randomness.

https://user-images.githubusercontent.com/5504953/189473330-e3d307d7-a1d6-4d66-a4bf-2f9916607ddf.mp4

![](../images/line2.png)


##### `Step 10.`\|`ITL`| :large_blue_diamond:

Right click on the open graph and select an **Add** node.  Take the output of the first and second **Sine** nodes and add them together.  Put a second **Add** node next to it with the output of the first one in the **A** side of the second add node.

![place two add nodes](images/firstSum.png)

![](../images/line2.png)

##### `Step 11.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: 

Connect **Time** to two multiply nodes.

![connect time to multipies](images/connectTime.png)

![](../images/line2.png)


##### `Step 12.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Now this gives us a really nice effect.  Lets turn these constants into parameters that we can edit in a light function instance material!

https://user-images.githubusercontent.com/5504953/189475041-2e5bb478-76c8-43e2-964d-7908fc0b523b.mp4


![](../images/line2.png)

##### `Step 13.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Add three **Scalar Paremeter** nodes.  Call them `SineSpeed1`, `SineSpeed2` and `SineSpeed3`. Make them a **Default Value** of `3`, `2` and `2.5`. 

![add three scalar parameters](images/addThreeScalarParams.png)

![](../images/line2.png)

##### `Step 14.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Add two more scalar parameters. Call the first `SineShift` and set it to `0.5` and plug it into the **B** side of the second **Add** node.  The second is set to `Brightness` with a default value of `10` and sent into the **Multiply | B**.

![add two more scalar parameters](images/addTwoMoreScalars.png)


![](../images/line2.png)

##### `Step 15.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: 

I backed off the **Intensity** from `10` to `2` lumens.  This provides a more subtle and realistic effect. The flicker also relects in the mannequin's surface, super cool!

https://user-images.githubusercontent.com/5504953/131690553-f30e19aa-350f-4292-8f1a-b83128bcc5bb.mp4

![](../images/line2.png)

##### `Step 16.`\|`ITL`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Lets now place 8 more flickering lights (for a total of 9 lights) on the remaining fires.  In my case it is **SM_FirePit_4**, **SM_FirePit_6**, **SM_FirePit_8**, **SM_FirePit_18**, **SM_FirePit_22**, **SM_FirePit_24**, **SM_FirePit_25** and **SM_FirePit_28** (the one I did above was **SM_FirePit2**). Duplicate 8 more lights. Copy and paste the position of the torch with each light and adjust the position. 

https://user-images.githubusercontent.com/5504953/131701352-f6e18cdd-2afb-4141-8e0d-f29f46851764.mp4

![](../images/line2.png)

##### `Step 17.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Right click on **M_FlickerFlame** and create 3 **Material Instances**.  Turn on **Flicker Speed** and set it to `1.3`,  `1.6` and `1.8`. Now with the original master material we have 4 different speeds. 

![add three material instances of M_FlickerFlame and change the flicker speed to 4 different values](images/ThreeMatInstances.jpg)

![](../images/line2.png)

##### `Step 18.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go to all of your **Flame Flicker Spotlight** actors and mix up the **Light Function Materials** assigning an equal amount of the 4.  Make sure no two lights close to each other or in the same vincinity have the same material.

![add different material instances to each actor](images/MIxUpMaterialInstances.jpg)

![](../images/line2.png)

##### `Step 19.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now you might notice that the generated shadows created in the lighting build are not of high quality.  We have been using a fast preview lighting model.  If you click on the arrow next to the **Build** button, you can adjust the **Lighting Quality** from `Preview` to `Medium`.  We can do this occasionally to get a better sense of how it will look to be more critical of our work.  Press **Build Lighting Only**.

![build medium quality lights](images/DefaultLightQuality.jpg)

![](../images/line2.png)

##### `Step 20.`\|`ITL`| :large_blue_diamond: :large_blue_diamond:
 Now run the game and look at all the firelight.  See how it adds a bit of life to the scene.  It is especially important in levels that are fairly bare with few people have enough elements in the scene that look alive to give it some life.  This is a nice addition.  You notice the shadows are better rendered in our baking process.  You can return to a **Preview** lighting quality to make future light builds faster.

https://user-images.githubusercontent.com/5504953/131703962-9481e5fb-6c37-4ae9-aaea-5dfa9f5d88c9.mp4

![](../images/line2.png)

##### `Step 21.`\|`ITL`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

Press **File | Save All** and press **Source Control |  Submit to Source Control...** and enter a **Description** then press the <kbd>Submit</kbd> button. Open up **GitHub Desktop** and press the <kbd>Push</kbd> button. Now we are updated.

![save all, commit and push to github](images/GitHub.jpg)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - ADD NEXT TITLE"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../point-lights/README.md#user-content-point-lights)| [home](../README.md#user-content-ue4-lighting) | [next](../mobility/README.md#user-content-actor--light-mobility)|
|---|---|---|
