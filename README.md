# simple-bot-to-bot CoCo Skill

Bot Framework v4 Skills CoCo sample.

This bot has been created using [Bot Framework](https://dev.botframework.com), it shows how to create a simple RootBot that sends message activities to a SkillBot which cocoes back the text.

## Prerequisites

- [Python SDK](https://www.python.org/downloads/) min version 3.6
- [Bot Framework Emulator](https://github.com/microsoft/botframework-emulator)

## Key concepts in this sample

The solution includes a parent bot (`simple-root-bot`) and a skill bot (`coco-skill-bot`) and shows how the parent bot can post activities to the skill bot.

- `simple-root-bot`: this project shows how to consume an coco skill and includes:
  - A [RootBot](simple-root-bot/bots/root_bot.py) that calls the coco skill and keeps the conversation active until the user says "end" or "stop". [RootBot](simple-root-bot/bots/root_bot.py) also keeps track of the conversation with the skill and handles the `EndOfConversation` activity received from the skill to terminate the conversation
  - A simple [SkillConversationIdFactory](simple-root-bot/skill_conversation_id_factory.py) based on an in memory dictionary that creates and maintains conversation IDs used to interact with a skill
  - A [SkillsConfiguration](simple-root-bot/config.py) class that can load skill definitions
  - An [AllowedSkillsClaimsValidator](simple-root-bot/authentication/allowed_skills_claims_validator.py) class that is used to authenticate that responses sent to the bot are coming from the configured skills
  - An [app.py](simple-root-bot/app.py) class that shows how to create the different skill components. This file also creates a `SkillHandler` and `aiohttp_channel_service_routes` which are used to handle responses sent from the skills
- `coco-skill-bot`: this project shows a simple coco skill that receives message activities from the parent bot and cocoes what the user said. This project includes:
  - A sample [CoCoBot](coco-skill-bot/bots/coco_bot.py) that shows how to send `EndOfConversation` based on the message sent to the skill and yield control back to the parent bot
  - A sample [AllowedCallersClaimsValidator](coco-skill-bot/authentication/allowed_callers_claims_validator.py) that shows how validate that the skill is only invoked from a list of allowed callers
  - A [sample skill manifest](coco-skill-bot/wwwroot/manifest/cocoskillbot-manifest-1.0.json) that describes what the skill can do



## To try this sample

- Clone the repository

    ```bash
    git clone https://github.com/microsoft/botbuilder-samples.git
    ```

- Create a bot registration in the azure portal for the `coco-skill-bot` and update [coco-skill-bot/config.py](coco-skill-bot/config.py) with the `MicrosoftAppId` and `MicrosoftAppPassword` of the new bot registration
- Create a bot registration in the azure portal for the `simple-root-bot` and update [simple-root-bot/config.py](simple-root-bot/config.py) with the `MicrosoftAppId` and `MicrosoftAppPassword` of the new bot registration
- Update the `SKILLS.app_id` in [simple-root-bot/config.py](simple-root-bot/config.py) with the `MicrosoftAppId` for the skill you created in the previous step
- (Optionally) Add the `simple-root-bot` `MicrosoftAppId` to the `AllowedCallers` comma separated list in [coco-skill-bot/config.py](coco-skill-bot/config.py)

## Running the sample

- In a terminal, navigate to `samples\python\80.skills-simple-bot-to-bot\coco-skill-bot`

    ```bash
    cd samples\python\80.skills-simple-bot-to-bot\coco-skill-bot
    ```

- Activate your desired virtual environment

- Run `pip install -r requirements.txt` to install all dependencies

- Run your bot with `python app.py`

- Open a **second** terminal window and navigate to `samples\python\80.skills-simple-bot-to-bot\simple-root-bot`

    ```bash
    cd samples\python\80.skills-simple-bot-to-bot\simple-root-bot
    ```

- Activate your desired virtual environment

- Run `pip install -r requirements.txt` to install all dependencies

- Run your bot with `python app.py`


## Testing the bot using Bot Framework Emulator

[Bot Framework Emulator](https://github.com/microsoft/botframework-emulator) is a desktop application that allows bot developers to test and debug their bots on localhost or running remotely through a tunnel.

- Install the Bot Framework Emulator version 4.7.0 or greater from [here](https://github.com/Microsoft/BotFramework-Emulator/releases)

### Connect to the bot using Bot Framework Emulator

- Launch Bot Framework Emulator
- File -> Open Bot
- Enter a Bot URL of `http://localhost:3978/api/messages`, the `MicrosoftAppId` and `MicrosoftAppPassword` for the `simple-root-bot`

## Deploy the bots to Azure

To learn more about deploying a bot to Azure, see [Deploy your bot to Azure](https://aka.ms/azuredeployment) for a complete list of deployment instructions.
