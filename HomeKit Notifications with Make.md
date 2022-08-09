# How to setup Make (Integromat) webhook notifications for HomeKit
-----
### Items required:
- Account with Make (free) available to create at [https://www.make.com](https://www.make.com/)
- [Integromat app (free)](https://apps.apple.com/app/id1177073656) on the device in which you want to receive notifications - this is still the app Make is using right now, it may change to a Make app later
- [HomeKit home hub](https://support.apple.com/en-us/HT207057) for the notifications to be triggered, but can still work in other situations as well

### Setup Make Scenario
1. While logged into Make.com, click / tap on the plus button to create a new scenario ![https://imgur.com/u5uU900](https://i.imgur.com/u5uU900.jpg)
2. Click / Tap the plus symbol in the new scenario to add items and search the list for webhook![](https://i.imgur.com/zexWoNw.png)![](https://i.imgur.com/JTOH4rn.jpg)
2. Select "Custom webhook"![](https://i.imgur.com/bHnOlCp.jpg)
3. Now that the webhook item is available to receive traffic, we have to setup the webhook parameters.
4. Tap / Click the add button in the webhook item's window that appeared ![](https://i.imgur.com/rMSX206.jpg)
5. Give the webhook some name you prefer i.e. My HomeKit Webhook)![](https://i.imgur.com/g4BLaO7.jpg)
6. Tap / Click Save
8. You will see that the webhook has been created and the URL is shown in the window as well as a copy address to clipboard button available (save this somewhere like a note so you can use it easily in your automations / shortcuts. We will get to that part soon.)![](https://i.imgur.com/kviBR6U.jpg)
9. Tap / Click OK
10. Tap / Click the node on the right side to add another node to the scenario![](https://i.imgur.com/BRT7Kk2.jpg)
11. Search the list for iOS and select "Apple iOS"![](https://i.imgur.com/VchxumW.jpg)
12. Select Send a Push Notification![](https://i.imgur.com/3LZGwMm.jpg)
13. Now the iOS device needs to be added to your Make account
14. Tap / Click the Add button![](https://i.imgur.com/d5jvn9W.png)![](https://i.imgur.com/Wldca2d.png)
15. Now would be the time to tap the App Store button to install Integromat unless you already have the app installed.
16. Once in Integromat, make sure you login with the same account as you use on Make and go to the scanner to scan the QR code to register your device to your account and provide a name![](https://i.imgur.com/soH6hPS.jpg)
17. In the notification options, enable "Get request headers" and "JSON pass-through"![](https://i.imgur.com/xlsZ5i4.png)
18. You will need to collapse some of the option items to see the button to OK / Save the changes if you are on a mobile device
19. Now we can setup the data structure that the webhook will receive. Thanks to their easy process, we can do this quickly with a shortcut. I preferred to set it up with a form entry named "item" and then the value for "item" is what the notification displays. This allows for customized notifications to be sent easily.
	1. Using the webhook URL we copied earlier, we will now create a shortcut. 
	2. Create a new shortcut and add a "Get Contents of URL" action using the webhook url as the address, the method needs to be set to "POST" and the Request Body set to "Form"
	3. Add a new field to the Request Body with the name of "item" and the value can be whatever message you like for this initial test (later, this will be the relevant message you want displayed)![](https://i.imgur.com/mdQajhU.jpg)
	4. Going back to Make, you can tap / click the button in your webhook window to determine the data structure. After tapping / clicking that, it will wait for the data to be delivered
	5. In your shortcut, press the play button in and you should see the result say "Accepted"
	6. Looking back at Make, you should now see a "Successfully Determined" message, indicating that the webhook now knows your data structure![](https://i.imgur.com/t5CKK0T.jpg)![](https://i.imgur.com/aRZBbbI.jpg)
20. In the Apple iOS mode of the scenario, we can now ensure the device name is selected and enter the information desired into the notification fields. You should see a red / maroon colored item named "item" because we made it learn the data we are sending. Tap / Click that when entering text into the Title of the notification![](https://i.imgur.com/emtmc5J.png)
21. Click OK and save the Scenario
22. You can press the run button on the Scenario to test it and it will wait for data, you can use the shortcut again to see the notification delivered on your device
23. The final step is to enable the Scenario so it will always be on. Tap / Click the toggle switch and you should be good to go. Any notifications you want to see, just need a Get Contents of URL action with the webhook URL added and the form data we used earlier. TIP: you can tap the upper left of the action used in the example shortcut and paste it into your HomeKit automations to make it easier![](https://i.imgur.com/MioFPdt.jpg)
