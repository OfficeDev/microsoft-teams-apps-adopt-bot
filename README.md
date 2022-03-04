# Adoption Bot 2022

Adoption Bot is a user care Chatbot built with Power Virtual Agents for Microsoft Teams (PVA).  Out of the box, Adoption Bot answers 100+ common questions about Microsoft Teams and Microsoft 365.  You can edit the included topics, add your own topics, and ingest existing FAQs.  If users need additional help, Adoption Bot can connect them to experts or even be extended to open service tickets with Premium Power Automate connectors.

New in Adoption Bot 2022:
-updated QnA pairs in English
-Dataverse for Teams stores Ask an Expert request status and capptures resolved requests
-Status Flow - users can check the status of their requests 
-Adoption Bot app to allow experts to review request status and feedback from users

Benefits:
- No code Bots have quick time to value and net quick win for M365 project team
- Capabilities available in the [Power Virtual Agents app in Microsoft Teams are available as part of select Microsoft 365 subscriptions](https://docs.microsoft.com/en-us/power-virtual-agents/requirements-licensing-subscriptions)
- Drive down support costs with fewer service desk tickets*

*Use of bots to handle employee questions reduces the number of IT and HR support tickets by 10% to 15%.  Source: Forrester Consulting Total Economic Impact™ Of using Microsoft Teams as a platform and Teams with Power Platform

## Cost
Free for most Enterprise customers for use in Teams only.  Adoption Bot 2022 and [Power Virtual Agents app in Microsoft Teams are available as part of most Microsoft 365 subscriptions](https://docs.microsoft.com/en-us/power-virtual-agents/requirements-licensing-subscriptions) and use standard connectors.  

## Prerequisites
-	Subscription that includes Power Virtual Agents for Teams.  Most plans except GCC, A1 and SUB SKUs
[Get access to Power Virtual Agents - Power Virtual Agents | Microsoft Docs](https://docs.microsoft.com/en-us/power-virtual-agents/requirements-licensing-subscriptions)
-	Power Virtual Agents for Teams App (Important: dont use Power Virtual Agents web app as you will have to start Power Apps Trial)
-	Microsoft Teams Team to host the Bot/Dataverse
-	Microsoft Teams Team for Ask an Expert and Submit Feedback Escalation to land in
-	Teams Admin rights to upload custom app and set Teams App Setup Policy
-	Required network access to PVA service endpoints listed [here](https://docs.microsoft.com/en-us/power-virtual-agents/requirements-quotas#required-services)
-	IMPORTANT:  This solution uses seeded licensing and does not require Power App licenses. Do not use PVA for Web (powerva.microsoft.com) as it will require you to start a 30 day trial.

## Deployment Guide
**First, add the required apps to Teams, and create your Power Apps app:**

1.	Download the Adoption Bot 2022 solution.
2.	Add the [Power Virtual Agents app in Microsoft Teams](https://teams.microsoft.com/l/app/1850b8bb-76ac-411c-9637-08f7d1812d35?source=store-copy-link), you can search for it directly in Microsoft Teams app store.
3.	Add the [Power Apps app in Microsoft Teams](https://teams.microsoft.com/l/app/a6b63365-31a4-4f43-92ec-710b71557af9?source=store-copy-link), and open it.
4.	It will open the app in **Home** tab and select **Start now**.
5.	Select the team you want to use, and create an application. When prompted, name the application **Demo** and select **Save**. If this is the first time you are creating an app in the team, it will take a few seconds to setup a Dataverse database before you are prompted to name the application

Now, import the template solution:
1.	In the Power Apps app, select the Build tab to see your list of teams on the side panel.
![image](https://user-images.githubusercontent.com/54556057/156798088-1acdd0f9-5190-4844-b23e-dd2a5ff07563.png)
2.	Select the team you choose in the previous step from the list. The app you just created will appear in the main section of the window, this may take a few minutes to update.
3.	Select **See all**.
![image](https://user-images.githubusercontent.com/54556057/156798463-dc59554a-4d45-471e-be0b-c6486c9d3317.png)
4.	On the top menu bar, select Import, then select Browse in the pane that appears.
![Image](https://user-images.githubusercontent.com/54556057/156798748-2f3b392e-f323-4078-86f0-7148b0f19dad.png)
5.	Select the template solution you downloaded, and then **Next**.
6.	When you see the items to choose to import, make sure everything is selected and click **Next**.
7.	If you have connections, select them, if you do not then add them. You will need to add Microsoft Teams, Office and Dataverse connection.
![Image](https://user-images.githubusercontent.com/54556057/156798983-3f0fdc09-9a1d-4c48-8ce9-7f5ff7d5fd40.png)
8.	Select **Import**.

You have now imported the solution and your can go to the Build tab in Power Apps to see all of your items. To use the bot, you will need to go through some additional set up steps.

**Set up and validate Adoption Bot**

We need to update Power Automate Flows, validate the Adoption Bot is working and add our Adoption Bot Admin application to a teams channel. Once this section is completed, the Adoption Bot bot's escalation flow will be up and running and ready to be added with your organization's content.

Setting up Power Automate flows
1.	In the Power Apps app, select the **Build** tab to see your list of teams on the side panel.
![image](https://user-images.githubusercontent.com/54556057/156798088-1acdd0f9-5190-4844-b23e-dd2a5ff07563.png)
2.	Select the team you choose in the previous step from the list, then select See all to view the solution overview.
![image](https://user-images.githubusercontent.com/54556057/156799403-c5d38a2f-7c1b-4d25-b69c-407157fe9429.png)
3.	Select **Cloud flows** on the side panel.
![image](https://user-images.githubusercontent.com/54556057/156799497-0fa14bef-096d-4e54-ac65-7a537621163d.png)

4.	Select the **Adoption Bot – Ask an Expert** flow to open it. This flow takes employee's escalation request and notify human expert in a team channel.
 i.	Select **Edit**
 ii.	Open the action **Convert time zone - Select Your Timezone** and set the **destination time zone** to your timezone.
 ![image](https://user-images.githubusercontent.com/54556057/156799812-19300ede-867d-4406-9bb3-5213fa852569.png)
 iii. Open the action Post adaptive card in a chat or channel - Select Team and Channel.
 iv. Change the **Team** and **Channel** to your desired team and channel for the feedback information adaptive card to be posted to.
 ![image](https://user-images.githubusercontent.com/54556057/156799996-734ccd10-7268-4998-9b86-bf2e76144fc5.png)
 v. Expand the condition action.
 vi. Open the action **Convert time zone - Select Your Timezone** - **Resolved** and set the **destination time zone** to your timezone.
 ![Picture9](https://user-images.githubusercontent.com/54556057/156800241-d8c545a9-9f64-488c-86e1-ef6ef57f961b.png)
 vii.	Select **Save**.
 viii. Select the back arrow ←.

5. 5.	Select the **Adoption Bot - Feedback flow** to open it. This flow takes employee's feedback and post into a team channel for human expert to review
 i. Select **Edit**.
 ii	Open the action Convert time zone - Select Your Timezone and set the destination time zone to your timezone.
 ![image](https://user-images.githubusercontent.com/54556057/156801368-8c6784c9-eb96-4198-8e4f-daf9fefc9db4.png)
 iii.	Open the action **Post adaptive card in a chat or channel - Select Team and Channel**.
 iv.	Change the **Team** and **Channel** to your desired team and channel for the feedback information adaptive card to be posted to.
 ![image](https://user-images.githubusercontent.com/54556057/156801607-8d98f7be-11aa-4869-a6ca-39c1adaa5405.png)
 v.	Select Save.
 
**Bot Validation**
1.	Open the **Power Virtual Agents** Teams application.
2.	Select Chatbots.
![image](https://user-images.githubusercontent.com/54556057/156801903-70bd7d6a-28b9-496c-81de-a0f72d60d286.png)
3.	Select your team.
4.	Select your chat bot.
5.	Select Publish on the left menu.
![image](https://user-images.githubusercontent.com/54556057/156802040-b1eea660-067e-4405-98da-60768fed9ca7.png)
6.	Select **Turn on Teams**.
![image](https://user-images.githubusercontent.com/54556057/156802106-f19c5829-5b91-44a8-9d7a-b454c541f62c.png)
7.	Select **Open the bot**.
![image](https://user-images.githubusercontent.com/54556057/156802269-77bfc8b9-eae4-425e-9d12-c91bde2041d1.png)
8.	Select Add to add the bot into Microsoft Teams for yourself
![image](https://user-images.githubusercontent.com/54556057/156802374-a8569680-0b2d-404c-95fc-a986cb6e6ded.png)
9.	You will now be taken to a chat window with your bot. Here you can try trigger phrases to ensure that the bot is functioning correctly. We have listed several phases you should consider trying below:
 i.	Hello
 ii.	Ask an expert
 iii.	What is the status of my request
 iv.	Submit feedback
10.	For **Ask an expert** and **Submit feedback**, make sure to check the bot posts request and feedback to the team and channel you configured earlier. *Note that you won't be able to deep link to yourself from the request adaptive card if you are the same person requesting it.*

**Set up Power App Teams tab**
You can review the bot's performance in Power Virtual Agents built-in analytics dashboard. In addition to the dashboard, Adoption Bot also comes with a Canvas app to allow experts to review the verbal feedback from employees.
1.	Open the Power Apps for Teams app Build Tab.
2.	Select your team

 
**Brand Adoption Bot for your organization**

Optionally, you can give the bot a name that makes sense to your organization.  To change the Bot name and icon, click Manage and Details.  Click save at the top.

![image](https://user-images.githubusercontent.com/54556057/114073509-5afa1f80-9871-11eb-8997-de72c77f768f.png)

**Publish the bot to your end users**

Now that you have tried out the bot and is satisfied with its content, it’s time to make it available to your employees.   

43. Go to Publish from the left navigation panel.  Select the Publish button and proceed with the confirmation dialog to make the bot content live. 

![image](https://user-images.githubusercontent.com/54556057/106008755-9f08c100-6085-11eb-94d3-cc53e7d3aeda.png)

44. Select Share the bot and select Turn on Teams so end users can chat with the bot in Microsoft Teams. 

![image](https://user-images.githubusercontent.com/54556057/106008804-acbe4680-6085-11eb-8d8d-ab0f20e11c42.png)

45. Select Submit for admin approval on the panel. 

![image](https://user-images.githubusercontent.com/54556057/106008845-bb0c6280-6085-11eb-9ea9-f16c770a4784.png)

46. Select Download manifest and provide the description and other information relevant to your bot. 

![image](https://user-images.githubusercontent.com/54556057/106008919-cbbcd880-6085-11eb-99c1-9a37e6f22c8c.png)
 
47. Once you have downloaded the Teams app manifest for your bot, extract the teamsApp.zip file on your computer and edit the manifest.json file. 

48. Replace AppID with 6c8c0828-bd30-4c89-900b-5656ac58683c and save the manifest.json

49. Rezip the 3 files (Manifest and two icons)

**Upload the bot to your tenant app store**

When you publish a custom Teams app, it's available to users in your organization's app store.

Note:  adding Apps to your tenant requires upload custom apps to be enabled in policy.  See this article for details [Publish a custom app by uploading an app package](https://docs.microsoft.com/en-us/microsoftteams/upload-custom-apps)

50. Launch Microsoft Teams admin center.

51. In the left navigation of the Microsoft Teams admin center, go to Teams apps > Manage apps.

52. Click Upload, click Select the zip file you edited in the prior step.

![image](https://user-images.githubusercontent.com/54556057/106159851-3b4cc980-6153-11eb-8edb-2c2019cdd347.png)

**Pin and install the app for users to discover**

By default, for users to find the app they have to go to your organization's app store and browse or search for it. To make it easy for users to get to the app, you can pin the app to the app bar in Teams. 

53. In the left navigation of the Microsoft Teams admin center, go to Teams apps > Setup policies.

54. Select the policy by clicking to the left of the policy name, and then select Edit.

55. Under Pinned apps, select Add apps.

56. In the Add pinned apps pane, search for the apps you want to add, and then select Add. You can also filter apps by app permission policy. When you've chosen your list of apps to pin, select Add.

![image](https://user-images.githubusercontent.com/54556057/106160982-6c79c980-6154-11eb-82ea-6969a2c6e84d.png)

57. Arrange the apps in the order that you want them to appear in Teams, and then select Save.

![image](https://user-images.githubusercontent.com/54556057/106161093-8adfc500-6154-11eb-9e80-895e3b574c84.png)

See this article for additional details:  [Manage app setup policies in Microsoft Teams](https://docs.microsoft.com/en-us/microsoftteams/teams-app-setup-policies)

**Make Adoption Bot your own**

- Rename the Bot to something that makes sense to your organization.  See Brand Adoption Bot for your organization section above.
- Review the included topics and remove or edit as you see fit.
- Add your own topics.  A best practice is to look at top help desk tickets and craft topics that map to top use questions.
- Use [Create topics from existing online support content](https://docs.microsoft.com/en-us/power-virtual-agents/advanced-create-topics-from-web) to automatically extract topics from your existing support documentation.  


## Contributing

Special thanks to contributors Aditya Challapally, Michael Chow, Jong Hoon Moon, Belinda Parker and Nidhi Shandilya who helped create and launch this app template.  
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
