# Adoption Bot

Adoption Bot is a user care Chatbot built with Power Virtual Agents for Microsoft Teams (PVA).  Out of the box, Adoption Bot answers 100+ common questions about Microsoft 365 and Teams.  You can edit the included topics, add your own topics, and ingest existing FAQs.  If users need additional help, Adoption Bot can connect them to experts or even be extended to open service tickets with premium Flow connectors.

![Demo animated GIF](https://adoptbotv2kb.blob.core.windows.net/%24web/adoptbotgithub2.gif)

Benefits:
- No code Bots have quick time to value and net quick win for M365 project team
- Capabilities available in the [Power Virtual Agents app in Microsoft Teams are available as part of select Microsoft 365 subscriptions](https://docs.microsoft.com/en-us/power-virtual-agents/requirements-licensing-subscriptions)
- Drive down support costs with fewer service desk tickets*

*Use of bots to handle employee questions reduces the number of IT and HR support tickets by 10% to 15%.  Source: Forrester Consulting Total Economic Impact™ Of using Microsoft Teams as a platform and Teams with Power Platform

[Adoption Bot Overview and Demo on YouTube](https://youtu.be/xEqErtGxizU)

[Adoption Bot QnA Pairs for hosted in 41+ languages](https://adoptbotv2kb.blob.core.windows.net/%24web/adoptbot2021.html)

[Awesome video by Stuart Ridout - Set up an FAQ bot in Microsoft Teams using Power Virtual Agent for Teams](https://www.youtube.com/watch?v=oX1MwSwqm7E)

## Costs
Adoption Bot and [Power Virtual Agents app in Microsoft Teams are available as part of most Microsoft 365 subscriptions](https://docs.microsoft.com/en-us/power-virtual-agents/requirements-licensing-subscriptions) and use standard connectors.  

## Deployment Guide
**Create your Dataverse for Teams environment**

You can skip this step if you already have a Dataverse for Teams environment for the team that will be managing the AdoptBot. 

1. Search for Power Virtual Agents Teams app in Microsoft Teams app store.

![image](https://user-images.githubusercontent.com/54556057/106006977-cd859c80-6083-11eb-94ff-dd754dcfadbf.png)

2. Add the app in Microsoft Teams and will land you in the homepage.  Select Start now.

![image](https://user-images.githubusercontent.com/54556057/106007208-0de51a80-6084-11eb-9067-d4ef939d40fc.png)

3. Select the team that will be managing the Bot.

![image](https://user-images.githubusercontent.com/54556057/106007331-2f460680-6084-11eb-8792-6b9081d8ddc1.png)
 
4. Wait for the Dataverse for Teams environment to be created in 30 seconds to a minute. 

![image](https://user-images.githubusercontent.com/54556057/106007410-44229a00-6084-11eb-93fe-2039f919db2c.png)

5. Once the environment is created you will be redirected to create your first bot.  You can exit out of it. 

**Import the bot into your Dataverse for Teams environment**

Please follow the instruction in the previous section if you do not have a Dataverse for Teams environment created yet.  Please note that the following instruction also applies to Dataverse full environment but that will require Power Platform licenses in addition to standard Office license.

1. Go to www.flow.microsoft.com and select the environment that you would like to own the bot in from the environment picker on the top right corner.

![image](https://user-images.githubusercontent.com/54556057/106007541-69afa380-6084-11eb-9a99-d9a8d73e8cfb.png)
 
2. Go to Solutions from the left nav menu and select Import. 

![image](https://user-images.githubusercontent.com/54556057/106007586-79c78300-6084-11eb-8f09-2f4777951a25.png)

3. Select the AdoptionBotPVA package .zip file that you have downloaded from the Github repo.  Select Next. 

![image](https://user-images.githubusercontent.com/54556057/106007675-8c41bc80-6084-11eb-93d8-a2867815ff6d.png)
 
4. Read the summary page and select Next again.  You will be asked to provide Connection for the solution.  You can select an existing connection or create a new one by following the instruction of the menu.  Skip to step 7 if you don’t need to create a new connection. *Note: Consider using a service account for the connections as notification cards originate from this account.  The service account will need a license that includes Exchange Online mailbox.*

![image](https://user-images.githubusercontent.com/54556057/106007726-9a8fd880-6084-11eb-9068-be9e8204ac82.png)

5. Optional – create a new connection.  By selecting New connection, a new tab will be opened and select Create on the dialog.  Sign in the account that you want the connector to be run as. 

![image](https://user-images.githubusercontent.com/54556057/106007808-abd8e500-6084-11eb-8025-4a46d626b47b.png)

6. Once the connection is created, return to the previous tab in Power Automate and select Refresh to get the latest connections. 

![image](https://user-images.githubusercontent.com/54556057/106007859-bd21f180-6084-11eb-8afa-b4b981b533cb.png)

7. Now select the connection you want to use for the bot.  And do the same for the Office 365 Users connection by selecting and existing one or follow steps 5 and 6 again to create a new Office 365 Users connection. 

8. Select Import.  You will see the status bar showing the solution is being imported.  This can take a few minutes. 

![image](https://user-images.githubusercontent.com/54556057/106007927-d034c180-6084-11eb-92e7-e6a19f7611c7.png)
 
9. Once the solution is imported you will see the following success message. 

![image](https://user-images.githubusercontent.com/54556057/106007979-de82dd80-6084-11eb-8410-2e35afab629c.png)

**Turn on and configure connection for the Flows**

Once the solution file is imported, we need to go to configure the connections used in the Power Automate flow of the adoption bot and turn them on. 

1. Select Default solution and filter the displayed components to Cloud flows on the top right corner. 

![image](https://user-images.githubusercontent.com/54556057/106008054-efcbea00-6084-11eb-830e-bb6133833840.png)

2. You will see two flows AdoptBot Ask an Expert and AdoptBot Submit Feedback.  

![image](https://user-images.githubusercontent.com/54556057/106008123-ff4b3300-6084-11eb-8fa1-2b9ef39cfdc4.png)

3. Select AdoptBot Ask an Expert.  The steps are identical for both flows.  You will need to configure both flows with the same steps below. 

4. Select Edit on the top menu. 

![image](https://user-images.githubusercontent.com/54556057/106008221-138f3000-6085-11eb-8f06-c46f2563ab0b.png)

5. Select the connections for the Office 365 user and Microsoft Teams connector. 

![image](https://user-images.githubusercontent.com/54556057/106008292-23a70f80-6085-11eb-8a1b-e8fd4a670707.png)

6. Select the Microsoft Teams connector.  Remove the content in the Team field and the Channel field.  Replace it with the team and the channel where your experts will be presented to handle user’s Ask an Expert request and view their feedback.   

![image](https://user-images.githubusercontent.com/54556057/106008353-33beef00-6085-11eb-88a5-8ac3fb3f7887.png)

7. Select Save on the top right corner. 

![image](https://user-images.githubusercontent.com/54556057/106008408-420d0b00-6085-11eb-9285-14829bcc5d4e.png)

8. Return to flow details by selecting the back arrow on the top left.   

![image](https://user-images.githubusercontent.com/54556057/106008466-505b2700-6085-11eb-9c1b-25d303daf9ae.png)

9. Select Turn on to turn on the flow.  Repeat the same for AdoptBot Submit Feedback flow. 

![image](https://user-images.githubusercontent.com/54556057/106008522-60730680-6085-11eb-8566-93388698da18.png)

**Test the bot in Power Virtual Agents**

Go to Power Virtual Agents Teams app by following the first step in the ‘Create your Dataverse for Teams environment’ section.  If you imported the bot to a Dataverse full environment, then you need to author the bot from Power Virtual Agents web portal by signing into www.powerva.microsoft.com 

1. Select Chatbots tab at the top of Power Virtual Agents Teams app 

![image](https://user-images.githubusercontent.com/54556057/106008587-7254a980-6085-11eb-843e-78be5fbdde64.png)

2. Select the team name of the Dataverse for Teams environment that you have imported the bot in.  Select the Adoption Bot to enter embedded authoring for the bot in Teams. 

![image](https://user-images.githubusercontent.com/54556057/106008665-88626a00-6085-11eb-93a5-2395449f19ca.png)

3. Chat with your AdoptBot in PVA embedded authoriing - Test bot pane.  Ask common questions like "Guests in Teams".  

Note: You may want to turn off topics, edit topics or add new topics using Power Virtual Agents App in Teams.  [Create and edit topics in your Power Virtual Agents bot](https://docs.microsoft.com/en-us/power-virtual-agents/authoring-create-edit-topics).

Note:  You can also extract topics from webpages or online files [Extract content from webpages or online files](https://docs.microsoft.com/en-us/power-virtual-agents/advanced-create-topics-from-web)

**Test the Flows for Ask an Expert and Submit feedback**

1. Type Ask an Expert in an AdoptBot conversation.

2. Enter a title for your request

3. Enter a description for your request

4. Check the Team and channel you configured in Step 6 (Turn on and configure connection for the Flows) for a new Adaptive Card.  

![image](https://user-images.githubusercontent.com/54556057/106078454-73b3bf80-60e1-11eb-9429-19823c2bef69.png)

5. Type Submit Feedback and test Submit Feedback flow as per instructions above.

IMPORTANT:  If Ask An Expert or Submit Feeback Flow fails with "Sorry the Bot can't talk for a while.." you need to remove and re-add the Ask An Expert Action in the Escalate topic.

![image](https://user-images.githubusercontent.com/54556057/107689540-f22e6680-6c76-11eb-84c3-af8c28dd9543.png)

1. Click the ellipsis next to Ask An Expert Flow Action and Choose Delete

2. Click + Add node in PVA conversation tree and choose Call an Action - AdoptBot Ask An Expert

3. Remap the 3 input variables (UPN -> bot.UserId, Title -> Var_AskTitle, Desc -> Var_AskDesc)

4. Save the Escalate topic and re-test in PVA Test UI


**Publish the bot to your end users**

Now that you have tried out the bot and is satisfied with its content, it’s time to make it available to your employees.   

1. Go to Publish from the left navigation panel.  Select the Publish button and proceed with the confirmation dialog to make the bot content live. 

![image](https://user-images.githubusercontent.com/54556057/106008755-9f08c100-6085-11eb-94d3-cc53e7d3aeda.png)

2. Select Share the bot and select Turn on Teams so end users can chat with the bot in Microsoft Teams. 

![image](https://user-images.githubusercontent.com/54556057/106008804-acbe4680-6085-11eb-8d8d-ab0f20e11c42.png)

3. Select Submit for admin approval on the panel. 

![image](https://user-images.githubusercontent.com/54556057/106008845-bb0c6280-6085-11eb-9ea9-f16c770a4784.png)

4. Select Download manifest and provide the description and other information relevant to your bot. 

![image](https://user-images.githubusercontent.com/54556057/106008919-cbbcd880-6085-11eb-99c1-9a37e6f22c8c.png)
 
5. Once you have downloaded the Teams app manifest for your bot, extract the teamsApp.zip file on your computer and edit the manifest.json file. 

6. Replace AppID with 6c8c0828-bd30-4c89-900b-5656ac58683c and save the manifest.json

7. Rezip the 3 files (Manifest and two icons)

**Upload the bot to your tenant app store**

When you publish a custom Teams app, it's available to users in your organization's app store.

Note:  adding Apps to your tenant requires upload custom apps to be enabled in policy.  See this article for details [Publish a custom app by uploading an app package](https://docs.microsoft.com/en-us/microsoftteams/upload-custom-apps)

1. Launch Microsoft Teams admin center.

2. In the left navigation of the Microsoft Teams admin center, go to Teams apps > Manage apps.

3. Click Upload, click Select the zip file you edited in the prior step.

![image](https://user-images.githubusercontent.com/54556057/106159851-3b4cc980-6153-11eb-8edb-2c2019cdd347.png)

**Pin and install the app for users to discover**

By default, for users to find the app they have to go to your organization's app store and browse or search for it. To make it easy for users to get to the app, you can pin the app to the app bar in Teams. 

1. In the left navigation of the Microsoft Teams admin center, go to Teams apps > Setup policies.

2. Select the policy by clicking to the left of the policy name, and then select Edit.

3. Under Pinned apps, select Add apps.

4. In the Add pinned apps pane, search for the apps you want to add, and then select Add. You can also filter apps by app permission policy. When you've chosen your list of apps to pin, select Add.

![image](https://user-images.githubusercontent.com/54556057/106160982-6c79c980-6154-11eb-82ea-6969a2c6e84d.png)

5. Arrange the apps in the order that you want them to appear in Teams, and then select Save.

![image](https://user-images.githubusercontent.com/54556057/106161093-8adfc500-6154-11eb-9e80-895e3b574c84.png)

See this article for additional details:  [Manage app setup policies in Microsoft Teams](https://docs.microsoft.com/en-us/microsoftteams/teams-app-setup-policies)

**Make Adoption Bot your own**

- Review the included topics and remove or edit as you see fit.
- Add your own topics.  A best practice is to look at top help desk tickets and craft topics that map to top use questions.
- Use [Create topics from existing online support content](https://docs.microsoft.com/en-us/power-virtual-agents/advanced-create-topics-from-web) to automatically extract topics from your existing support documentation.  


## Contributing

Special thanks to contributors Erik Olsson, Aditya Challapally, Michael Chow, Jong Hoon Moon, Belinda Parker and Nidhi Shandilya who helped create and launch this app template.  

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
