# FA24-WitcherS-GundlingS
Sequoia Gundling
Stephanie Witcher
CS 310H-001
23 October 2024
README Homework One
Play Through video: https://youtu.be/05-6IGNMYTE 
BluePrints video: https://youtu.be/kv_Th4TVTU8 
GitHub link: https://github.com/csu-hci-projects/FA24-WitcherS-GundlingS 
Responsibilities
Stephanie:
	I had the task of implementing the health, ammo, and hazards. I first used the lab videos to do the functionality of the ammo count. I created a user interface that showed “AMMO: #” and “Heath: #” on the user’s screen. In the first person weapon component I added the decreasing ammo functionality. This caused the number of ammo to be reduced by one with every shot. This appeared on screen through the user interface and bindings. I then added ammo pickups by creating an actor object. This object, when collided with, increments the ammo count which again updates on the screen. I then worked on hazards and health. I used a YouTube video from Jet Dev to learn about the Apply Damage function. If an object is collided with, damage is applied to the first person character. This then affects the first person blueprint by decreasing the health count by the event of any damage. This is again updated in the user interface using bindings. If the health reaches zero or below then the current level is restarted with the load level blueprint. The health pickups were similar to the ammo pickups except they now affect the current health variable. 

Sequoia: 
I had the task of creating the menu screen UI, and implementing the targets as well as the level transfers. I watched a video on youtube for essentially everything I did, but the screen transfers I figured out how to do on my own. I created a user interface with a play and an exit button that both work. When the menu screen is on the game behind it is paused and when Play is clicked, the game can be played. Then for the targets I used a Can from a western package cited below and attached a Target Blueprint to it that has a UI along with a Health Bar to see the cans health. I decided to have each shot take away 50% damage. Then once the cans are destroyed they disappear. Through the creation of the targets I learned about level functionality along with Events in the event graph. This made it relatively easy to make comparisons of the number of cans along with the number of cans in the level destroyed. I did this with another blueprint CanCounter. Then in the event that the CanCounter = 0, the next level loads. I decided to have the play screen reappear in the instances that a Player didn't want to play the second level so they could quit the game.     

How the Application Works 
	The first thing you see in the game is the main menu. The main menu BP is a widget over the levels with two buttons and text over the buttons so that during implementation OnClicked could be utilized. For the exit condition the nodes are in the MainMenu_widget event graph where Onclicked the game is quit. Then the start button is implemented on the first person BP graph. The event BeginPlay is used to create the main menu widget which is fed from the main menu widget and then set and passed to the viewport. Then the link is passed to pause the game character and set it to UI only. Then the UI only sets the main menu to focus and activate the mouse, through getController. Then on Clicked the game is started and all the widgets are removed, the mouse cursor is deactivated and the game is set to game only. Then the ammo and health widget is  linked in after the game is unpaused.
The Main user interface widget, for health and ammo, is done with a canvas panel, horizontal boxes, and text boxes. The health starts at 100 and the ammo count starts at zero. This is so you must acquire an ammo pickup before the first person weapon will allow firing. These look like the weapon projectile so the player knows what the ammo pick up is. When firing the first person weapon, the ammo count will decrease by one. This is done in the first person weapon component. Each fire will decrement the ammo count and update the count. This appears on the screen through the user interface widget and binding. The game also includes ammo pickups so the player can continue firing. These pickups are activated on overlap and increase the ammo count by the pickup count, which is how much each pickup is worth. It adds ten to the ammo for every pickup. 
The hazards are implemented on the event actor overlap. Each spike will apply damage to the first person character. The base damage amount is 10. In the first person character blueprint, using the Event Any Damage to see if the player has been harmed, the damage is applied to the player health and updated in the event graph of the User Interface “MainUI” widget and the health binding. For first person character blueprint, the same execution checks to see if the health is less than or equal to zero. If the damage causes the health count variable to change to zero or below, GetCurrent level is called to get the current level and restarts the game to that level. In addition, there are also health pickups marked with a gold material. This pickup starts with the event actor overlap. It then checks the current health to make sure it does not exceed 100. Then it adds 10 to the current health and sets that number to the current health. 
For the targets a targetBP widget was implemented that included a progress bar and max health/current health percentage. Then on the target BP we used the event BeginPlay where we casted to the targetBP widget that we got from the widget that was added to the components of the blueprint. Then we created a current health and max health variable that were set to the widgets currentHealth and MaxHealth text. To implement damage the Event hit was used where 0.5 damage was applied to the target. Then in the event of damage, it is multiplied by 100 to get a percent and subtracted that percent from the current health. Then we used the set node to update the health from the targetHealth. Then a boolean branch is called if the current health was <= 0. In this event the spawn emitter gets the default scene root and then delays and deletes the actor. Later decrease can counter was added to the target blueprint to feed the CanCounter blueprint to load the next level.
Cancount is an empty mesh blueprint present in the levels with the targets. This is implemented with a decrementer “Decrease Can Counter”. The Targets make this call before they self-destruct so that the can counter can keep track of the cans that are deleted. Once the amount of cans is decremented to 0, the next level loads, or the game ends.


References:

Link to health and hazard video: https://www.youtube.com/watch?v=iUsZrBfWEIQ
Link for Main Menu https://www.youtube.com/watch?v=g15DNCM5Aoo
Link for Targets https://www.youtube.com/watch?v=uI5ps5DbFgI

|Meeting Dates| Time | In Progress| Completed |
|:------------:|:-----------:|:------------:|:-----------:|
| 10/13/24 | 11:30-12:30| Github Set Up | Project Review / Breakdown |
| 10/14/24 | 5:00-6:00 | Menu / Level 1 | Github Set Up |
| 10/21/24 | 6:00-9:00 | Ammo Count and Pickup / Level Design | Project Planning / Menu |
| 10/22/24 | 7:00-9:00 | Level Design / Target Health | Ammo Count and Pickup / Level Design |
| 10/23/24 | 8:00-10:00 | Health and Hazards / Load Next Level | Pickups / Target Health |
| 10/26/24 | 3:00-4:00 | Video / Scripts / ReadME | Health Hazards and Load Level |
| 10/28/24 | 5:00-6:00 | Scripts / Video | README |
| 10/30/24 | 4:00 - 5:00 | Submission | Video |

