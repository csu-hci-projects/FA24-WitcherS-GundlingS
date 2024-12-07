Sequoia Gundling
Stephanie Witcher
CS 310H-001
5 December 2024
README Homework 2
Homework2 GitHub Repo Stephcw/csu-cs310h-HW2
Play Through Video: https://youtu.be/UwyAp4WbnLU 
BluePrints Video: https://youtu.be/UVqai4RcDwQ 
GitHub Link: https://github.com/csu-hci-projects/FA24-WitcherS-GundlingS

How the Application Works
	To run our application you will need the virtual reality head mounted display. This game is in the VRGameMode and contains the VR pawn to use within the game. The teleportation zone is created through a nav mesh bound volume. This is added to the project then stretched around the level floor so teleportation can be enabled. The player can now move around freely and go to other objects.

The grabbable objects were quite simple. We first created a new blueprint actor, then added a static mesh on top of it. We chose to use meshes that one would find underwater. We chose a pearl, a statue, and a trident. The trident mesh came from the Fab Asset store. Then we checked the simulated physics box so when the object was thrown it did not defy gravity. 

For the VR pistol we first copied the basic pistol from the starter content. The implementation for the ammo count and reload was based on the Lab 5 video made by Brenden. We first updated the pistol to have a spatial UI displayed. This UI kept track of the ammo count and decreased when the pistol shot. The text render is applied to the pistol so the number of ammo can be shown on the pistol itself. The ammo count starts at 15. In the event graph of the ammo pistol we implemented the decrement. We first add an ammoCount variable to keep track of how much ammo we currently have. We then check if the ammoCount is greater than zero, if it is we decrement the ammoCount and update the text render for the spatial UI. On EventBeginPlay we set up the text render in the event graph of the pistol so it will show when the pistol is picked up.
For the reload function I had to create a new input in project settings. This allowed us to have an event for that specific button push. On the push the ammo count was reset to 15. The text render is also reset to 15. In between the input press and the ammoCount reset we added a time delay of 2 seconds. The knowledge to use this node can be found from the YouTube video stated below. After the reload completes then a sound from the 2d audio. This also came from a YouTube video listed below. The gun then had to have an audio listener to recognize the explosion sound.              

	The way that the targets work is based on the Lab4VR video. Essentially I create an event Overlap that casts to a projectile to start the event when the collision is a projectile. On the first collision I change the material to red while incrementing a variable hit count. This is so on the second collision I can call Destroy Target with a branch. The branch’s conditions are based on whether the hits are greater than 1. Then, if true, Target Destroyed is called.

I use Destroy target for the Navigation Modifier where after the first target is destroyed, the locked area becomes navigable again. The Navigation modifier is just an object in the class that prevents the player from navigating to that area. I set this up by changing the project settings runtime to Display Modifiers. 

I also created a Kill count that is called in my shark target. This keeps track of the number of targets with a call to all instances of the class. In addition, it has a variable num Targets that is decremented by each target being destroyed. The main reason I created this was for my UI count in my KillCount_UI. This takes the number of targets which at the start should be 5, then continuously subtracts the number of targets based on the number of targets being reduced. This is then printed as a formatted string onto the UI for level one. I also use the KillCounter to load the next level once all the targets in the level are destroyed.

For the win screen, the base was similar to the HW1 UI. I used a canvas panel, horizontal box, and text box to have the writing “You Win” appear on screen. However, this was not as simple as setting it up on the player even graph. We had to create a new blueprint actor that would help display the UI on the VR screen. This actor has the widget attachment and the WinUI widgetBlueprint was able to bind to it. In the win level, we decorated with pillars, sparklers, and a red carpet.  

Responsibilities
Stephanie: 
I had the responsibility of setting up the project. I started a new VR project and set the game mode to the VRGameMode. I also added the surrounding teleportation area in the level. This made it so our player could move all around the area to explore and shoot targets. I also had the responsibility of adding the three grabbable objects. These simulate both gravity and physics. They made the game more interesting. I added them as a “pearl”, a stone statue, and a broken trident to match with the underwater theme. Since Sequoia did lab 5 which dealt with the VR pistol and reload I decided to do that implementation for homework 2. I added UI to the pistol to show the ammo count. Then when the pistol shot I decreased the count. When the pistol reached zero the gun stopped firing. Then I followed the provided videos to add the reload function. I also created the win level and added the WinUI to the screen upon entry to the level.

Sequoia:
I had the responsibility of creating the targets, the NavMesh and the kill count display. On Top of that I worked on creating the load win level after the targets were destroyed. I did the targets by watching the provided video from Lab4(3)VR. In addition to the video I figured out how to create a separate branch to change color on the first hit and only destroy the target after the second hit. I decided to use a shark actor in order to match the underwater theme we were going for. For the Nav Modifier volume I put it around my targets and had it become a nav area once the first target was destroyed. Then in order to create the kill count display I needed to add in a kill counter to keep track of all the targets destroyed. I then decremented the amount of targets each time a target was destroyed, and once it reached 5, the win level loaded.

References:
Link for Delay Reload https://youtu.be/RCuqjo5W2m0?si=3btskWQKXCLH_XOc 
Link for Sound Reload https://youtu.be/A53GL_5PuaM?si=BJlFNTVqJSDf7ahK
Link for WinUI https://youtu.be/H5nVjSwM_Uk?si=hzl9e7g-VdGx81b7

Meeting Dates 
Wednesday 11/27 5:30 PM
Friday 11/29 2:20 PM
Wednesday 12/4 3 PM
Thursday 12/5 10 AM & 5 PM
Friday 12/6 1:30 PM
 
