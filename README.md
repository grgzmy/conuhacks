# ConUHack Marketplace

AppDirect's API challenge may be a little different than what you are accustomed to. Rather than providing you with an API endpoint, we will ask your team for an endpoint for us to contact you!

This pattern is sometimes called a [webhook](https://en.wikipedia.org/wiki/Webhook). It is particularly useful for real-time integration scenarios between systems. Much of AppDirect's billing and event functionality works that way. Rather than having a client poll for events happening in a third party system, you reverse the roles: don't call us, we'll call you.

For ConUHacks, we have created a system that enables participants to register their team members & hackathon projects into a demonstration marketplace. It is in a sense a miniature version of how AppDirect works.

When you implement the endpoint correctly, your application & team will show up on the marketplace with the information you have provided to us. The more information you provide, the better your profile on the marketplclop;kmn ace will look.

The marketplace is visible to everyone at https://conuhacks.appdirectondemand.com.

## Register your endpoint

Visit https://conuhacks.appdirectondemand.com/register and follow the instructions. You will be asked to enter a valid URI. Our server will periodically make requests to all registered endpoints. You will receive a secret key. Keep it to yourself!

## Response

The server will make a `GET` request to your URI and expect a response with a status code of `200 OK`, and a content type of `application/json`.

The response you return should be in the following format:

```javascript
{
	teamName: "Your team name",           // These two fields are mandatory. The rest is optional!
	projectName: "Your project name",     // 
	projectPicture: 'http://imgur.com/yourproject.jpg',   // Make it square ideally
	teamPicture: 'http://imgur.com/yourteam.jpg`, 
	
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

- Images may be in any web compatible format. Animated .gif anyone? :)
- Please, nothing offensive. Remember the Major League Hacking [code of conduct](http://static.mlh.io/docs/mlh-code-of-conduct.pdf).
