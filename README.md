## **Unity3D - Discord Rich Presence**
a Discord Rich Presence Framework for your game (Unity3D Game Engine)

#
## **About**
this Framework is my Open Source Framework using DiscordRichPresenceSDK package

#
## **Getting Started**
First, copy Assets folder, and Place to your Unity Project

Go to Discord [Developer Application](https://discord.com/developers/applications/) and make a New Application

![alt img](https://cdn.discordapp.com/attachments/784761936230744074/943572752785354802/unknown.png)

Then go to **OAuth2** > **General**

![](https://cdn.discordapp.com/attachments/784761936230744074/943576587901743164/unknown.png)

After that go to **Redirect** section and click **Add Redirect**

![](https://cdn.discordapp.com/attachments/784761936230744074/943577086914871376/unknown.png)

Put the redirect link that we want to use, which is **http://127.0.0.1** then click **Save Changes** on the bottom

![](https://cdn.discordapp.com/attachments/784761936230744074/943577855026147488/unknown.png)

Go to your Unity Project, then open  the script located at **Assets/Script/DiscordController.cs**
```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using Discord;

public class DiscordController : MonoBehaviour
{
    public Discord.Discord discord;

    public string sClientId, sDetails, sState, sLargeImage, sLargeText, sSmallImage, sSmallText;

    void Start()
    {
        discord = new Discord.Discord(/*PUT_YOUR_CLIENT ID_HERE*/, (System.UInt64)Discord.CreateFlags.Default);
        var activityManager = discord.GetActivityManager();
        var activity = new Discord.Activity
        {
            Details = sDetails,
            State = sState,
            Assets = 
            {
                LargeImage = sLargeImage,
                LargeText = sLargeText,
                SmallImage = sSmallImage,
                SmallText = sSmallText
            },
        };
        activityManager.UpdateActivity(activity, (res) => {
            if (res == Discord.Result.Ok)
                Debug.Log("Discord status set!");
            else
                Debug.LogError("Discord status failed!");
        });
    }

    void Update()
    {
        discord.RunCallbacks();
    }
}
```

Change the __/* PUT_YOUR_CLIENT_ID_HERE */__ with your CLIENT ID, CLIENT ID is located on **OAuth2** > **General**

![](https://cdn.discordapp.com/attachments/784761936230744074/943582726097862676/unknown.png)

After that, you can attach **DiscordController.cs** script to any GameObject on your Scene.

This is How to Configure your Discord Rich Presence Status

- **S Details** is for Details
- **S State** is for State
- **S Large Image** is for Large Image Name that you upload on Discord Developer Application **Rich Presence** > **Art Assets** > **Rich Presence Assets**
- **S Large Text** is for text details on Large Image
- **S Small Image** is for Small Image Name that you upload on Discord Developer Application **Rich Presence** > **Art Assets** > **Rich Presence Assets**
- **S Small Text** is for text details on Small Image

![](https://cdn.discordapp.com/attachments/784761936230744074/943585070403424318/unknown.png)

****You can see how to putting an image down below on Optional Section***

#
## **Here is the result**

Discord RP Preview

![](https://cdn.discordapp.com/attachments/784761936230744074/943584812512469042/unknown.png)

#
## ***This is optional*** 
After that go to **Rich Presence** > **Art Assets**

![](https://cdn.discordapp.com/attachments/784761936230744074/943579215855501392/unknown.png)

Then click on **Rich Presence Invite Image** for changing Invite Image or **Rich Presence Assets** for changing RPS Image

![](https://cdn.discordapp.com/attachments/784761936230744074/943579702428307456/unknown.png)

**Examples**

![](https://cdn.discordapp.com/attachments/784761936230744074/943586620714659900/unknown.png)

****remember, file name is used on Unity Inspector***