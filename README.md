# Azure Bot


Azure Bot is a chat bot built on the [Hubot][hubot] framework. It was initially generated by [generator-hubot][generator-hubot], and configured to be deployed on [Azure](azure)

This README is intended to help get you started. Definitely update and improve to talk about your own instance, how to use and deploy, what functionality is available, etc!

[azure]: https://azure.microsoft.com/en-us/
[hubot]: http://hubot.github.com
[generator-hubot]: https://github.com/github/generator-hubot

## Prerequisites
- Create a [Personal Access Token](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/) in GitHub that you will use to authenticate as you deploy Hubot
  - You may want to consider creating an automation account to own this personal access token
- If you are using SAML authentication for your GitHub organization, you may need to [authorize this token](https://help.github.com/articles/authorizing-a-personal-access-token-for-use-with-a-saml-single-sign-on-organization/)

### Tools

Tool | Used for
--- | ---
[GitHub](https://github.com) (Please log in now) | To store and version code
[Slack team](https://slack.com/get-started#create) (Please create a new Slack team) | To interact with your chatbot
[Azure](https://azure.microsoft.com/en-us/) (Please Authenticate) | To host your chatbot
[Microsoft Teams](https://products.office.com/en-us/microsoft-teams/group-chat-software) (Please authenticate) | To interact with your chatbot


## Install
To install and connect the Azure Hubot to your Azure environment you will need to complete the following actions:

### Clone the Repository
Clone This repository to your GitHub Organization
- You will want to set this up as a private repository and give all members of your organization write access to allow inner-sourcing
- This will allow for greater contributions and speed up the development process

### Create Web App in Azure  
Connect to your Azure web portal and authenticate. You will then need to complete the following actions:  
- Select `Create a resource`
- Select `Web App`
  - Fill in the form data
  - Select `Create`
- Go to your newly created application on the dashboard
- Configure environment variables that your Hubot will need to use
  - Select `application settings`
  - Navigate to the `Application Settings` section
  - Select `Add new setting` to create key pairs:
    - HUBOT_SLACK_TOKEN=Your Created Slack Token
    - HUBOT_ADAPTER=slack
    - Select `Save` from top banner
  - *NOTE:* If you are using a different chat tool, you will need to configure different environment variables
- Set up automatic deployment of this app from your GitHub repository
  - Select `Deployment options`
  - Select `Choose source`
  - Select `GitHub`
    - Fill in the form data
    - *NOTE:* Use GitHub API Token that has write access to this repository
    - Select the correct azure Hubot repo


### Deployment
Any time the master branch of your Azure Hubot repository is updated, it will trigger the Azure Deployment and update the Hubot. The Hubot only takes around 30 seconds to be re-deployed.   
*NOTE:* The first deployment will take longer as it will need to pull in many of the base dependencies.

-------------------------------------

## Adding scripts to this Bot
Hubot is a node app running coffeescript modules that can be written within the `scripts` folder. One common pattern is to use a coffeescript wrapper that calls scripts in other languages so you can write Hubot in any scripting language you're comfortable with.

This implementation includes an example of this at `scripts/create-repo.coffee`. This module interprets the input given by the user and calls a bash script at `scripts/shell/create-and-protect-repo.sh` to create a github repository. These example files include documentation to implement this for other uses.

-------------------------------------

## Hubot / MS-Teams Bot integrations

### Connect to VSTS
You will want to connect the bot from your Chat tooling into VSTS.  
This integration should be able to complete at the minimum the following actions:
- Show queue
- Start build
- List Jobs

Other actions are greatly encouraged, and can be seen as enhancements.

### Connect to GitHub
You will want to connect the bot from your Chat tooling into GitHub.  
This integration should be able to complete at the minimum the following actions:
- List Repositories
- Create Repository
- List members of team

Other actions are greatly encouraged, and can be seen as enhancements.

### Monitoring
Having your bot be able to connect to your monitoring environment is a great step in maturity.  
The ability to query information or metrics gives you a quick insight to your environment from your chat environment.  
This allows teams to collaborate in real time about the environment and have a record of what is happening.
Commands that allow you to fetch metrics and graphs, as well as check endpoints can greatly increase your culture and promote your environments.  


### Sparkles
[Sparkles](https://github.com/pmn/sparkles/blob/master/scripts/sparkles.coffee)
Giving your teammates points for doing something special is a great way to build culture and promote sharing.  
This can be added and enhance your culture.  

### Remember
This is a fairly common script that allows your bot to remember basic strings.  
This is useful to remember common end points, or other common data that needs to be stored in chat.