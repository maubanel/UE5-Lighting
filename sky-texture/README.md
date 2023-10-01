![](../images/line3.png)

### Customize Clouds 

<sub>[previous](../post-process/README.md#user-content-post-process-volumes) • [home](../README.md#user-content-ue4-lighting)</sub>

![](../images/line3.png)

Lets look at customizing clouds as the default clouds don't have much customization at first glance. We have a more advanced cloud material that has more parameters to edit.

<br>

---


##### `Step 1.`\|`ITL`|:small_blue_diamond:

Now the last thing we will look at are the volumetric clouds..  Lets go to **Edit | Plugins** and add the **Volumetrics** plugin and restart the engine to load the plugin.

![add volumetrics plugin](images/Volumetrics.png)


![](../images/line2.png)

##### `Step 2.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: 

Now lets adjust the speed of the clouds movement.  Select in the **Outliner** the **Volumetric Clouds** and open up the material used **M_SimpleVolumetricCloud_Inst** by clicking on the folder next to the material. Right click on **M_SimpleVolumetricCloud_Inst** and select **Duplicate**.  Name the new material instance `MI_VolumetricCloud`.  Now we don't want to edit the one in the **Engine** folder as this will change it for every project moving forward.  We just want to affect the clouds in this one level which is why we are duplicating this texture.

![create material instance of M_SimpleVolumetricCloud_Inst](images/windVectors.png)
![](../images/line2.png)

##### `Step 3.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:


![](../images/line2.png)

##### `Step 4.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:



![](../images/line2.png)

##### `Step 5.`\|`ITL`| :small_orange_diamond:



![](../images/line2.png)

##### `Step 6.`\|`ITL`| :small_orange_diamond: :small_blue_diamond:



![](../images/line2.png)

##### `Step 7.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:



![](../images/line2.png)

##### `Step 8.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:



![](../images/line2.png)

##### `Step 9.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:



![](../images/line2.png)

##### `Step 10.`\|`ITL`| :large_blue_diamond:




![](../images/line2.png)

##### `Step 11.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: 



![](../images/line2.png)


##### `Step 12.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 



![](../images/line2.png)

##### `Step 13.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 



![](../images/line2.png)

##### `Step 14.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 



![](../images/line2.png)

##### `Step 15.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: 


![](../images/line2.png)

##### `Step 16.`\|`ITL`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

![](../images/line2.png)

##### `Step 17.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:


![](../images/line2.png)

##### `Step 18.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:



![](../images/line2.png)

##### `Step 19.`\|`ITL`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:



![](../images/line2.png)

##### `Step 20.`\|`ITL`| :large_blue_diamond: :large_blue_diamond:



![](../images/line2.png)

##### `Step 21.`\|`ITL`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

Drag and drop **MI_VolumetricCloud** in **Materials | Supplied** and select **Move Here**.

![move material to supplied folder](images/moveMIVolumetric.png)


![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - HDRI and Customize Clouds"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../post-process/README.md#user-content-post-process-volumes)| [home](../README.md#user-content-ue4-lighting) | 
|---|---|
