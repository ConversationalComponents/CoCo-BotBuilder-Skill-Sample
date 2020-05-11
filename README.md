# simple-bot-to-bot CoCo Skill

Bot Framework v4 Skills CoCo Skill sample.

A CoCo skill provides the ability to use conversational components dynamically
through our universal skill. 

## Prerequisites

- [Python SDK](https://www.python.org/downloads/) min version 3.6
- [Bot Framework Emulator](https://github.com/microsoft/botframework-emulator)


## Testing the bot using Bot Framework Emulator

[Bot Framework Emulator](https://github.com/microsoft/botframework-emulator) is a desktop application that allows bot developers to test and debug their bots on localhost or running remotely through a tunnel.

- Install the Bot Framework Emulator version 4.7.0 or greater from [here](https://github.com/Microsoft/BotFramework-Emulator/releases)

### Connect to the bot using Bot Framework Emulator

- Launch Bot Framework Emulator
- File -> Open Bot
- Enter a Bot URL of `http://localhost:3978/api/messages`, the `MicrosoftAppId` and `MicrosoftAppPassword` for the `simple-root-bot`

## Deploy the bots to Azure

To learn more about deploying a bot to Azure, see [Deploy your bot to Azure](https://aka.ms/azuredeployment) for a complete list of deployment instructions.
