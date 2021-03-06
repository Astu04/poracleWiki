---
title: Customize Alarm Messages
nav_order: 7
layout: default
parent: v4
---

# Custom Messages

## dts.json

All alarm messages can be customized via the `./config/dts.json` file.  

A useful visualizer can be found [HERE](https://leovoel.github.io/embed-visualizer/) 

Sometimes it's necessary to use three curly braces on each side. This avoids url encoding for fields that need an url. You can do all kinds of fancy handlebar magic, read more about that [HERE][https://github.com/helpers/handlebars-helpers].

### Monster alarms
{% raw %}
```json
{
    "id": 1,
    "type": "monster",
    "default": true,
    "platform": "discord",
    "template": {
      "embed": {
        "color": "{{ivcolor}}",
        "title": "{{round iv}}% {{name}} cp:{{cp}} L:{{level}} {{atk}}/{{def}}/{{sta}} {{boostemoji}}",
        "description": "End: {{time}}, Time left: {{tthm}}m {{tths}}s \n {{addr}} \n quick: {{quickMove}}, charge {{chargeMove}} \n Maps: [Google]({{{mapurl}}}) | [Apple]({{{applemap}}})",
        "thumbnail": {
          "url": "{{{imgUrl}}}"
        }
      }
    }
  },
```

For monsters without IV information, you can specify a different message.

```json
{
    "id": 1,
    "type": "monsterNoIv",
    "default": true,
    "platform": "discord",
    "template": {
      "embed": {
        "color": "{{color}}",
        "title": "?% {{name}} {{boostemoji}}",
        "description": "Ends: {{time}}, Time left: {{tthm}}m {{tths}}s \n {{addr}} \n Maps: [Google]({{{mapurl}}}) | [Apple]({{{applemap}}})",
        "thumbnail": {
          "url": "{{{imgUrl}}}"
        }
      }
    }
  },
```


Any of the fields can be customized with the following:

| Option        | Value         | 
| --------------- |:-------------:|
|{{id}}| Pokemon Id|
|{{name}}| Monsters name|
|{{time}}| Disappear time|
|{{tthh}}| Full hours until hidden|
|{{tthm}}| Full minutes until hidden|
|{{tths}}| Full seconds until hidden|
|{{verified}}| True/False if disappear timestamp is verified|
|{{now}}| Current Timestamp|
|{{latitude}}| Latitude of the alerted location|
|{{longitude}}| Longitude of the alerted location|
|{{addr}}| Address of the alerted location|
|{{streetNumber}}| Street number of the alerted location|
|{{streetName}}| Street name of the alerted location|
|{{zipcode}}| Zip code of the alerted location|
|{{country}}| Country of the alerted location|
|{{countryCode}}| 2 letter country code of the alerted location|
|{{city}}| City name of the alerted location|
|{{state}}| State name of the alerted location|
|{{stateCode}}| 2 letter state code of the alerted location|
|{{neighbourhood}}| Neighbourhood of the alerted location|
|{{quickMove}}| Monsers quick move (alt: {{moveName move_1}} )|
|{{chargeMove}}| Monsters charge move (alt: {{moveName move_2}} )|
|{{move1emoji}}| Monsers quick move type emoji|
|{{move2emoji}}| Monsters charge move type emoji|
|{{iv}}| Monsters Individual Value Precentage|
|{{cp}}| Monsters CP|
|{{genderData.emoji}}| Monsters gender emoji|
|{{weight}}| Monsters weight|
|{{level}}| Monsters level|
|{{atk}}| Monsters attack|
|{{def}}| Monsters defense|
|{{sta}}| Monsters stamina|
|{{weight}}| Monsters weight in kilograms|
|{{{staticmap}}}| Static link to map|
|{{{mapurl}}}|Link to google maps search of the location|
|{{{imgUrl}}}| Link to monsters picture|
|{{formName}}| Monsters form|
|{{color}}| Color to be used for embed (Color of monsters primary type)|
|{{ivcolor}}| Color to be used for embed (Color of monsters perfection based on config.discord.iv_colors)|
|{{boost}}| Monsters weather boost name|
|{{boostemoji}}| Monsters weather boost emoji)|
|{{gif}}| Gif image using pokemon-gif|
|{{{pokemoji}}}| Custom Emoji of the pokemon if defined in config/emoji.json|
|{{flagemoji}}|Country flag emoji for location|
|{{areas}}| Matched geofence area names for alert|


### Raid alarms

