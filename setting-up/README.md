![](../images/line3.png)

### Setting Up

<sub>[home](../README.md#user-content-ue4-lighting) • [next](../prep/README.md#user-content-lighting-prep)</sub>

![](../images/line3.png)

We will be working with a level that has already been gray blocked and modelled. It is a finished level minus the lighting. This was created by the team at Unreal and included in their Content Example project in UE4 (they have removed it in the latest version). You will also have a first person character to move through the environment to check your work.

<br>

---

| `required.software`\|`UE5 Materials`| 
| :--- |
| :floppy_disk: &nbsp; &nbsp; You will need to install the latest version of _UE4 5.0.X_ by downloading the [Epic Games Launcher](https://www.epicgames.com/store/en-US/download). You will also need a [P4V](https://www.perforce.com/downloads/helix-visual-client-p4v) account which is free to sign up for as we will be using version control. Lets make sure you can see hidden folders. On the PC follow these [Windows 10 Turn on Hidden Folders](https://support.microsoft.com/en-us/help/4028316/windows-view-hidden-files-and-folders-in-windows-10) directions.

##### `Step 1.`\|`ITL`|:small_blue_diamond:

If you have not installed the required software go and add [Epic Games Launcher](https://www.epicgames.com/store/en-US/download), [git](https://git-scm.com/downloads) (PC only), [Github Desktop](https://desktop.github.com), [Git LFS (Large File System)](https://git-lfs.github.com) (Large File System) on your mac or PC. Make sure you have a valid GitHub account. Make sure it has a 4.26.X in front of the version so that we know this walk through will be compatible with your version of Unreal.

![software installs](images/InstallSoftware.jpg)

![](../images/line2.png)

##### `Step 2.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: 

After you accept the [GitHub Classroom](https://classroom.github.com/a/WqCC8uOJ) invitation, go to the new **GitHub** repository and click on the green Code button and select open with **GitHub Desktop** then confirm that you will open in desktop then pick a directory and press the <kbd>Clone</kbd> button.

![accept github classroom and clone project](images/githubClassroom.jpg)

![](../images/line2.png)

##### `Step 3.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:


Go to the directory in where you installed the project and open the LICENSE file in a text editor. If you want to change the type of license now is the time to do so. If you want to keep the MIT license then just replace `ENTER NAME HERE` with your legal name. Press save and quit.

![change license for project and add your name](images/changeLicense.jpg)

![](../images/line2.png)

##### `Step 4.`\|`ITL`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Edit the README.md file in a text editor and add your name and a message (in my case it is a reminder that I will complete it at the end!). 

![edit README.md and ](images/NameMessageREADME.jpg)

![](../images/line2.png)

##### `Step 5.`\|`ITL`| :small_orange_diamond:

Move the `.gitattributes` file from the **Assets** folder into the top folder that contains the **Content** folder and **.gitignore** file.

![move .gitattributes to top folder ](images/addgitattributes.jpg)



![](../images/line2.png)

##### `Step 6.`\|`ITL`| :small_orange_diamond: :small_blue_diamond:

Add a message stating change to **LICENSE**, **README.md** and **.gitattribute** files.  Press the **Commit** button.  Then press **Push** to update the change to **GitHub**.  

![commit and push to github](images/CommitAndPushInitial.jpg)

Check the repository online to see the added changes to make sure it pushed properly.

![check github for changes license, readme and gitattributes](images/InitialUpdatedGitHub.jpg)

![](../images/line2.png)

##### `Step 7.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Open up **UE4LightingStarter.uproject**. The project should load up in the Room/Level **UnlitLevel**. It should look like a pitch black room as there are no lights. Also, the game may be building the shaders. You might want to wait for all the shaders to render before moving on.

![pitch black game screen](images/blackGameScreen.jpg)

![](../images/line2.png)

##### `Step 8.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

You will also most likely see a dark room that has not been lit. To see what is going on swtich to **Unlit** mode. Next page we will start lighting the scene from scratch.

![change to unlit mode to see level](images/unlitMode.jpg)

![](../images/line2.png)

##### `Step 9.`\|`ITL`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Lets look at what is included in this project. We have a **Blocking Volumes** folder that contains invisible meshes. These are collision volumes with no visible geometry. They are used to stop players from entering areas the designer doesn't want them to go in. Press **BlockingVolume6** and press the <kbd>F</kbd> key to focus on it. Notice that is is blocking the player from jumping outside the unblocked window archways.

![added blocking volumes](images/unblockedWindows.jpg)

![](../images/line2.png)

##### `Step 10.`\|`ITL`| :large_blue_diamond:

The **Static Meshes** folder contains all the static meshes for the level.

![building meshes in world outliner](images/worldOutlinerBuildingMeshes.jpg)

![](../images/line2.png)

##### `Step 11.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: 

The **Audio** contains sound effects that you can hear in the level when you start the game and the **Environment** folder contains the ocean that we will activate shortly.

![come meshes have collision volumes](images/collisionMeshOrNot.jpg)

![](../images/line2.png)

##### `Step 12.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

The **Game Mode** loads up the **Blueprints | MyGameLDDemo** that the **PlayerStart** object launches the player in the front terrace. The **Blueprints** folder also contains **ThirdPersonCharacter** which is the **UE4** mannequin that we will control in the game. This character blueprint is the **Default Pawn** in the gamemode blueprint.

![game mode for level](images/gameMode.jpg)

![](../images/line2.png)

##### `Step 13.`\|`ITL`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Open up **Settings | Project Settings | Maps and Modes**. It will start the editor and full game in the level `Unlit Level`. This is the dark room we are in. We also have **GameModeBase** which is the default gamemode for the entire project. 

Now go into **Settings | World Settings** and expand **Game Mode**. This is overrides the settings that are in project settings for this one level. So **MyGameLDDemo** is overriding the **GameModeBase** in the project level setting.  You can see when you expand the **Selected Game Mode** that the **Default Pawn** is `ThirdPersonCharacter`. 

![room project settings](images/projectSettings.jpg)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Preparing to Start Lighting"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [home](../README.md#user-content-ue4-lighting) | [next](../prep/README.md#user-content-lighting-prep)|
|---|---|
