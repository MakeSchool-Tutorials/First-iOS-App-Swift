---
title: "Connecting Objects"
slug: connecting-objects
---     

The time has finally come to start connecting the dots and connecting objects from the Interface Builder to our own code. 
Your code will connect with interface objects through *IBAction* and *IBOutlet* connections.

#Actions

You will create an `IBAction` when you need to send a message from an object to your code. A good example of this is when a user clicks a button.  This action by the user
will send a message to execute the function connected to the button. 

> [action]
> Open `ViewController.swift` and ensure your code reads as follows:
> 
>
    class ViewController: UIViewController {
>
        override func viewDidLoad() {
            super.viewDidLoad()
            // Do any additional setup after loading the view, typically from a nib.
        }
>    
        override func didReceiveMemoryWarning() {
            super.didReceiveMemoryWarning()
            // Dispose of any resources that can be recreated.
        }
>    
        // Let's handle the button
        @IBAction func buttonTapped(sender: AnyObject) {
            println("Ouch")
        }
    }

Great! You have created a new function that prints out a line of text to our debug window. However, by adding the `@IBAction` attribute to the function definition, it will now be accessible 
to the Interface Builder.  Notice the little empty circle in the code editor to the left of this function definition...

> [action]
> Select the `Assitant Editor` view
> ![image](ibaction_connection_1.png)

If you don't see the view shown above, you will need to change the right panel back to `Automatic`. You previously changed it to enable the Interface Builder preview mode.

![image](automatic_view.png)

#Connecting an Action

You now want to Connect your `IBAction` to the `Button`
 
> [action]
> Click on the circle beside the `@IBAction`, drag across to your `Button` (you will see a light blue line between the two), then let go.
>
> ![image](ibaction_connection_2.png)

That was easy! Notice that the previously empty circle is now filled in, and that hovering your cursor over this circle highlights the `Button`, confirming the connection.
You can also check out any Connections via the `Connection Inspector` panel.

![image](connection_inspector_1.png)

Great, let's see this in action.  Time to run the app...

> [action]
> Click the Button a few times and success, the *Debug Panel* will now start to fill up with your `Ouch` message.
> ![image](debug_1.png)

Excellent! Let's see how you handle yourself with outlets.

#Outlets

You will want to use an *IBOutlet* to enable your code to send a message to your user interface object. For example, changing the string of an interface label from your own code.

Time to try this out for yourself - see if you can:

> [action]
>
> 1. Add a label to your View 
> 2. Create a variable with attribute *IBOutlet* in your `ViewController` class that you will connect to your *UILabel*
> 3. Connect your View's Label to your code's label variable.
> 4. Have the label text change upon pressing the button.

=

> [solution]
> Your view *ViewController* should look something like this:
    class ViewController: UIViewController {
>        
        @IBOutlet var label: UILabel!
>
> Let's look at modifying the `buttonTapped` function to facilitate this.
>
    @IBAction func buttonTapped(sender: AnyObject) {
        println("Ouch")
        label.text = "wooo hoo"
    }
>

#Bonus Points
Have some fun; create other objects in your *View* and connect them. The best way to learn is to play.

#Debugging

Sometimes things go wrong in development. At times it can be challenging to find out why a certain piece of code isn't working.  Xcode has a nice Debugger and it's relatively easy to use.

Let's jump in by adding a breakpoint.

> [action]
> 1. Open `ViewController.swift`
> 2. Click on the left hand side of your code, across from `println("Ouch")`, you should see a blue highlight appear.
>![image](breakpoint_1.png)

Time to see it in action. 

> [action]
> 1. Run your App
> 2. Click on the Button in your App

Xcode will now change and you will be taken back into your code with debug mode enabled.  Your App has been effectively halted at the *Breakpoint* and is waiting to execute the `println` line of code.

![image](debug_view_1.png)

As you can see there is a lot of information disabled. We will be looking at the *Variables* view. Xcode will automatically present you with the variables in the current scope.

> [action]
> 1. Click on `self` to expand the current `ViewController` variable scope.
> 2. Right click on `label` and select `Print Description of "label"`

You will notice there is a handy quick view of your label. Notice the label text has not been changed yet as this line of code has not been executed yet.

![image](debug_2.png)

#Debug Stepping

Let's step through the code together.

> [action]
> 1. Press the `Step Over` button.  You will see your println code has now been executed and the output is in the debug window.
> 2. Press `Step Over` once again and then select `Print Description of "label"`. You will see this has been updated.

![image](debug_view_2.png)

Bring your Simulator back into view and you will notice the label hasn't changed...
This is because although the code has updated the labels text value, the App still needs to refresh its View to present this information.

> [action]
> 1. Select `Continue Program Execution`. It's the button beside `Step Over`

The App will resume running again and you will notice your Label has been updated.  If you select the button again, the breakpoint will 
be triggered and you will be taken back to the debug mode as before.

Now that we've touched briefly on a lot of key skills, the best way to further ingrain them is to practice, practice, practice...

Without further ado, let's take all of this new knowledge and start to build the *MakeSchool Notes App*.
