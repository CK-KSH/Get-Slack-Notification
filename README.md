# GitHub Actions Workflow Demo with Slack

For a push or pull request, a Slack notification message ("Hello World! Beautiful Day!") is sent to my selected channel in my Workspace (#get-notification) in Slack account.

1) Go to Github Marketplace and look for "Post Slack messages v1.0.7" 
https://github.com/marketplace/actions/post-slack-message

Follow instructions in this webpage for:

i) Setup -> Creating a Slack app
Give this new slack app a name, Github Action (can change later)
Then, select the Development Slack Workspace, in my case here is Training. The app belongs to this workspace, leaving this workspace will remove your ability to manage this app. Unfortunately, this can't be changed later.

ii) Using the Action -> Posting the messages

Please note that Slack has reorganised the real estate of some of its functionalities. Bot User is now located under Basic Information section on the LHS bar.
- Go to Add features and functionality.
- Under Bot Token Scopes, add in OAuth scope of sending messages to slack with github push or pull request. This used to be called chat.postMessage but now is called chat.write. Select chat.write for add scope.
- Leave User Token Scopes, i.e. no need to fill in anything
- then, Install your app to your workspace.

iii) Under OAuth & Permissions, Bot User Token is generated (starting with xoxb-). Copy this token code.

2) Go to GitHub Actions section to create a new workflow. In new ymal file:

- Rename ymal file to
- Rename the workflow to 
- on: include both push and pull request, on the main branch
- Rename job to 
- After line with "steps:", remove all default given lines as we do not use them.
- Copy and past below 6 lines after "steps:" 
![image](https://user-images.githubusercontent.com/66695423/121761220-1b95cb00-cb61-11eb-8679-4b812c03be3e.png)
- In the last line of code, change the default "C1234567890" to our Slack channel id (last 10 digits in slack workspace-channel web address). This linked this github repo to the selected slack channel.
- I have changed my message that will show up in Slack as "Hellow World! Beautify Day!".

3) Go to Settings -> Secrets -> New repository secret -> Give secret a name (BOT_USER_TOKEN1) -> Paste the token code in step 1(iii) above in Value section.
This gives github access to slack account to send messages to slack when a push or pull request is made in github.

4) Last step, go to App section in Slack workspace, Training and select Github app we created in step 1. Go to Configure. 
Check that under Bot User, the Github Action section is set to link to #github-notification channel.

5) Vola! We're done with the setup. Now can test the automated workflow.
6) Make some changes to any files in this repo such as this README.md file.
7) Can look at Actions workflow progress and see a slack message show up in #github-notification channel, if the workflows are executed correctly.
![image](https://user-images.githubusercontent.com/66695423/121762046-2bfc7480-cb66-11eb-8363-743d7baded14.png)

8) Note that the 2 js files are for my own testing of code error in JS under nodejs.
9) Can see workflow files under .github/workflows folder.

Great thanks to this youtube link where I learn how to automate Github action workflows.
Learn how to create your own with [How to Use Github Actions to Automate Tests and Slack Notifications](https://www.youtube.com/watch?v=1n-jHHNSoTw)

