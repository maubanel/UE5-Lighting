![](../images/line3.png)

### Setting Up

<sub>[home](../README.md#user-content-ue4-lighting) • [next](../prep/README.md#user-content-lighting-prep)</sub>

![](../images/line3.png)

We will be working with a level that has already been gray blocked and modelled. It is a finished level minus the lighting. This was created by the team at Unreal and included in their Content Example project in UE4 (they have removed it in the latest version). You will also have a third person character to move through the environment to check your work.

<br>

---

| `required.software`\|`UE5 Lighting`| 
| :--- |
| :floppy_disk: &nbsp; &nbsp; You will need to install the latest version of _UE4 5.0.X_ by downloading the [Epic Games Launcher](https://www.epicgames.com/store/en-US/download). You will also need a [P4V](https://www.perforce.com/downloads/helix-visual-client-p4v) account which is free to sign up for as we will be using version control. Lets make sure you can see hidden folders. On the PC follow these [Windows 10 Turn on Hidden Folders](https://support.microsoft.com/en-us/help/4028316/windows-view-hidden-files-and-folders-in-windows-10) directions.

##### `Step 1.`\|`ITL`|:small_blue_diamond:

If you have not installed the required software go and add [Epic Games Launcher](https://www.epicgames.com/store/en-US/download). Make sure the version of Unreal you are installed  has a 5.0.X in its name so that we know this walk through will be compatible with your version of Unreal. This will not work in UE4.

![unreal 5 installed](images/FiveDotO.png)

![](../images/line2.png)

##### `Step 2.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: 

Make sure you have room for another 4 gigabytes (starter plus your added work) of space on your computer. Navigate to [UE5-Lighting-Starter](https://github.com/LSU-UE5/UE5-Lighting-Starter) and press the <kbd>Code Button</kbd> and select **Download ZIP**. It will take a while so try and do this on your best internet connection available to you. The file is roughly ~2 gigabytes.

![download github lighting starter project](images/downloadZip.png)

![](../images/line2.png)

##### `Step 3.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Right click on **UE5-Lighting-Starter-main.zip** and select **Extract Files...**.  A pop up with the current directory appears and you can press the <kbd>OK</kbd> button. 

![exract and renamte folder](images/unzipDownload.png)

![](../images/line2.png)

##### `Step 4.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Rename the folder from **UE5-Lighting-Starter-main** to `UE-5-Lighting`.  Drag and drop the renamed folder into your **P4 Workspace** folder.
![drag starter project into p4 workspace](images/dragFiles.png)


![](../images/line2.png)

##### `Step 5.`\|`ITL`| :small_orange_diamond:

Delete the `.gitignore` and `.gitattributes` file as they are not needed.

![delete two .git... files](images/deleteDotGit.png)

![](../images/line2.png)

##### `Step 6.`\|`ITL`| :small_orange_diamond: :small_blue_diamond:

Edit the README.md file in a text editor and add your name and a message (in my case it is a reminder that I will complete it at the end!). 

![edit README.md and ](images/changeReadme.png)

![](../images/line2.png)

##### `Step 7.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Open up P4V and log into the workspace you avhe set up for this maching. select the **UE5-Lighting** folder and press the **+ Add** button.  Select a **New** changelist and enter a message `uploading ue5 lighting starter`. Press the <kbd>OK</kbd> button.

![alt_text](images/submitToP4Initial.png)

![](../images/line2.png)

##### `Step 8.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Press the <kbd>Submit</kbd> button to send these files to the **Depot**. Enter a message `UE 5 Lighting Starter Project` then press the <kbd>Submit</kbd> on the pop up.

![submit to P4V](images/submitP4v.png)

![](../images/line2.png)

##### `Step 9.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Open up **UE5Lighting.uproject**. The project should load up in the Room/Level **UnlitLevel**. It should look like a pitch black room as there are no lights. 

![pitch black game screen](images/emptyLevel.png)

![](../images/line2.png)

##### `Step 10.`\|`ITL`| :large_blue_diamond:

You will see a dark room that has not been lit. To see what is going on swtich to **Unlit** mode. Next page we will start lighting the scene from scratch.

![change to unlit mode to see level](images/unlitMode.jpg)

Lets look at what is included in this project. We have a **Blocking Volumes** folder that contains invisible meshes. These are collision volumes with no visible geometry. They are used to stop players from entering areas the designer doesn't want them to go in. Press **BlockingVolume6** and press the <kbd>F</kbd> key to focus on it. Notice that is is blocking the player from jumping outside the unblocked window archways.

![added blocking volumes](images/unblockedWindows.jpg)

The **Static Meshes** folder contains all the static meshes for the level.

![building meshes in world outliner](images/worldOutlinerBuildingMeshes.jpg)

![](../images/line2.png)

##### `Step 11.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: 
The **Game Mode** loads up the **Blueprints | MyGameLDDemo** that the **PlayerStart** object launches the player in the front terrace. The **Blueprints** folder also contains **ThirdPersonCharacter** which is the **UE4** mannequin that we will control in the game. This character blueprint is the **Default Pawn** in the gamemode blueprint.

![](../images/line2.png)

##### `Step 12.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Open up **Settings | Project Settings | Maps and Modes**. It will start the editor and full game in the level `Unlit Level`. This is the dark room we are in. We also have **GameModeBase** which is the default gamemode for the entire project. 

Now go into **Settings | World Settings** and expand **Game Mode**. This is overrides the settings that are in project settings for this one level. So **MyGameLDDemo** is overriding the **GameModeBase** in the project level setting.  You can see when you expand the **Selected Game Mode** that the **Default Pawn** is `ThirdPersonCharacter`. 

![room project settings](images/projectSettings.jpg)

![game mode for level](images/gameMode.jpg)

![](../images/line2.png)

##### `Step 13.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 


![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Preparing to Start Lighting"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [home](../README.md#user-content-ue4-lighting) | [next](../prep/README.md#user-content-lighting-prep)|
|---|---|
