# Adoption Bot

Adoption Bot is a user care Chatbot built with Power Virtual Agents for Microsoft Teams (PVA).  Out of the box, Adoption Bot answers 100+ common questions about Microsoft 365 and Teams.  You can edit the included topics, add your own topics, and ingest existing FAQs.  If users need additional help, Adoption Bot can connect them to experts or even be extended to open service tickets with premium Flow connectors.

![Demo animated GIF](https://hickweb.blob.core.windows.net/%24web/AdoptBot/adoptbotgithub2.gif)

Benefits:
- No code Bots have quick time to value and net quick win for M365 project team
- Capabilities available in the [Power Virtual Agents app in Microsoft Teams are available as part of select Microsoft 365 subscriptions](https://docs.microsoft.com/en-us/power-virtual-agents/requirements-licensing-subscriptions)
- Drive down support costs with fewer service desk tickets*

*Use of bots to handle employee questions reduces the number of IT and HR support tickets by 10% to 15%.  Source: Forrester Consulting Total Economic Impact™ Of using Microsoft Teams as a platform and Teams with Power Platform

[Adoption Bot Overview and Demo on YouTube](https://youtu.be/xEqErtGxizU)

[Adoption Bot QnA Pairs for hosted in 41+ languages](https://hickweb.blob.core.windows.net/%24web/AdoptBot/adoptbot2021.html)

[Good deployment video by Szymon Bochniak](https://youtu.be/5QIwMVFaKzs)

[If you would rather build the Adoption Bot from scratch, follow this Step by Step guide](https://1drv.ms/w/s!Ah-35FI1EEXFiFGt7DEV164pZQc2?e=dKzMTO)

## Cost
Free for most Enterprise customers.  Adoption Bot and [Power Virtual Agents app in Microsoft Teams are available as part of most Microsoft 365 subscriptions](https://docs.microsoft.com/en-us/power-virtual-agents/requirements-licensing-subscriptions) and use standard connectors.  


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
**Create Teams to host the Dataverse for Teams environment**
You can skip this step if you already have a Team for the team that will be developing and managing the Adoption Bot.

1.	Create a new Team in Microsoft Teams to host your Dataverse.  Open Microsoft Teams and Click Join or Create a Team.
2.	Choose Create a Team from scratch.
3.	Team can be public or private.
4.	We don’t need to add any users currently.  Any owner of this team will have authoring rights to your Adoption Bot. 

**Create a Teams where Submit Feedback and Ask An Expert escalations land**
You can skip this step if you already have a Team for Champions or support personal who will monitor bot esclations.

1.	Create a new Team in Microsoft Teams to host esclations.  Open Microsoft Teams and Click Join or Create a Team.
2.	Choose Create a Team from scratch.
3.	Team can be public or private.
4.	Add members who will have access to Bot escalations.  You can create seperate channels for Submit Feedback and Asn An Export or have them both go to the same channel.

![image](https://user-images.githubusercontent.com/54556057/115288087-0717f200-a11f-11eb-92fa-4a835ddbc440.png)

**Prepare to import**

1.	Search for Power Apps Teams app in Microsoft Teams app store.

![image](https://user-images.githubusercontent.com/54556057/115288329-52ca9b80-a11f-11eb-8b55-47ce3fd2d2e8.png)

2. Click Add to open Power Apps for Teams app in Microsoft Teams and will land you in the homepage. 

3. Select Home Tab.  If you don’t see any Recent Apps or any Apps Under Start Now, we need to create a dummy app to get access to Solution Explorer.

![image](https://user-images.githubusercontent.com/54556057/115288461-768de180-a11f-11eb-8235-cf44f6901661.png)

If you do see Apps listed skip to 7.

![image](https://user-images.githubusercontent.com/54556057/115288547-8c030b80-a11f-11eb-8977-6b14d6a4c4c3.png)

4.	Click Start now and select the team you created in Step one to create the dummy app.

![image](https://user-images.githubusercontent.com/54556057/115288681-bb197d00-a11f-11eb-84f4-119adaae51bd.png)
 
5. Click Create, this step will take a few minutes as it hydrates the Dataverse environment.

![image](https://user-images.githubusercontent.com/54556057/115288784-d6848800-a11f-11eb-8fec-78628837860a.png)

6.	Provide a name for the dummy app and click Save.

![image](https://user-images.githubusercontent.com/54556057/115288826-e734fe00-a11f-11eb-9be0-cb703990128f.png)

**Import PVA Chatbot and Flows**

7.	Click Home Tab at the top of Power Apps for Teams App.

9.	Below Recent Apps Click See More ->.

![image](https://user-images.githubusercontent.com/54556057/115288902-02077280-a120-11eb-8f1b-38f7bb9ae749.png)

9.	Click See All Under Items Created for TEAM_NAME.

![image](https://user-images.githubusercontent.com/54556057/115288964-1481ac00-a120-11eb-9464-c0a15f20828d.png)

10.	Click Import at top of Solution Explorer.

![image](https://user-images.githubusercontent.com/54556057/115289212-54489380-a120-11eb-8100-c3bd50652a90.png)

11.	Choose the Zip file you downloaded from the Adoption Bot GitHub Repro.

12. Click Next.

![image](https://user-images.githubusercontent.com/54556057/115289319-704c3500-a120-11eb-8595-6a07af58840b.png)

13.	You should see confirmation we are importing 2 Flows and 1 Chatbot.

![image](https://user-images.githubusercontent.com/54556057/115289401-835f0500-a120-11eb-8d9a-b2a16890d7be.png)

14.	Click Next.

16.	Next we need to specify Connections for Teams and Office 365 user connectors used in the Flows.

**Create or select connections for Flows**

16.	If you have existing connections choose them now.  A connection is the security  context (account) the Flow runs under.  To create new connections, Click dropdown next to Microsoft Teams and + New Connection.

![image](https://user-images.githubusercontent.com/54556057/115289661-d1740880-a120-11eb-96c0-17a0b092bf5a.png)

17.	It's recommended you use a generic or service for the Flow connections.  Flow notifications will orginate from this account.  The service account requires Teams License and Exchange Online Mailbox/license.

![image](https://user-images.githubusercontent.com/54556057/116165279-841c0c00-a6c9-11eb-8542-37810b5e8b39.png)

19.	In the Microsoft Teams New Connections Click Create.

![image](https://user-images.githubusercontent.com/54556057/115289738-e8b2f600-a120-11eb-83c1-6750eb7ef362.png)

19.	Specify and sign into the the account you want to use for the connection.  E.g. service@contosomfg.com.

![image](https://user-images.githubusercontent.com/54556057/115289797-fb2d2f80-a120-11eb-80d3-25b7e349bd1c.png)

20.	You should see the new connection for Teams Listed.

![image](https://user-images.githubusercontent.com/54556057/115289902-0da76900-a121-11eb-9fe8-ff96cf5a3e3d.png)

21.	Go back to Power App for Teams App and Hit Refresh button on screen.  You should see Teams now has a valid connection – in my example using a service account.

23.	Do the same steps for the Office 365 Users Connection:   Drop Down Select a Connection, Click New Connection, Create, Sign in with account.

25.	Now back in Power Apps for Teams you should see 2 valid connections for the Flows being imported.

![image](https://user-images.githubusercontent.com/54556057/115290023-23b52980-a121-11eb-9a7d-45126c15122a.png)

24.	Click Import.

![image](https://user-images.githubusercontent.com/54556057/115290082-37f92680-a121-11eb-8643-0d082346f327.png)

25.	After a few minutes you should see this.

![image](https://user-images.githubusercontent.com/54556057/115290187-46dfd900-a121-11eb-9904-c355d65e76bb.png)

**Configure Team and Channels for Ask An Expert and Submit Feedback Flows**

26.	Back in Power App for Teams App Build Tab, Click See all.

28.	Click Cloud Flows – you should have 2 flows listed.

![image](https://user-images.githubusercontent.com/54556057/115290360-6e36a600-a121-11eb-9cbe-f830679b469d.png)

28.	Click on the First Flow Adoption Bot Share Feedback.

30.	Click Edit.

32.	Open the Flow Action – Post your own adaptive card as the Flow bot to a channel (Preview) action. 

34. Change the Team and Channel where you want to Submit Feedback escalations to land.  In My Case I created a Team called M365 Champs | Adoption Bot Feedback.  Note:  if using a service account, the service accounts needs to be a member of this Team to show up here.

![image](https://user-images.githubusercontent.com/54556057/115290484-97573680-a121-11eb-89a5-42dcfc413fc6.png)

32.	Click Save to Save the Flow.  

34.	Click Back arrow and now edit the Adoption Bot Ask An Expert:  Edit Flow, Open Post your own adaptive card as the Flow bot to a channel action, change Team and Channel, Click Save.

![image](https://user-images.githubusercontent.com/54556057/115290562-b2c24180-a121-11eb-9031-00aaccb363dc.png)

**Test the bot in Power Virtual Agents for Teams**

34. Back in Power Apps for Teams App, Build tab, Click Chatbots in left rail.

![image](https://user-images.githubusercontent.com/54556057/115290917-1e0c1380-a122-11eb-8931-22588d51669c.png)

35. Click on Adoption Bot PVA 2021 which will launch Power Virtual Agents for Teams App.

![image](https://user-images.githubusercontent.com/54556057/115290977-2ebc8980-a122-11eb-91d2-f49d2fcbdf26.png)

36. Chat with your AdoptBot in PVA embedded authoriing - Test bot pane.  Ask common questions like "Guests in Teams".  

Note: You may want to turn off topics, edit topics or add new topics using Power Virtual Agents App in Teams.  [Create and edit topics in your Power Virtual Agents bot](https://docs.microsoft.com/en-us/power-virtual-agents/authoring-create-edit-topics).

Note:  You can also extract topics from webpages or online files [Extract content from webpages or online files](https://docs.microsoft.com/en-us/power-virtual-agents/advanced-create-topics-from-web)

**Test the Flows for Ask an Expert and Submit feedback**

37. Type "Agent" in Power Virtual Agents for Teams Test Bot.

38. Choose Ask An Expert.

39. Enter a title for your request.

40. Enter a description for your request.

41. Check the Team and channel you configured in Step 31 and 33 for new Ask An Expert notification.

![image](https://user-images.githubusercontent.com/54556057/106078454-73b3bf80-60e1-11eb-9429-19823c2bef69.png)

42. Type Agent again and test Submit Feedback flow as per instructions above.

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
