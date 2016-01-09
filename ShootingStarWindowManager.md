# Introduction #

I created the Shooting Star Window Manager to be efficient, and useful.


# Details #

Shooting Star must be written manually, here is a quick tutorial how.  First off, go to the form you want to be able to move.  Next, add these three variables at the top of the form code:

Dim drag As Boolean

Dim mouseX As Integer

Dim mouseY As Integer


After that, go to the form's MouseDown event, add the following code:

drag = True

mouseX = Windows.Forms.Cursor.Position.X - Me.Left

mouseY = Windows.Forms.Cursor.Position.Y - Me.Top

This is where efficiency comes into play, what this is doing is when you click on the window, it sets the variables.

Now go to the forms MouseMove event, add the following code:

If drag Then

> Me.Opacity = 0.9

> Me.Top = Windows.Forms.Cursor.Position.Y - mouseY

> Me.Left = Windows.Forms.Cursor.Position.X - mouseX

> End If

This changes the variables as you move the mouse while drag is true, it will also make the window become slightly transparent (this is optional)

Finally, in the MouseUp event, add the following code:

drag = False

Me.Opacity = 1

This simply releases the variables and resets the transparency (also optional)

That's it!  Now you've got the Shooting Star Window Manager implemented into your program!  Remember to add credit in your code as a comment that you're using the free and open source window manager made by Cody Zusman!

Have a good day.