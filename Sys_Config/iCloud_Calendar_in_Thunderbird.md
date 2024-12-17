# How to add an Apple calendar to Thunderbird?

In order to add an Apple iCloud calendar to Thunderbird, two things are needed :
1. An App-specific password
2. A CalDav URL allowing to access this specific calendar

## How to generate an App-specific password

Go to icloud.com
Sign-in with the account whose calendar is meant to be used with Thunderbird
On the top-right angle of the webpage, click on the icon of the account.
A menu pops-up
Select "Manage Apple Account"
This should open a new window, most likely after a new authentication has been asked from you (usually password and 2nd factor, but if you had already logged in not too long before, it may only be the second factor)
In the new window, choose "Sign-in and Security" (left side of the webpage)
A new page is loaded
At the bottom-right there is a box with "App-specific Passwords". Click on it.
This will open a pop-up
Click on "+"
A dialog box appears, that requires you to fill a name for this specific app. For example, you can use "<machine-name>-Thunderbird-calendar"
It may then ask for your icloud password (not always)
Then a new box appears with the following content : 
"Your app-specific password is:
dssu-zzkt-lkgf-xwde
Enter this password into the password field of the app you would like to sign in to. Password is case-sensitive."
BEFORE CLICKING ON DONE, please copy-paste this password in your password manager, as it won't be displayed anymore to you on the dedicated Apple Account management page.
You'll have to enter this password when configuring the calendar in Thunderbird

## How to identify the CalDav URL specific to your calendar

In a **Firefox** web browser, connect to the online icloud calendar : https://www.icloud.com/calendar/
Right-click on the page once it has been loaded, and select "Inspect".
Select the Network tab in the Inspector frame that appears (usually at the bottom of the web page).
In the box containing "Filter URLs" in light gray, type "collections".
Unselect and select the Calendar you are interested in (in the left column of the icloud calendar page, where all the available calendars are listed). If the said calendar wasn't already selected, you simply need to select it once.
Select the first POST Url in the list of results. You should see a box with the headers on the right side of the Inspector window. The POST URL is displayed at the top of this box, and should start with something like : https://pXXX-calendarws.icloud.com/ca/collections/ where XXX is a number. 
Please record somewhere this XXX.
Then, still in the URL, and just after the part described precedently, there is a set of numbers, capiltal letters and hyphens. An example could be the following : 2D09C7510-6F91-3B81-9116-C5DFE4056A83
This number is the "guid". Please record it along with the XXX.
Finally, and still in the same URL, there should be a field name "dsid", displayed in the following way : dsid=4799369245. Record it with the guid and XXX.
You can now create the needed URL. It's format is https://pXXX-caldav.icloud.com/dsid/calendars/guid
With the examples above, it should be : https://p218-caldav.icloud.com/4799369245/calendars/2D09C7510-6F91-3B81-9116-C5DFE4056A83


## How to configure the calendar in Thunderbird

In Thunderbird, select the calendar. At the bottom left, click on "New Calendar". A pop-up window will appear, which should be titled "Create New Calendar". On it, choose the radio button "On the Network" then click on Next.
On the next screen, enter your username for the calendar you wish to add. The location is the URL of the calendar. Here you'll use the CalDav URL identified above.
Once it's done, click on "Find Calendars" (Bottom-right of the window). A pop-up will appear, titled "Authentication Required - Mozilla Thunderbird". Fill the corresponding text box with the App-specific password generated above.
You should be able to finalize the configuration by selecting which calendars should be displayed, if there are several calendars associated with the account.
