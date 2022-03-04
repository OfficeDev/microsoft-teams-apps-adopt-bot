# Adoption Bot 2022

Adoption Bot is a user care Chat Bot built with [Power Virtual Agents for Microsoft Teams (PVA)](https://docs.microsoft.com/en-us/power-virtual-agents/teams/fundamentals-what-is-power-virtual-agents-teams) and the [Employee FAQ Template](https://github.com/Flow-Joe/PowerVirtualAgentsSamples/tree/master/Templates/Employee%20FAQ). Out of the box, Adoption Bot answers 100+ common questions about Microsoft Teams and Microsoft 365.  You can edit the included topics, add your own topics, or ingest your existing FAQs.  If users need additional help, Adoption Bot can connect them to experts or be extended to open service tickets in ITSM with Premium Power Automate connectors.

New with Adoption Bot 2022:
- 103 updated QnA pairs in English
- Dataverse for Teams stores Ask an Expert request status and captures resolved requests
- Status Flow - users can check the status of their requests 
- Adoption Bot Canvas app to allow experts to review request status and feedback from users

Benefits:
- No code Bots have quick time to value and net quick win for M365 project team
- Capabilities available in the [Power Virtual Agents app in Microsoft Teams are available as part of select Microsoft 365 subscriptions](https://docs.microsoft.com/en-us/power-virtual-agents/requirements-licensing-subscriptions)
- Bots can drive down support costs with fewer service desk tickets*

*Use of bots to handle employee questions reduces the number of IT and HR support tickets by 10% to 15%.  Source: Forrester Consulting Total Economic Impact™ Of using Microsoft Teams as a platform and Teams with Power Platform

## Cost
Adoption Bot 2022 is free for most Enterprise customers for use in Teams.  Adoption Bot 2022 and [Power Virtual Agents app in Microsoft Teams are available as part of most Microsoft 365 subscriptions](https://docs.microsoft.com/en-us/power-virtual-agents/requirements-licensing-subscriptions) and use standard connectors.  

## Prerequisites
-	Subscription that includes Power Virtual Agents for Teams.  Most plans except A1, F1 and SUB SKUs.  *note for full details see
[Get access to Power Virtual Agents - Power Virtual Agents | Microsoft Docs](https://docs.microsoft.com/en-us/power-virtual-agents/requirements-licensing-subscriptions)*
-	Access to Power Virtual Agents for Teams App to deploy and customize the Bot
-	Microsoft Teams Team to host the Bot/Dataverse and Ask an Expert and Submit Feedback escalations to land *(Team Owner)*
-	Required network access to PVA service endpoints listed [here](https://docs.microsoft.com/en-us/power-virtual-agents/requirements-quotas#required-services)

## Deployment Guide
**First, add the required apps to Teams, and create your Power Apps app:**

1.	Download the [Adoption Bot 2022 solution](https://github.com/OfficeDev/microsoft-teams-apps-adopt-bot/blob/main/Adoption%20Bot%202022.zip) Zip file.
2.	Add the [Power Virtual Agents app in Microsoft Teams](https://teams.microsoft.com/l/app/1850b8bb-76ac-411c-9637-08f7d1812d35?source=store-copy-link), you can search for it directly in Microsoft Teams app store.
3.	Add the [Power Apps app in Microsoft Teams](https://teams.microsoft.com/l/app/a6b63365-31a4-4f43-92ec-710b71557af9?source=store-copy-link), and open it.
4.	It will open the app in **Home** tab and select **Start now**.
5.	Select the team you want to use, and create an application. When prompted, name the application **Demo** and select **Save**. If this is the first time you are creating an app in the team, it will take a few seconds to setup a Dataverse database before you are prompted to name the application

**Next, import the template solution:**

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

**Setting up Power Automate flows**

1. In the Power Apps app, select the **Build** tab to see your list of teams on the side panel.

![image](https://user-images.githubusercontent.com/54556057/156798088-1acdd0f9-5190-4844-b23e-dd2a5ff07563.png)

2. Select the team you choose in the previous step from the list, then select See all to view the solution overview.

![image](https://user-images.githubusercontent.com/54556057/156799403-c5d38a2f-7c1b-4d25-b69c-407157fe9429.png)

3. Select **Cloud flows** on the side panel.

![image](https://user-images.githubusercontent.com/54556057/156799497-0fa14bef-096d-4e54-ac65-7a537621163d.png)

4. Select the **Adoption Bot – Ask an Expert** flow to open it. This flow takes employee's escalation request and notify human expert in a team channel.
5. Select **Edit**
6. Open the action **Convert time zone - Select Your Timezone** and set the **destination time zone** to your timezone.

![image](https://user-images.githubusercontent.com/54556057/156799812-19300ede-867d-4406-9bb3-5213fa852569.png)

7. Open the action Post adaptive card in a chat or channel - Select Team and Channel.
8. Change the **Team** and **Channel** to your desired team and channel for the feedback information adaptive card to be posted to.

![image](https://user-images.githubusercontent.com/54556057/156799996-734ccd10-7268-4998-9b86-bf2e76144fc5.png)

9. Expand the condition action.
10. Open the action **Convert time zone - Select Your Timezone** - **Resolved** and set the **destination time zone** to your timezone.

![image](https://user-images.githubusercontent.com/54556057/156800241-d8c545a9-9f64-488c-86e1-ef6ef57f961b.png)

11. Select **Save**.
12. Select the back arrow ←.

13. Select the **Adoption Bot - Feedback flow** to open it. This flow takes employee's feedback and post into a team channel for human expert to review
14. Select **Edit**.
15. Open the action Convert time zone - Select Your Timezone and set the destination time zone to your timezone.
 
![image](https://user-images.githubusercontent.com/54556057/156801368-8c6784c9-eb96-4198-8e4f-daf9fefc9db4.png)
 
16. Open the action **Post adaptive card in a chat or channel - Select Team and Channel**.
17. Change the **Team** and **Channel** to your desired team and channel for the feedback information adaptive card to be posted to.

![image](https://user-images.githubusercontent.com/54556057/156801607-8d98f7be-11aa-4869-a6ca-39c1adaa5405.png)

18. Select Save.
 
**Bot Validation**

1. Open the **Power Virtual Agents** Teams application.
2. Select Chatbots.

![image](https://user-images.githubusercontent.com/54556057/156801903-70bd7d6a-28b9-496c-81de-a0f72d60d286.png)

3. Select your team.
4. Select your chat bot.
5. Select Publish on the left menu.

![image](https://user-images.githubusercontent.com/54556057/156802040-b1eea660-067e-4405-98da-60768fed9ca7.png)

6. Select **Turn on Teams**.

![image](https://user-images.githubusercontent.com/54556057/156802106-f19c5829-5b91-44a8-9d7a-b454c541f62c.png)

7. Select **Open the bot**.

![image](https://user-images.githubusercontent.com/54556057/156802269-77bfc8b9-eae4-425e-9d12-c91bde2041d1.png)

8. Select Add to add the bot into Microsoft Teams for yourself

![image](https://user-images.githubusercontent.com/54556057/156802374-a8569680-0b2d-404c-95fc-a986cb6e6ded.png)

9. You will now be taken to a chat window with your bot. Here you can try trigger phrases to ensure that the bot is functioning correctly. We have listed several phases you should consider trying below:

i. Hello
ii. Ask an expert
iii. What is the status of my request
iv. Submit feedback

10. For **Ask an expert** and **Submit feedback**, make sure to check the bot posts request and feedback to the team and channel you configured earlier. *Note that you won't be able to deep link to yourself from the request adaptive card if you are the same person requesting it.*

**Set up Power App Teams tab**
You can review the bot's performance in [Power Virtual Agents built-in analytics dashboard](https://docs.microsoft.com/en-us/power-virtual-agents/analytics-sessions#:~:text=Analyze%20session%20information%20in%20Power%20Virtual%20Agents%201,the%20default%20period%20of%20session%20transcript%20retention.%20). In addition to the dashboard, Adoption Bot also comes with a Canvas app to allow experts to review the verbal feedback from employees.

1. Open the **Power Apps for Teams** app **Build** Tab.
2. Select your team
3. Select See All.

![image](https://user-images.githubusercontent.com/54556057/156798463-dc59554a-4d45-471e-be0b-c6486c9d3317.png)

4. Select the three dots next to the **Adoption Bot Admin App** (...).
5. Select **Edit**.

![image](https://user-images.githubusercontent.com/54556057/156804546-29e1714c-c428-47bd-bfd2-de0400ddfbd0.png)

6. Select **Publish to Teams** on the upper right.

![image](https://user-images.githubusercontent.com/54556057/156804815-7e5f8ad7-e891-45df-852d-81ba9a1b4e28.png)

7. Select **Next**.

![image](https://user-images.githubusercontent.com/54556057/156805107-0361f8bb-ecf5-4442-a991-079a468532c2.png)

8. Select your team.

![image](https://user-images.githubusercontent.com/54556057/156805271-db4f7cfa-a340-40d2-827c-497cffa3a9b8.png)

9. Select **+ Add app as a Tab**.

![image](https://user-images.githubusercontent.com/54556057/156805424-ad99438d-a481-4e00-9b4b-753a44ea7aa8.png)

10. Select **Save and close**.
11. Open your team
12. Select the Adoption Bot Admin tab

![image](https://user-images.githubusercontent.com/54556057/156805664-e30c348e-0b6d-43de-9405-049cf62ad75e.png)

13. Once selected you will see the Adoption Bot Admin Canvas App. You will be able to view requests and feedback.

![image](https://user-images.githubusercontent.com/54556057/156805832-0fe1f23d-72e3-423c-8d09-69ee09aff4ad.png)

**Next steps**

You have now fully set up the Adoption Bot template. The next step is to go to Power Virtual Agents Teams application to add FAQ content for the bot to answer your organization's questions. [Extension documentation](https://github.com/Flow-Joe/PowerVirtualAgentsSamples/blob/master/Templates/Employee%20FAQ/EXTEND.md)

**Adding bot content in Power Virtual Agents**

The Adoption Bot template can easily be extended in [Power Virtual Agents Teams](https://teams.microsoft.com/l/app/1850b8bb-76ac-411c-9637-08f7d1812d35?source=store-copy-link) application by adding new [topics, messages, questions, actions](https://docs.microsoft.com/en-us/power-virtual-agents/teams/authoring-create-edit-topics-teams#create-a-topic) and more.

As a starting point, we suggest looking at the greeting system topic, customizing it to provide a personal greeting that represents your company and how you want your users to start using the bot. Yyou can freely edit the topics or simply create new topics to handle any additional areas you wish to include. You can also quickly and easily add new topics with the built-in [topic suggestion feature](https://docs.microsoft.com/power-virtual-agents/teams/advanced-create-topics-from-web-teams).

Reach out to the Github Repro here or the [PVA Community](https://powerusers.microsoft.com/t5/Power-Virtual-Agents-Community/ct-p/PVACommunity) for help and ideas from our community members.

**Making the bot available to employees**

Once you are satisfied with the bot's content, it's time to make it available to employees. You can easily make the bot available in Microsoft Teams app store by following the steps to [share the bot with your organization](https://docs.microsoft.com/en-us/power-virtual-agents/teams/publication-add-bot-to-microsoft-teams-teams#share-the-bot-with-your-organization). We recommend to partner with your IT admin to also pre-pin the bot on the left rail so employees can easily discover the bot in Microsoft Teams without needing to manually install it. Learn more about best practice guidance to [partner with admin to roll out bot in Microsoft Teams](https://powervirtualagents.microsoft.com/blog/partner-with-admin-to-roll-out-bot-in-microsoft-teams/).

Alternatively, you can also directly [share the bot's installation link](https://docs.microsoft.com/power-virtual-agents/teams/publication-add-bot-to-microsoft-teams-teams#install-a-bot-as-an-app-in-microsoft-teams) with others in the organization without going through the admin approval process. Make sure you change the bot's [access](https://docs.microsoft.com/power-virtual-agents/teams/configuration-security-teams) to fit your target audience so they have permission to install the bot.

**Brand Adoption Bot for your organization**

Optionally, you can give the bot a name that makes sense to your organization.  To change the Bot name and icon, click Manage and Details.  Click save at the top.

![image](https://user-images.githubusercontent.com/54556057/114073509-5afa1f80-9871-11eb-8997-de72c77f768f.png)

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
