![](../images/line3.png)

### Light Functions

<sub>[previous](../gi-rect/README.md#global-illumination--rect-light) • [home](../README.md#user-content-ue4-lighting) • [next](../light-functions-ii/README.md#user-content-light-functions-ii)</sub>

![](../images/line3.png)

Now we have a back room with no incidental window light and just flames.  So lets add a point light with a light function that will exaggerate the indirect light of the flames.  A light function material allows us to alter what a light does. In this case it will be to change the intensity to look like flickering fire light.

<br>

---

##### `Step 1.`\|`ITL`|:small_blue_diamond:

Lets create a new **Material** in the **Materials | Master** folder.  Click on <kbd>+ Add</kbd> and select a new **Material** and call it `FL_Flicker`. Open up the material and click on the Material node.  Change the **Material Domain** to `Light Function`.  This will turn off all the pins except for emission (as you cannot use any texture effects on the light - just affect the luminance).  

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

https://github.com/maubanel/UE5-Lighting/assets/5504953/1e4cc935-d91d-4763-b0ab-aeceea691c29

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

To add more randomness we can add together three sine waves that have a different period.  So lets multiply time by `2.5` and `2` take an input from **Time** then send them to their own sine nodes (for a total of 3 sine nodes).

![triple the speed of the flicker](images/doubleMultiply.png)

![](../images/line2.png)

##### `Step 11.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: 

Right click on the open graph and select an **Add** node.  Take the output of the seconds and third **Sine** nodes and add them together.  Put a second **Add** node next to it with the output of the first add node in the **B** side of the second add node and the output of the first **Sine** to the **A** side. This adds up all sine nodes.  Send the final output to the absolute value **Abs** node.

![place two add nodes](images/firstSum.png)

![](../images/line2.png)


##### `Step 12.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Now since we are adding up three sine waves we can get a range from -3 to 3.  So we should divide the result by `3.0`.

![connect time to multipies](images/divide3.png)

![](../images/line2.png)

##### `Step 13.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now we should have a more random looking flashing that is a bit more subtle.

https://github.com/maubanel/UE5-Lighting/assets/5504953/114b5687-5b89-46e3-b50b-372d36c1dc2b

![](../images/line2.png)

##### `Step 14.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Add three **Scalar Paremeter** nodes.  Call them `SineSpeed1`, `SineSpeed2` and `SineSpeed3`. Make them a **Default Value** of `3`, `2` and `2.5`.  Make all the **Group**'s `LightFlicker` and set the **Sort Priority** from `0` to `2`.

![add three scalar parameters](images/addThreeScalarParams.png)

![](../images/line2.png)

##### `Step 15.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: 

Add another **Mutliply** node at the end so we can scale the amount of emissive coming from the light.

![add three scalar parameters](images/multiplyScalar.png)

![](../images/line2.png)

##### `Step 16.`\|`ITL`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Lets allow the user to alter the addition shifting the range and the multiplyer, making it brighter. Add two more scalar parameters. Call the first `SineShift` and set it to `0.5` and plug it into the **B** side of the second **Add** node.  The second is set to `Brightness` with a default value of `2.5` and sent into the **Multiply | B**. Clean up the nodes and add a comment. Change the **Group** to `LightFlicker` and set the **Sort Priority** to `3` and `4`

![add two more scalar parameters](images/addTwoMoreScalars.png)

![](../images/line2.png)

##### `Step 17.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now you can preview what it looks like as we go from the pure sine waves added to adjusting it back to the 0 to 1 zone keeping the values positive. Press the <kbd>Apply</kbd> button.

https://github.com/maubanel/UE5-Lighting/assets/5504953/b27b8a72-b9eb-438d-88fd-e5895c7590f6

![](../images/line2.png)

##### `Step 18.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Your final node chart should look like the below.  Select all the nodes and press the <kbd>C</kbd> and put a comment box and clean up the node chart.

![add two more scalar parameters](images/finalFlickerWithComments.png)


![](../images/line2.png)

##### `Step 19.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Right click on **FL_Flicker** and select **Create Material Instance**.  Call it `MI_FlickerBackRoom`.

![create material instance](images/matInstance.png)

![](../images/line2.png)

##### `Step 20.`\|`ITL`| :large_blue_diamond: :large_blue_diamond:


Go to the very back room and above the large fire pit add a **Light | Point Light** to the room.  Add it to a new folder called `BackRoom` in the **Lighting** folder. Call the light `BackLight`.

![add point light to back room](images/pointLightBackRoom.png)

![](../images/line2.png)

##### `Step 21.`\|`ITL`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

Now match the orange glow coming off of the embers in the large fire pit.  I used the eydropper tool to pick a dark rich orange for the glow (remember the emission multiplier brings it closer to white).

![make light orange](images/matchOrange.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Light Functions II> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../gi-rect/README.md#global-illumination--rect-light)| [home](../README.md#user-content-ue4-lighting) | [next](../light-functions-ii/README.md#user-content-light-functions-ii)|
|---|---|---|
