# Remove-Duplicate-Values-in-a-Row
Delete the duplicate applications(app_0 to app_20) recorded from different sensors, merge them for each unique user.

Raw data


Approaches:
1. The FuzzyWuzzy Package by calculating the Levenshtein Distance:

https://www.datacamp.com/community/tutorials/fuzzy-string-python
https://www.youtube.com/watch?v=4L0Py4GkmPU
Result: Fail. 
Reason: Only can calculate the ratio. Cannot delete the duplicate values in the csv.

2. Dedupe 

https://dedupe.io/
Result: Fail. 
Reason: A ML tool, used to train data.

3. Excel: Remove Duplicates dialog box

https://www.howtoexcel.org/tutorials/remove-duplicates/
Result: Fail. 
Reason: Only can be applied between different rows, not columns. 

4. Excel: VBA

http://www.officexr.com/etagid57093b0/
https://superuser.com/questions/879567/identify-and-delete-duplicate-values-in-single-row
Result: Haven't tried

5. Python: Loop

https://stackoverflow.com/questions/22082680/remove-duplicate-cells-in-a-row
Result: Haven't tried

6. Pandas

(1) Cleaning data: Replace the similar values

mobile - com.kodarkooperativet.blackplayerfree ~ com.kodarkooperativet.blackplayerfree
mobile - com.samsung.android.messaging ~ com.samsung.android.messaging
mobile - com.appeaseinc.todolist135 ~ 135 Todo List 15
mobile - com.spotify.music 212 / spotify 587 ~ Spotify
mobile - com.samsung.android.calendar ~ com.samsung.android.calendar 159
mobile - com.lifx.lifx 6/ lifx 11 ~ LIFX
Twitter for Android/twitter.com 45 ~ Twitter
WhatsApp Messenger Android ~ WhatsApp Messenger 553
Messenger for Android ~ Messenger 97
Snapchat for Android ~ Snapchat 54
PowerPoint for Tablet/Microsoft PowerPoint ~ PowerPoint 122
Google Chrome for Android 568/ Google Chrome 1289/google.com 775 ~ Google
GMail for Android ~ Gmail 612
drive.Google ~ Google Drive 145
Google Maps for Android ~ Google Maps 197
Google /calendar 78 / Google calendar 394 ~ Google Calendar
Adobe Reader Android ~ Adobe Reader 12
youtube.com ~ Youtube 69
Facebook for Android 426/facebook.com 154 ~ Facebook
Instagram for Android 452
Slack for Android 119
outlook.office.com 278/Microsoft Outlook 270/Outlook for Android 115/outlook.office365.com 29/ MS Outlook 562 ~ Outlook
teams.microsoft.com ~ Microsoft Teams 65
zoom.us ~ zoom 6
LinkedIn - Android 77 ~ LinkedIn

(2) Code: 

https://stackoverflow.com/questions/43898903/delete-duplicate-values-in-a-row-of-pandas-dataframe

mask = df.apply(pd.Series.duplicated, 1) & df.astype(bool)

df1=df.mask(mask, 0)

df1

