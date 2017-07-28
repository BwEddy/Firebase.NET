## Welcome to Firebase.NET  [Official site](https://urimkurtishi.github.io/Firebase.NET/)

Firebase.NET implements Firebase Cloud Messaging HTTP Protocol that enables sending notifications to Android, iOS and Web clients through Firebase Cloud Messaging.

It is a small and lightweight .NET client library written entirely in C# with high performance and reliability. It provides handling mechanism and retry provider (implementing exponential backoff algorithm) for response messages returned from FCM servers. It has been tested and it’s used by different companies and projects.

### How to use Firebase.NET

Below is a sample on pushing notifications to your client apps through Firebase.NET

```csharp
using Firebase.NET.Messages;
using Firebase.NET.Notifications;

string[] ids = {
    //registration tokens here
};

var requestMessage = new RequestMessage
{
    Body =
    {
        RegistrationIds = ids,
        Notification = new CrossPlatformNotification
        {
            Title = "Important Notification",
            Body = "This is a notification send from Firebase.NET"
        },
        Data = new Dictionary<string, string>
        {
            { "leage", "UEFA" },
            { "game", "Albania vs Kosovo!" },
	    { "score", "1:1" }
        }
    }
};
       
var pushService = new PushNotificationService("yourFcmServerKey");
var responseMessage = await pushService.PushMessage(requestMessage);

```

### Installation

Firebase.NET library can be downloaded directly from github and build within your project or it can be installed through [NuGet Package Manager](https://www.nuget.org/packages/Pantheon.Firebase.NET/1.1.0).


### Dependencies
* Newtonsoft.Json 10.0.3

### Documentation

Check out our [documentation](https://urimkurtishi.github.io/Firebase.NET/#firebasenet-library) for more information and tutorials on how to use Firebase.NET library.
