# ConUHack Marketplace

AppDirect's API challenge is going to be a little different than what you are accustomed to. Rather than providing you with an API endpoint for you to use, we will ask you for an endpoint for US to contact your application.

This type of API hook is a common pattern used in integration scenarios between systems. Much of AppDirect's billing and event functionality works that way.

For ConUHack, we have created a system that enables teams to register their hackathon project and team into a demo marketplace.

When you implement the endpoint correctly, your application & team will show up on the marketplace with the information you have provided to us.

The marketplace is visible to all at https://conuhacks.appdirectondemand.com.

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

