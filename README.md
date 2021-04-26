# NBGames - Version 4.21.1
**Pure forge** catching &amp; battling mini game for players to spend time on!

# General information
Create a grid system allowing the player to earn points with missions that you set up. These points can be used to buy slot on the grid and collect the content. All items are configurable and the generation is automatic. The player can only buy adjacent slot to his starting point (represented by his custom head) or adjancent slot of already bought slot (no diagonal). Once arrived at the destination, a new card is generated (the previous one is then lost) and the player can continue his purchases within the limits of the number of available cards (configurable). **NBGames** uses the **UUID** of the players, so the progress is not lost in case of change of nickname. ***The plugin allows you to increase the playing time considerably, it is up to you to adjust the rewards to your player base.***


# Configuration
The configuration is structured in the folder "**NBGames**" which will be created in your config folder. 
The configuration is organized in **3 main files** whose details are presented below. The players data are available in a folder that will be created and named **PlayerData**.
![image](https://user-images.githubusercontent.com/30299182/116123107-e6254300-a6c2-11eb-8723-7217f9a2c7ec.png)
## GamesInitializer.json
![image](https://user-images.githubusercontent.com/30299182/116123239-0fde6a00-a6c3-11eb-9eae-bfaed80a94e1.png)
- **ChatMenu** will display a clickable text menu with the list of available cards.
- **UIMenu** will display an UI with the list of available cards.
- **AutomaticSurnameColor** will format pokemon name with surname defined in config with the pokemon type.

![image](https://user-images.githubusercontent.com/30299182/116123495-58962300-a6c3-11eb-8bf7-11ff2cfb2b92.png)
![image](https://user-images.githubusercontent.com/30299182/116123805-c0e50480-a6c3-11eb-86e9-7754033da70a.png)
<br>
*Please note that you can configure the formats.*

### Item structure
There are 5 types of items, the first one in the list "**Common**" selects a random object in the list (**75%** chance), in the category "**Rare**" (**25%** chance). A starting item (represented by default by the **player's head**). The destination item represented by an "**Arc Chalice**". And **ONE** random item with a **100%** chance in the **Unique** list.
```json
{
    "ItemType": "pixelmon:potion",
    "Quantity": 6,
    "Meta": 0,
    "Cost": 20,
    "CustomNBT": ""
}
```
*You can change item type, quantity, meta (for color and variations), cost in point for players and custom NBT (only for the UI display).*
## GamesManager.json
This is where you can configure the maps you want. The name of the set, the permission, the color of stained glass pane once the item is purchased, the starting object, and the ending object, following the same format as described above. You also have the possibility to set the points earned, for captures and defeats. You have for each category, access to the types of pokémon ; to a list of ; and to bonuses in case of legendary / shiny pokémon. (The points are cumulative)
```json
{
	"Cards": {
		"Demo": {
			"MaxMapForPlayer": 15,
			"Permission": "nbgames.demo",
			"StainedGlassPaneCompletionColor": 11,
			"Catch": {
				"Type": {
					"Grass": 5
				},
				"Pokemon": {
					"Turtwig": 15
				},
				"Modifier": {
					"Legendary": 50,
					"Shiny": 50
				}
			},
			"Defeat": {
				"Type": {
					"Water": 5
				},
				"Pokemon": {
					"Piplup": 15
				},
				"Modifier": {
					"Legendary": 0,
					"Shiny": 0
				}
			},
			"StartItem": {
				"ItemType": "minecraft:skull",
				"Quantity": 1,
				"Meta": 3,
				"Cost": 0,
				"CustomNBT": "{SkullOwner: {PLAYER}}"
			},
			"EndItem": {
				"ItemType": "pixelmon:plateholder",
				"Quantity": 1,
				"Meta": 0,
				"Cost": 100,
				"CustomNBT": ""
			}
		}
	}
}
```
## GamesString.json
You will find in this file the list of all messages and formats used by the plugin, in order to customize the plugin to make it unique for your servers. The "Surname" category changes the description displays in the UI.

# Commands and permissions
## Player command
**/nbgames {Card}** ({Card} is optionnal.) <br>
The display depends on your previous settings. Player need only the default permission defined in the GamesManager for the followed card. If it's blank, everyone can have access to it. Take note, the player can see only cards he is allowed to see (Permission).

## Admin command
### /NBGamesPoints <Get / Add / Remove / Reset> <Player> {Amount}
  Manage player points. <br>
  Permission: ``nbgames.admin``<br>
  
### /NBGamesPoints <Get / Add / Remove / Reset> <Player> {Amount}
  Manage player points. <br>
  Permission: ``nbgames.admin``<br>
  
### /NBGamesLicence <Action>
Regarding the license, all players have access to the command ``/NBGamesLicence`` which displays the information about the current license. Admin will be able to configure this using the permission **"nbgames.licence"** (***I advise you to give this permission only to the server owner and to prefer to remove these permissions once configured.***)

#### Buy a single license / network license
For purchases please go directly to my discord, where the prices are posted. To join, simply go here: https://discord.gg/w3S9ZQf8nR
Please note that single licenses will only work for a single server. For network licenses, the IP addresses of the authorized servers on the network must be sent to the developer to be linked to your license. 

#### Activate my license
*This process is the same for single licenses as for network licenses.*
The information used here is fictituous and will not work, it is used as an example.
For our example we will use this information:<br>
**Server/Network Name**: ``MyAmazingServer``<br>
**Server/Network Key**: ``AmazServQXCegs1X16``<br>

Then use these commands in order <br>
``/NBGamesLicence ServerName MyAmazingServer``<br>
``/NBGamesLicence ServerKey AmazServQXCegs1X16``<br>
``/NBGamesLicence Connect``<br>

A success message should then be displayed. If not, check your information and contact the developer if the license is still not activated. <br>
Once this is complete, use the command "**/NBGamesLicence Ip**" and send the address to the developer to complete the process.

## Example of usage
![image](https://user-images.githubusercontent.com/30299182/116129179-1a503200-a6ca-11eb-85ae-61b7a4a9f06c.png)
The display changes if the player does not have enough to buy the slot.<br>
![image](https://user-images.githubusercontent.com/30299182/116129307-3fdd3b80-a6ca-11eb-93ea-d51b62cee6c1.png)
<br>
The points of the players are displayed in the title of the menu.<br>
When you defeat / catch a pokemon who are in points condition setup previously, player wins points, and a message is sent below inventory action bar.
![image](https://user-images.githubusercontent.com/30299182/116129681-abbfa400-a6ca-11eb-840d-f0bea371bcf4.png)
