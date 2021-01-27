# AdoptBot

Adopt Bot is a user care Chatbot built with Power Virtual Agent for Teams.

Adoption Bot answers common questions about Office 365 and Teams.  If users need additional help, Adoption Bot can connect them to experts or open service tickets:
- Self-help facility to drive adoption at scale - use M365 drive adoption of M365
- Adoption Bot can be branded.  E.g. AskO365, AskMyCompanyIT
- No code Bots have quick time to value and net quick win for M365 project team
- Power Virtual Agent Bots for Teams work with Enterprise customer seeded licensing
- Solidifies and strengthens your champions network
- Drive down support costs with fewer service desk tickets*

* Use of bots to handle employee questions reduces the number of IT and HR support tickets by 10% to 15%.  Source: Forrester Consulting Total Economic Impact™ Of using Microsoft Teams as a platform and Teams with Power Platform

## Deployment Guide
Create your Dataverse for Teams environment 

You can skip this step if you already have a Dataverse for Teams environment for the team that will be managing the AdoptBot. 

1. Search for Power Virtual Agents Teams app in Microsoft Teams app store. 
Graphical user interface, application, Teams
![image](https://user-images.githubusercontent.com/54556057/106006977-cd859c80-6083-11eb-94ff-dd754dcfadbf.png)

Description automatically generated

Graphical user interface, application, Teams

Description automatically generated 

Add the app in Microsoft Teams and will land you in the homepage.  Select Start now. 

 

Select the team that will be managing the adoption bot. 

 

Wait for the Dataverse for Teams environment to be created in 30 seconds to a minute. 

Graphical user interface, application

Description automatically generated 

Once the environment is created you will be redirected to create your first bot.  You can exit out of it. 

Import the bot into your Dataverse for Teams environment 

Please follow the instruction in the previous section if you do not have a Dataverse for Teams environment created yet.  Please note that the following instruction also applies to Dataverse full environment but that will require Power Platform licenses in addition to standard Office license. 

Go to www.flow.microsoft.com and select the environment that you would like to own the bot in from the environment picker on the top right corner. 

 

Go to Solutions from the left nav menu and select Import. 

 

Select the AdoptionBotPVA package .zip file that you have downloaded from the Github repo.  Select Next. 

 

Read the summary page and select Next again.  You will be asked to provide Connection for the solution.  You can select an existing connection or create a new one by following the instruction of the menu.  Skip to step 7 if you don’t need to create a new connection. 

 

Graphical user interface, application

Description automatically generated 

Optional – create a new connection.  By selecting New connection, a new tab will be opened and select Create on the dialog.  Sign in the account that you want the connector to be run as. 

Graphical user interface, application, Teams

Description automatically generated 

Once the connection is created, return to the previous tab in Power Automate and select Refresh to get the latest connections. 

Graphical user interface, text, application

Description automatically generated 

Now select the connection you want to use for the bot.  And do the same for the Office 365 Users connection by selecting and existing one or follow steps 5 and 6 again to create a new Office 365 Users connection. 

Select Import.  You will see the status bar showing the solution is being imported.  This can take a few minutes. 

 

Once the solution is imported you will see the following success message. 

Graphical user interface, application, email

Description automatically generated 

Turn on and configure connection for the Flows 

Once the solution file is imported, we need to go to configure the connections used in the Power Automate flow of the adoption bot and turn them on. 

Select Default solution and filter the displayed components to Cloud flows on the top right corner. 

 

You will see two flows AdoptBot Ask an Expert and AdoptBot Submit Feedback.   

Graphical user interface, application, email

Description automatically generated 

Select AdoptBot Ask an Expert.  The steps are identical for both flows.  You will need to configure both flows with the same steps below. 

Select Edit on the top menu. 

Select the connections for the Office 365 user and Microsoft Teams connector. 

 

Select the Microsoft Teams connector.  Remove the content in the Team field and the Channel field.  Replace it with the team and the channel where your experts will be presented to handle user’s Ask an Expert request and view their feedback.   

 

Select Save on the top right corner. 

 

Return to flow details by selecting the back arrow on the top left.   

 

Select Turn on to turn on the flow.  Repeat the same for AdoptBot Submit Feedback flow. 

 

Test the bot in Power Virtual Agents 

Go to Power Virtual Agents Teams app by following the first step in the ‘Create your Dataverse for Teams environment’ section.  If you imported the bot to a Dataverse full environment, then you need to author the bot from Power Virtual Agents web portal by signing into www.powerva.microsoft.com 

Select Chatbots tab at the top of Power Virtual Agents Teams app 

 

Select the team name of the Dataverse for Teams environment that you have imported the bot in.  Select the Adoption Bot to enter embedded authoring for the bot in Teams. 

Graphical user interface, application, Teams

Description automatically generated 

Matt to fill in the detail on what to try out in the bot 

Publish the bot to your end users 

Now that you have tried out the bot and is satisfied with its content, it’s time to make it available to your employees.   

Go to Publish from the left navigation panel.  Select the Publish button and proceed with the confirmation dialog to make the bot content live. 

 

Select Share the bot and select Turn on Teams so end users can chat with the bot in Microsoft Teams. 

 

Select Submit for admin approval on the panel. 

 

Select Download manifest and provide the description and other information relevant to your bot. 

 

Once you have downloaded the Teams app manifest for your bot, open the teamsApp.zip file on your computer and open the manifest.json file. 

 

Matt to provide the app id to replace the “id” field in the app manifest and instructions to upload custom app into Teams from here. 

 

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft 
trademarks or logos is subject to and must follow 
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general).
Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship.
Any use of third-party trademarks or logos are subject to those third-party's policies.
