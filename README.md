# iOS-Programming-tips

In general, this is what I do:

1) ViewDidLoad - Whenever I'm adding controls to a view that should appear together with the view, right away, I put it in the ViewDidLoad method. Basically this method is called whenever the view was loaded into memory. So for example, if my view is a form with 3 labels, I would add the labels here; the view will never exist without those forms.

2) ViewWillAppear: I use ViewWillAppear usually just to update the data on the form. So, for the example above, I would use this to actually load the data from my domain into the form. Creation of UIViews is fairly expensive, and you should avoid as much as possible doing that on the ViewWillAppear method, becuase when this gets called, it means that the iPhone is already ready to show the UIView to the user, and anything heavy you do here will impact performance in a very visible manner (like animations being delayed, etc).

3) ViewDidAppear: Finally, I use the ViewDidAppear to start off new threads to things that would take a long time to execute, like for example doing a webservice call to get extra data for the form above.The good thing is that because the view already exists and is being displayed to the user, you can show a nice "Waiting" message to the user while you get the data.

#define or const for global string

The #define is a pre-processor macro. That means that it basically goes through your code and replace your macro with what you've defined.
If you use a const, it's going to be a pointer to the string in memory. It's way more efficient than having the same string being allocated wherever/whenever it is used.
