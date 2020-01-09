# The Utility of Delegates and Events in Unity


_Originally published at [timrodz.com](http://www.timrodz.com/blog/the-utility-of-delegates-and-events-in-unity/)._

**Update**: [@damagefilter](https://twitter.com/damagefilter/) wrote a more advanced tutorial regarding events in Unity. Go check it out [here](http://www.indiedb.com/members/damagefilter/blogs/event-and-unity) 😄.

¡Hola! My name is Juan Rodriguez. I am a Panamanian data & game developer and programmer based in New Zealand. This blog post was written for [notGDC](http://www.notgdc.fun/) as I wanted to contribute some of my knowledge with the community. It is aimed towards programmers looking to get the most out of Unity, no matter the skill level. The initial stages will be fairly basic as I want everyone to understand this tutorial, so feel free to skip parts as you wish! (Or just grab the [source code](https://github.com/timrodz/unity-callback_examples)). The tools I used are Unity [2017.3.1p2](https://unity3d.com/unity/qa/patch-releases/2017.3.1p2) and [Visual Studio Code](https://code.visualstudio.com/).

# 📩 What
In games, we often encounter situations where we want to notify objects about events that are happening without having to tie them together. Let’s consider the following situation. You have a UI system with:

-   An input field to write a message.
-   A button to send the message.
-   A field to display the message sent.

When the user clicks the ‘_Send Message_’ button, you want to inform the UI controller that a new message has been sent. After this, you will replace the current message with the new one. Lastly, the input field will be cleared up.

Here’s a GIF of how the game will look like:

![Simple, but works.](https://raw.githubusercontent.com/Mad-Hyrax/blog/gh-pages/assets/img/posts/notgdc_intro.gif)

# 📤 How
In order to achieve the desired functionality, we will approach the solution by implementing **delegates**. Delegates allow us to treat methods as variables, and they work like a mailing list. Subscribers will receive emails and can opt-out at any time. **Note**: You can subscribe as many methods as you desire. **Events** are very similar. The main difference is they add a layer of abstraction and protection on the **delegate** instance. This protection prevents clients of the delegate from resetting the delegate and its invocation list and only allows adding or removing targets from the invocation list ([Source](https://stackoverflow.com/questions/29155/what-are-the-differences-between-delegates-and-events)).

On the programming side, we are going to have two scripts: an event controller and a UI controller. The event controller will work as our mailing list, and it will have one event: **OnMessageUpdateRequest**. Since we want to replace our current message for the input field’s one, so this method will send out new message update requests.

The UI controller will have an **UpdateMessage** method subscribed to the **OnMessageUpdateRequest** event, and it will work as a _listener_. Also, to introduce you to **UnityEvents** we will play around with our Button and its capabilities, but we’ll get to that later. In essence: Delegates, Events and UnityEvents are very similar.

# 📨 Implementation

Inside Unity, create a new Scene and add the following objects to it:

-   Two Empty GameObjects. Rename them ‘_UI Controller_’ and ‘_Event Controller_’ respectively.
-   Right click on the hierarchy view:
    -   Choose **UI** → **Button**.
    -   Choose **UI** → **Input** **Field**.
    -   Choose **UI** → **Text**.

> **Note**: New UI objects will automatically add a **Canvas** and an **EventSystem** if your scene does not already have them inside. Why? because the **Canvas** displays UI elements and the **EventSystem** handles interactions from inputs that are not keys — They’re necessary to make any UI system work.

Your scene should look similar to this one:

![A very simple scene.](https://cdn-images-1.medium.com/max/1000/0*_T31weY-0J-2ovBf.png)

# Applying our solution

Once you have finished setting up your scene, it’s time to create the following C# scripts:

-   **UIController.cs**
-   **EventController.cs**

These scripts have the same names as our previously created Empty GameObjects. They will be attached to them as components.

## UIController.cs

Once you create the class, it should look similar to this snippet:

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class UIController : MonoBehaviour
{
    // Use this for initialization
    void Start() {}

    // Update is called once per frame
    void Update() {}
}
```

Since we’re working with UI, we need to include the _UnityEngine.UI_ library in order to access functionality of UI elements. Between lines **3** and **5**, add the following code snippet:

```csharp
using UnityEngine.UI;
```

After this is done, remove the **Update** method— We won’t be needing it. Now that we’ve got our UI library imported, we will proceed to create references to our UI objects in the scene. Inside the UIController class, add the following declarations before the **Start** method:

```csharp
public Button ButtonSendMessage;
public InputField InputField;
public Text MessageDisplay;
```

Now, we need to create two methods: **SendMessageUpdateRequest** and **UpdateMessage**. Inside UIController.cs, add the following lines of code:

```csharp
void SendMessageUpdateRequest() {}

void UpdateMessage(string _message) {}
```

If you’ve followed the steps correctly, your class should now look like this: [Gist url](https://gist.github.com/timrodz/db92598bed64de07ff71a1e772df79a2).

Head over to the Unity inspector. Click on the **UI Controller** GameObject and click on the ‘Add component’, from here you will add the _UIController_ script. Alternatively, you can also drag and drop the script into the GameObject. Once added, the UI Controller component will have three visible variables. After this, proceed to drag and drop the matching components inside the **Canvas** object.

> **Note**: The UI Controller **GameObject** holds **components** such as the Transform. The UIController script can be attached as a **component** to any **GameObject**. In this case, we’re attaching it to the UI Controller GameObject.

![Adding our components to the UI Controller.](https://cdn-images-1.medium.com/max/800/1*NvRgBceLTzj7ZQ39gkHFCA.gif)

Before going forward, we need to talk about **UnityEvents** and how we’re using them in this tutorial. If you click on the Button inside the canvas, you will see the following component:

![A button’s view in the Unity inspector.](https://cdn-images-1.medium.com/max/800/1*Kp3DWqTH84BeIZrMrBx9eA.png)

At the bottom of the component’s view, you see a **On Click ()** field with an empty list and a **+**/**-** sign. This is a **UnityEvent**: They allow you to add methods of objects in the current scene to to it! So, whatever methods you add here will be called when the button receives a click (**onClick**).

If the method you assign is not in the same hierarchy as the component (In this case, our button), its reference might get lost. This can create many undesired scenarios where you have to reassign methods over and over again. To combat this problem, we will add a listener to our Button’s **onClick** event via code. Inside the **Start** method, add the following line:

```csharp
ButtonSendMessage.onClick.AddListener(SendMessageUpdateRequest);
```

The **AddListener** method allows us to subscribe any of our classes’ functions to the desired event; in this case, it’s **onClick**. The parameter taken is of type _UnityAction_, which is essentially anything that is considered a method according to Unity. Now, everytime you click the ‘_Send Message_’ button, the **SendMessageUpdateRequest** method will be called, no matter the contents.

> **Note**: The **AddListener** method only accepts UnityEvents with no parameters, unless you add them via a Lambda expression.

## EventController.cs

Before going any further, we need to declare our delegate and implement its functionality.
Add the following declarations inside EventController.cs (and before the **Start** method):

```csharp
public delegate void OnMessageUpdateRequestDelegate(string _message);
```

Here we declare our delegate **OnMessageUpdateRequestDelegate**. In this part of the declaration, you specify the parameters it will have (no parameters is also valid). In our case, we are adding a string _message._

```csharp
public static OnMessageUpdateRequestDelegate OnMessageUpdateRequest;
```

We’re declaring **OnMessageUpdateRequest** as an _OnMessageUpdateRequestDelegate_. This is because delegates are methods treated as variables. Also, it’s static because we want to be able to access it from other classes without having to save a reference of the EventController (This is entirely optional, and it will vary heavily from your implementation/coding practices).

Now, replace the **Start** method for the following one:

```csharp
public static void Event_OnMessageUpdateRequest(string _message)
{
    Debug.LogFormat("-- EventController // Received a request to update message: {0}", _message);

    OnMessageUpdateRequest(_message);
}
```

**Final EventController.cs**
If you followed the steps correctly, your EventController class should look like this: [Gist url](https://gist.github.com/timrodz/21e7339f8dab8d3a0ac532b8012f274f).

## Back to UIController.cs

Now that our EventController code is ready, it’s time to continue working with our implementation. We now want to subscribe our **UpdateMessage** method to EventController’s **OnMessageUpdateRequest** delegate. Inside the Start method, add this line of code:

`EventController.OnMessageUpdateRequest += UpdateMessage;`

> **Note**: We did not use AddListener because delegates/events can simply add/remove listeners with the **+=**/**-=** operators. Also, a delegate can equal (=) one method whereas events cannot, they require use of **+=**/**-=** assignment operators.

Inside our SendMessageUpdateRequest method, we will store our message in a temporary string. We do this because we will call EventController’s **Event_OnMessageUpdateRequest** method:

```csharp
void SendMessageUpdateRequest()
{
    // Store the input field's text into a string
    string message = InputField.text;

    EventController.Event_OnMessageUpdateRequest(message);
}
```

If you recall EventController.cs, the contents of **Event_OnMessageUpdateRequest** method calls the OnMessageUpdateRequest delegate. Because **SendMessageUpdateRequest** invokes the event, and **UpdateMessage** is subscribed to the event, it will also be called.

## 🗳 Method call order

1. Button '_Send Message_’ **onClick** _UnityEvent_ calls **SendMessageUpdateRequest** (_subscriber_).
2. **SendMessageUpdateRequest** _method_ calls **Event_OnMessageUpdateRequest**.
3. **Event_OnMessageUpdateRequest** _method_ calls **OnMessageUpdateRequest**.
4. **OnMessageUpdateRequest** _delegate_ calls **UpdateMessage** (_subscriber_).

This may be confusing, so let me rephrase them in a more readable way: Because _method_ **SendMessageUpdateRequest** is subscribed to Button’s **onClick** _UnityEvent_, it will be called every time onClick is also called. Same goes for number 4: Because _method_ **UpdateMessage** is subscribed to delegate **OnMessageUpdateRequest**, it will be called every time **OnMessageUpdateRequest** is also called. Hope that eases things up!

Finally, we do follow the last steps: replace the message, and clear up the input field.

```csharp
void UpdateMessage(string _message)
{
    // Print the message
    Debug.LogFormat("-- UIController // Updating message: {0}", _message);

    // Replace our message display text with the contents of the message variable
    MessageDisplay.text = _message;

    // Reset the text of our input field
    InputField.text = "";
}
```

**Final UIController.cs**
If you followed all steps correctly, this is how your UIController class should look like: [Gist url](https://gist.github.com/timrodz/10534c89b7832a50d57dad7a54222a83)

Now, press play and **cross your fingers.** If all goes well, congratulations! If not, let me know what’s the issue and we’ll figure it out!

# 💌 Summary

---

We have learned about delegates, events and UnityEvents in Unity. They are useful variables that can help overcome many programming challenges. I hope you have enjoyed reading this [notGDC](https://twitter.com/notgdc) blog post.
