# SlackMonitor
A simple slack app to allow only certain users to post in a channel

This app is meant to run as an Amazon AWS Lambda function. So you need to set that up, as well as the AWS API Gateway.

The Lambda function requires the following environment variables (don't hardcode API keys!):
SLACK_API_TOKEN - the API token of your app. Your app requires the chat:write:user permission scope.
SLACK_CHANNEL_ID - the channel we are planning to write into, can be the ID or name (I prefer the ID, in case someone changes the name)
SLACK_CHANNEL_TOKEN - the channel token that is being sent by the Outgoing Webhook, to make sure we get the message from the 
USERS_ALLOW - a comma separated list of users that are allowed to post

Your Lambda function setup should look something like this:
![Lambda Code](https://raw.githubusercontent.com/flipswitchingmonkey/SlackMonitor/master/img/2017_07_14_13_24_58_Lambda_Management_Console.png)


![Lambda Config](https://raw.githubusercontent.com/flipswitchingmonkey/SlackMonitor/master/img/2017_07_14_13_27_20_Lambda_Management_Console.png)

Your API Gateway Integration Request mapping should be similar to this. The mapping template (originally from https://forums.aws.amazon.com/thread.jspa?messageID=673012) is in the repo as well. 

![API Gateway](https://raw.githubusercontent.com/flipswitchingmonkey/SlackMonitor/master/img/2017_07_14_13_28_53_API_Gateway.png)
