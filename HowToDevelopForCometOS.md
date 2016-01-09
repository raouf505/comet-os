# Introduction #

Comet OS is in fact, a platform like Windows or Mac...just it's written differently than other Operating Systems.  While it is not possible to make apps that you can download and install right into Comet OS, you can download the source code, add your program, and re-distribute your very own version of Comet OS complete with all of the programs you want to see in it.  Here's how:

Download the latest source code from the downloads page(make sure you have
Visual Basic 2010) and open it up by opening Comet OS.sln.  After you do that you should see the source code.



# Details #

Setting up a window:

Go to the solution explorer and right click on Comet OS at the top of the window and then go to add, windows form.  Name it whatever the heck you want.  After that, you should see a blank windows form, go to properties and make TopMost true, ShowInTaskBar false, ShowIcon to false, FormBorderStyle to none, backcolor to black, BackGroundImageLayout to none, and backgroundimage to gradient(NOT gradient3!)  boom, there you have the basics of a Comet OS window.  Next step...adding the buttonz.  Go to any random form(Use clef I guess) and copy and paste the x button from it onto your window.  Double click on the button and add the code: Me.Visible = False, then go to the label properties, events and go down to MouseEnter and add the code: LabelWhateverTheFreakingNumberIsIDontReallyCare.ForeColor = Color.DimGray

And in MouseLeave add: LabelWhateverTheFreakingNumberIsIDontReallyCare.ForeColor = Color.Black

There you go, a close button.  Now take the window name label from Clef and paste it into your window, change the text to anything.

Ok, now for the hard part.

In the window code, go up to right under Public Class and add these variables:
Dim drag As Boolean
Dim MouseX As Integer
Dim MouseY As Integer

Now go back to the designer and in the form events go to MouseDown and add this code:
drag = True
> MouseX = Windows.Forms.Cursor.Position.X - Me.Left
> MouseY = Windows.Forms.Cursor.Position.Y - Me.Top
> Me.Opacity = 0.9
And in MouseMove add this code:
If drag Then
> > Me.Top = Windows.Forms.Cursor.Position.Y - MouseY
> > Me.Left = Windows.Forms.Cursor.Position.X - MouseX

> End If
Now go to MouseUp and add this:
drag = False
Me.Opacity = 1

In form activate add:
Me.Opacity = 1

and in form deactivate add:
Me.Opacity = 0.5

There!  Your form is pretty much good to go except it is required that all windows make a console log entry and show up in the appCache manager.

In form load add this:
Console.CommandLog.Items.Add("Opened yourProgramName at " & TimeOfDay)
Settings.CachedApps.Items.Add("Process::yourProgramName")

and in form closed add:
Console.CommandLog.Items.Add("Process terminated at " & TimeOfDay)
Settings.CachedApps.Items.Remove("Process::yourProgramName")

Make sure that your program gets cached at startup by going to Loading.vb and adding to the initializeAppCaching() Sub under About.Visible = False:
yourProgramName.Show()
yourProgramName.Visible = False()

and go to settings and add to the Clear Cache button code:
yourProgramName.Close()

and to the End Process button add an ElseIf like this:
ElseIf CachedApps.SelectedItem = "Process::yourProgramName" Then
> yourProgramName.Close()

There you go! You should be all set to write your program in Comet OS!  Hope to see your distro around!