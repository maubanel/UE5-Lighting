![](../images/line3.png)

### Sky & Fog

<sub>[previous](../) • [home](../README.md#user-content-ue5-lighting) • [next](../)</sub>

![](../images/line3.png)

Now that we have a single direct light we need a sky to reflect the light and act like our real atmoshpere.  We will also add some fog into the scene as air is not always completely translucent.

<br>

---


##### `Step 1.`\|`ITL`|:small_blue_diamond:

Now we have a convenient tool for setting up levels quickly.  You can click on **Window | Env. Light Mixer** and it brings up all of the elements you need to complete an initial pass at lighting the level.

![environmental light mixer](images/envLightMixer.png)

![](../images/line2.png)

##### `Step 2.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: 

Now add a **[Sky Atmosphere](https://docs.unrealengine.com/5.0/en-US/sky-atmosphere-component-in-unreal-engine/)** to the level.  Notice that our sky goes from black to an actual atmosphere.  

> The Sky Atmosphere component in Unreal Engine is a physically-based sky and atmosphere-rendering technique. It's flexible enough to create an Earth-like atmosphere with time-of-day featuring sunrise and sunset, or to create extraterrestrial atmospheres of an exotic nature. - Unreal Manual

Change the sun position and notice that the atmosphere changes based on the position of the sun.

https://user-images.githubusercontent.com/5504953/188452815-0ea89816-b8ce-4a08-aa3e-035049efc78b.mp4

![](../images/line2.png)

##### `Step 3.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

> The sky atmoshphere also provides an aerial perspective to which you can simulate transitions from ground to sky to outer space with proper planetary curvature. - Unreal

Now you can can adjust the camera speed and zoom out into space.  Our island disappears as those object culls are set to not render at a certain distance.  But you can see that we have a complete earth like atmosphere even in space.

https://user-images.githubusercontent.com/5504953/188460013-14fa14af-d427-4748-bf87-35e7cdf3e9ee.mp4

![](../images/line2.png)

##### `Step 4.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

You can make many adjustments but most of the defaults are set for planet earth so not much needs to be done for realistic earth like atmosphere. There is one adjustment that affects the "thickness" of the atmosphere as if higher up in the sky (like on the top of a mountain). In the Sky Atmosphere you can change the **Art Direction | Aerial Perspecive View Distance Scale**. You can see a change on the horizon.

> The Aerial Perspective View Distance Scale property scales distances from the view to surfaces to make them look thicker when viewed from a high enough distance above the ground surface. - Unreal manual

https://user-images.githubusercontent.com/5504953/188461608-8034546b-c7cb-4fcd-b67e-0358caba7c62.mp4


![](../images/line2.png)

##### `Step 5.`\|`ITL`| :small_orange_diamond:

Move the **SkyAtmosphere** actor to the **Lighting** folder.

Now you can add **Volumetric Clouds** from the **Env Light Mixer** to add moving clouds to the sky. And you see volumetric clouds in the sky.  

>The [Volumetric Cloud](https://docs.unrealengine.com/5.0/en-US/volumetric-cloud-component-properties-in-unreal-engine/) component is a physically-based cloud rendering system that uses a material-driven approach to give artists and designers the freedom to create any type of clouds they need for their projects. The cloud system handles dynamic time-of-day setups that is complemented by the Sky Atmosphere and Sky Light using the real time capture mode. The system provides scalable, artist-defined clouds that can adapt to projects using ground views, flying, and ground to outer space transitions. - Unreal Manual

![add volumetric clouds](images/volumetricClouds.png)

![](../images/line2.png)

##### `Step 6.`\|`ITL`| :small_orange_diamond: :small_blue_diamond:

Put the **Volumetric Clouds** actor in the **Lighting** folder. Now we will get into more detail on how to alter the cloud cover.  This basic actor has two major elements we can change.  The height the clouds start at and how high they extend into the sky.  If we go up in the air it is a bit more appraent what is happening here. You can adjust the **Layer Bottom Altitude** in kilometers which is how far from the ground do the clouds start.  You can also adjust the **Layer Height** which is how high in kilometers to the clouds extend from the prior starting point.

![](../images/line2.png)

##### `Step 7.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 8.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 9.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 10.`\|`ITL`| :large_blue_diamond:

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 11.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: 

![alt_text](images/.png)

![](../images/line2.png)


##### `Step 12.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 13.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 14.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 15.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: 

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 16.`\|`ITL`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 17.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 18.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 19.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 20.`\|`ITL`| :large_blue_diamond: :large_blue_diamond:

![alt_text](images/.png)

![](../images/line2.png)

##### `Step 21.`\|`ITL`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

![alt_text](images/.png)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - ADD NEXT TITLE"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../)| [home](../README.md#user-content-ue5-lighting) | [next](../)|
|---|---|---|