```json
  {
    "id": 1,
    "type": "raid",
    "default": true,
    "platform": "discord",
    "template": {
      "embed": {
        "title": "Raid against {{name}} has started at {{gymName}}!",
        "description": "CP: {{cp}}, quick: {{quickMove}}, charge {{chargeMove}} \n Maps: [Google]({{{mapurl}}}) | [Apple]({{{applemap}}})",
        "color": "{{color}}",
        "thumbnail": {
          "url": "{{{imgUrl}}}"
        },
        "author": {
          "name": "{{name}} lvl{{level}}. End: {{time}} in {{tthm}}m {{tths}}s",
          "icon_url": "{{{detailsurl}}}"
        }
      }
    }
  },
```

| Option        | Value         | 
| --------------- |:-------------:|
|{{id}}| Pokémon id|
|{{name}}| Monsters name|
|{{time}}| Disappear time|
|{{tthh}}| Full hours until raid ends|
|{{tthm}}| Full minutes until raid ends|
|{{tths}}| Full seconds until raid ends|
|{{now}}| Current Timestamp|
|{{latitude}}| Latitude of the alerted location|
|{{longitude}}| Longitude of the alerted location|
|{{addr}}| Address of the alerted location|
|{{streetNumber}}| Street number of the alerted location|
|{{streetName}}| Street name of the alerted location|
|{{zipcode}}| Zip code of the alerted location|
|{{country}}| Country of the alerted location|
|{{countryCode}}| 2 letter country code of the alerted location|
|{{city}}| City name of the alerted location|
|{{state}}| State name of the alerted location|
|{{stateCode}}| 2 letter state code of the alerted location|
|{{neighbourhood}}| Neighbourhood of the alerted location|
|{{quickMove}}| Monsters quick move|
|{{chargeMove}}| Monsters charge move|
|{{move1emoji}}| Monsters quick move type emoji|
|{{move2emoji}}| Monsters charge move type emoji|
|{{cp}}| Raid boss cp|
|{{cp20}}| Monsters cp with 100% perfect IV and level 20|
|{{cp25}}| Monsters cp with 100% perfect IV and level 25|
|{{mincp20}}| Monsters cp with 0% perfect IV and level 20|
|{{mincp20}}| Monsters cp with 0% perfect IV and level 25|
|{{level}}| Raid level|
|{{gymName}}| Name of the gym|
|{{teamName}}| Team owner of the gym |
|{{description}}| Description of the gym|
|{{{detailsurl}}}| Descriptive picture url|
|{{{staticmap}}}| Static link to map|
|{{{mapurl}}}|Link to google maps search of the location|
|{{{imgUrl}}}| Link to monsters picture|
|{{color}}| Color to be used for embed (Color of monsters primary type)|
|{{ex}}| If raid takes place in a potential EX gym (empty string if false)|
|{{#ex}}True{{/ex}}{{^ex}}False{{/ex}}| Prints True if ex eligible, False if not|
|{{gif}}| Gif image using pokemon-gif|
|{{flagemoji}}|Country flag emoji for location|
|{{{pokemoji}}}|Custom emoji for the award pokemon as set in config/emoji.json|
|{{areas}}| Matched geofence area names for alert|


### Egg alarms

```json
 {
    "id": 1,
    "type": "egg",
    "default": true,
    "platform": "discord",
    "template": {
      "embed": {
        "title": "Raid egg level{{level}} at {{gymName}}",
        "description": "Maps: [Google]({{{mapurl}}}) | [Apple]({{{applemap}}})",
        "color": "{{color}}",
        "thumbnail": {
          "url": "{{{detailsurl}}}"
        },
        "author": {
          "name": "Hatch at: {{time}} in {{tthm}}m {{tths}}s",
          "icon_url": "{{{imgUrl}}}"
        }
      }
    }
  },
```



| Option        | Value         | 
| --------------- |:-------------:|
|{{time}}| Disappear time|
|{{tthh}}| Full hours until raid ends|
|{{tthm}}| Full minutes until raid ends|
|{{tths}}| Full seconds until raid ends|
|{{now}}| Current Timestamp|
|{{addr}}| Address of the alerted location|
|{{latitude}}| Latitude of the alerted location|
|{{longitude}}| Longitude of the alerted location|
|{{streetNumber}}| Street number of the alerted location|
|{{streetName}}| Street name of the alerted location|
|{{zipcode}}| Zip code of the alerted location|
|{{country}}| Country of the alerted location|
|{{countryCode}}| 2 letter country code of the alerted location|
|{{city}}| City name of the alerted location|
|{{state}}| State name of the alerted location|
|{{stateCode}}| 2 letter state code of the alerted location|
|{{neighbourhood}}| Neighbourhood of the alerted location|
|{{gymName}}| Name of the gym|
|{{teamName}}| Team owner of the gym |
|{{description}}| Description of the gym|
|{{level}}| Raid level|
|{{{detailsurl}}}| Descriptive picture url|
|{{{staticmap}}}| Static link to map|
|{{{mapurl}}}|Link to google maps search of the location|
|{{{imgUrl}}}| Link to monsters picture|
|{{color}}| Color to be used for embed (Color of monsters primary type)|
|{{ex}}| If raid takes place in a potential EX gym (empty string if false|
|{{#ex}}True{{/ex}}{{^ex}}False{{/ex}}| Prints True if ex eligible, False if not|
|{{flagemoji}}|Country flag emoji for location|


### Quest alarms

```json
  {
    "id": 1,
    "type": "quest",
    "default": true,
    "platform": "discord",
    "template": {
      "embed": {
        "title": "{{questType}} \n Pokestop Name: {{pokestop_name}}",
        "url": "{{{mapurl}}}",
        "description": "Conditions: {{conditionString}} \n Reward: {{rewardString}} {{monsterNames}} \n {{addr}} \n Maps: [Google]({{{mapurl}}}) | [Apple]({{{applemap}}})",
        "thumbnail": {
          "url": "{{{imgUrl}}}"
        }
      }
    }
  },
```



| Option        | Value         | 
| --------------- |:-------------:|
|{{now}}| Current Timestamp|
|{{questType}}| The type of quest (for example: battle in 3 raids)|
|{{quest_task}}| Exact text of the Quest (MAD only)|
|{{conditionString}}| Extra conditions (for example: you must win these battles)|
|{{rewardString}}| Reward if you finish (Pokemon, item or stardust)|
|{{monsterNames}}| Names of all reward monsters for this quest|
|{{itemNames}}| Names of all reward Items for this quest|
|{{stardust}}| The word "stardust" if it's that type of quest|
|{{{imgUrl}}}| Image of the reward. Could be Pokemon or Item or stardust|
|{{pokestop_name}}| Name of the Pokestop|
|{{{rewardemoji}}}| emoji for the reward|
|{{url}}| Link to the image of the Pokestop|
|{{minCp}}| Minimum CP of the reward pokemon|
|{{maxCp}}| Maximum CP of the reward pokemon|
|{{{staticmap}}}| Static link to map|
|{{{mapurl}}}| Link to google maps|
|{{{applemap}}}| Link to apple maps|
|{{areas}}| Matched geofence area names for alert|
|{{latitude}}| Latitude of the alerted location|
|{{longitude}}| Longitude of the alerted location|
|{{streetNumber}}| Street number of the alerted location|
|{{streetName}}| Street name of the alerted location|
|{{zipcode}}| Zip code of the alerted location|
|{{country}}| Country of the alerted location|
|{{countryCode}}| 2 letter country code of the alerted location|
|{{neighbourhood}}| Neighbourhood of the alerted location|
|{{city}}| City name of the alerted location|
|{{state}}| State name of the alerted location|
|{{stateCode}}| 2 letter state code of the alerted location|
|{{flagemoji}}|Country flag emoji for location|

### Invasion alarms

```json
  {
    "id": 1,
    "type": "invasion",
    "default": true,
    "platform": "discord",
    "template": {
      "embed": {
        "title": "Team Rocket at {{name}}!",
        "url": "{{{mapurl}}}",
        "description": "Name: {{gruntName}} {{genderName}} \n Type: {{gruntType}} {{gruntTypeEmoji}} \n Possible Rewards: {{gruntRewards}} \n Ends: {{time}}, in {{tthm}}m {{tths}}s \n Maps: [Google]({{{mapurl}}}) | [Apple]({{{applemap}}})",
        "thumbnail": {
          "url": "{{{imgUrl}}}"
        }
      }
    }
  },
```


| Option        | Value         | 
| --------------- |:-------------:|
|{{time}}| Invasion end time|
|{{tthh}}| Full hours until invasion ends|
|{{tthm}}| Full minutes until invasion ends|
|{{tths}}| Full seconds until invasion ends|
|{{now}}| Current Timestamp|
|{{gruntName}}| The name of the grunt (grunt female or grunt male)|
|{{gruntType}}| The type of invasion (for example: Rock, Mixed|
|{{gruntTypeEmoji}}| The emoji of type of invasion|
|{{gruntRewards}}| If known, a list of possible rewards. Splits into 2 lines if there's a 85/15 split chance of reward.|
|{{gruntRewardsList}}| A list of possible rewards containing chance, id and name|
|{{gruntTypeColor}}| The color code matching the grunt invasion type|
|{{genderName}}| The gender name or gender emoji of the grunt|
|{{gruntTypeId}}| The id of the invasion type|
|{{gender}}| The id of the grunt gender|
|{{name}}| Name of the Pokestop|
|{{{imgUrl}}}| alias for Link to the image of the Pokestop|
|{{url}}| Link to the image of the Pokestop|
|{{{staticmap}}}| Static link to map|
|{{{mapurl}}}| Link to google maps|
|{{{applemap}}}| Link to apple maps|
|{{areas}}| Matched geofence area names for alert|
|{{latitude}}| Latitude of the alerted location|
|{{longitude}}| Longitude of the alerted location|
|{{streetNumber}}| Street number of the alerted location|
|{{streetName}}| Street name of the alerted location|
|{{zipcode}}| Zip code of the alerted location|
|{{country}}| Country of the alerted location|
|{{countryCode}}| 2 letter country code of the alerted location|
|{{neighbourhood}}| Neighbourhood of the alerted location|
|{{city}}| City name of the alerted location|
|{{state}}| State name of the alerted location|
|{{stateCode}}| 2 letter state code of the alerted location|
|{{flagemoji}}|Country flag emoji for location|


### Weather

```json
  {
    "id": 1,
    "type": "weatherchange",
    "default": true,
    "platform": "discord",
    "template": {
      "embed": {
        "title": "Weather change!",
        "description": "NB! The weather for some active mons have changed from {{oldweather}} {{oldweatheremoji}} to {{weather}} {{weatheremoji}}!\nThis could have altered the reported IV!"
      }
    }
  },
```


| Option        | Value         | 
| --------------- |:-------------:
|{{latitude}}| Latitude of the alerted location|
|{{longitude}}| Longitude of the alerted location|
|{{oldweather}}| Weather of the past hour|
|{{oldweatheremoji}} Weatheremoji of the past hour|
|{{weather}}| Weather of the current hour|
|{{weatheremoji}} Weatheremoji of the current hour|

### Greeting Message

```json
  {
    "id": 1,
    "type": "greeting",
    "default": true,
    "platform": "discord",
    "template": {
      "embed": {
        "title": "Welcome",
        "description": "Thank you for registering \nPlease set a location `{{prefix}}location name of place` or add ares where to receive alarms from",
        "fields": [
          {
            "name": "General commands",
            "value": "`{{prefix}}poracle`: Adds you to database and enables tracking \n`{{prefix}}unregister`: Removes you from tracking \n`{{prefix}}stop`: Temporarily stops alarms \n`{{prefix}}start`: Re-enables alarms \n`{{prefix}}location yourArea`: Searches for yourArea and sets it as your location \n`{{prefix}}area add somePlace`: Sets one or multiple areas where to receive alarms from, areas need to be configured by admin \n`{{prefix}}area remove somePlace`: Removes a configured area"
          },
          {
            "name": "Monster tracking commands",
            "value": "`{{prefix}}track snorlax lapras d500 iv50 maxiv90 cp1000 level15`: Any arguments are optional, this command would alert you about snorlax and lapras within 500 meters of your location or inside an added area. The set filters require them to have IV between 50% - 90% be at least level 15 and minimum CP of 1000 \n`{{prefix}}untrack lapras vileplume`: will remove tracking for lapras and vileplume"
          },
          {
            "name": "Raid tracking commands",
            "value": "`{{prefix}}raid snorlax lapras d500 instinct`: Any arguments are optional, this command would alert you about snorlax and lapras raids within 500 meters of your location or inside an added area. The set filters require the Gym to be controlled by team Instinct \n`{{prefix}}raid remove lapras vileplume`: will remove tracking for lapras and vileplume raids"
          },
          {
            "name": "Raid egg tracking commands",
            "value": "`{{prefix}}egg level3 d500 instinct`: Any arguments are optional, this command would alert you about level 3 raid eggs within 500 meters of your location or inside an added area. The set filters require the Gym to be controlled by team Instinct \n`{{prefix}}egg remove level3`: will remove tracking for level 3 raid eggs"
          },
          {
            "name": "Quest tracking commands",
            "value": "`{{prefix}}quest porygon pikachu poke ball d500 `: Any arguments are optional, this command would alert you about Quests obtainable within 500m of your location with porygon, pikachu or pokeballs as rewards \n `{{prefix}}quest remove all items` Removes tracking for all item based quests. Can also use `all pokemon` or `stardust`"
          },
          {
            "name": "Invasion tracking commands",
            "value": "`{{prefix}}invasion template3 d500 dragon mixed`: Any arguments are optional, this command would alert you about Team Rocket Incidents within 500m of your location if the grunt type was mixed or dragon. You can use any pokemon type name.\n `{{prefix}}invasion remove` Removes tracking for all Team Rocket Incidents."
          }
        ]
      }
    }
  }
```
{% endraw %}
This is the message that is sent to newly added users via DM. There are no dynamic variables in this message.  

The "fields" without title and description are sent to users upon `!help` command
