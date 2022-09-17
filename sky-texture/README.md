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

![bring image into photoshop](images/adjustBlendRadius.png)

![](../images/line2.png)

##### `Step 4.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

https://user-images.githubusercontent.com/5504953/189629265-a132d73d-360f-47f3-9adb-431ae11c0eb1.mp4

![](../images/line2.png)

##### `Step 5.`\|`ITL`| :small_orange_diamond:


![change aspect ration to square](images/addHDRIBackdrop.png)

![](../images/line2.png)

##### `Step 6.`\|`ITL`| :small_orange_diamond: :small_blue_diamond:


![image is square ratio](images/hdriLevel.png)

![](../images/line2.png)

##### `Step 7.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Download [T_KiaraDawn.hdr](../Assets/T_KiaraDawn.hdr) and drag it into the **Textures | Supplied** folder.

![export as a png](images/tKiara.png)

![](../images/line2.png)

##### `Step 8.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:


![export as hdr](images/noMips.png)

![](../images/line2.png)

##### `Step 9.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:


![change texture in m_sky](images/.png)

![](../images/line2.png)

##### `Step 10.`\|`ITL`| :large_blue_diamond:



![add hdri to sky light](images/.png)

![](../images/line2.png)

##### `Step 11.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: 


![adjust sun to match new sky sphere](images/.png)

![](../images/line2.png)


##### `Step 12.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 


![](../images/line2.png)

##### `Step 13.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 


![save all, commit and push to github](images/.png)

| `lighting.reflections`\|`THE END`| 
| :--- |
| **That's All Folks!** Thanks for sticking around. That's it for this lesson. |


![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - HDRI and Customize Clouds"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../post-process/README.md#user-content-post-process-volumes)| [home](../README.md#user-content-ue4-lighting) | 
|---|---|
