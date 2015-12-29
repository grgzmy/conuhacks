# ConUHack Marketplace

AppDirect's API challenge may be a little different than what you are accustomed to. Rather than providing you with an API endpoint, we will ask your team for an endpoint for us to contact you!

This type of API "hook" is a common pattern used in integration scenarios between systems. Much of AppDirect's billing integration and event functionality works that way. Rather than having an API client poll for changes or events happening in a third party system, you reverse the roles: don't call us, we'll call you.

For ConUHacks, we have created a system that enables participants to register their team members & hackathon projects into a demonstration marketplace. It is in a sense a miniature version of how AppDirect works.

When you implement the endpoint correctly, your application & team will show up on the marketplace with the information you have provided to us. The more information you provide, the better your profile on the marketplace will look.

The marketplace is visible to everyone at https://conuhacks.appdirectondemand.com.

## Register your endpoint

Visit https://conuhacks.appdirectondemand.com/register and follow the instructions on screen. You will be asked to enter a valid URI. Periodically during the day our server will make requests to all registered endpoints.

## Response

The server will make a `GET` request to your URI and expect a response with a status code of `200 OK`, and a content type of `application/json`.

The response you return should be in the following format:

```javascript
{
	teamName: "Your team name",
	projectName: "Your project name",
	// We fully understand that this URL will be broken most of the time :)
	projectUrl: "http://yourproject.com"
	members: [{
		name: "Team member #1",
		// The email will be used to display a GRAVATAR
		email: "member1@team.com",
		title: "Whatever title you want :)"
	}, { ... }]
}
```
