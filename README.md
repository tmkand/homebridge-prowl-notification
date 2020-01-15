
# Homebridge-Prowl-Notification

With this plugin, you can create any number of fake switches that, when turned on, will trigger a Prowl notification. 

For more information about Prowl notifications visit the [Prowl homepage](https://www.prowlapp.com).

## How to install

 * ```sudo npm install -g homebridge-prowl-notification```
* Create a platform with one or more switches in your config.json file
* Restart homebridge

## Example config.json:

 ```  "platforms": [
        {
            "platform": "ProwlNotification"
            "name": "Prowl",
            "apikey": "abcdef1234dcba4567",
            "defaultmsg": "%s has been triggered",
            "switches": [
                {
                    "name": "MyNote",
                    "subject": "Something happend",
                    "message": "but everything's still ok."
                    "priority": 0
                }
            ],
        }
      ]

```
This gives you a switch which, when turned on, will trigger a Prowl notification with the 
subject "Something happend" and the message "bbut everything's still ok."

```  "platforms": [
        {
            "platform": "ProwlNotification"
            "name": "Prowl",
            "apikey": "abcdef1234dcba4567",
            "defaultmsg": "%s has been triggered",
            "switches": [
                {
                    "name": "MyNote"
                }
            ],
        }
      ]

```
This gives you a switch which, when turned on, will trigger a Prowl notification with the 
subject "MyNote" and the message "MyNote has been triggered."

If there's no subject, the 'name' property of the switch is used as subject. If there's
no 'message' property, the defaultmsg will be used and the '%s' will be replaced with the
subject (or name if no subject). The '%s' is only working as a placeholder in 'defaultmsg'.
In 'message' it will be printed as '%s' and will not be replaced.

## Prerequiremant: A Prowl API key

In order to use this plugin you need the Prowl App for iOS and an API key. The iOS App Store
or the [Prowl homepage](https://www.prowlapp.com) has more inforamtion about the iOS app.
To get an API key you have to register at [Prowl](https://www.prowlapp.com) and then just
follow the directions outlined there on the 'API Keys' tab.

## Changing notification message

The notification text ('subject' and 'message') is read at runtime directly from homebrigde's
config.json. This allows you to easily change the notification by simply modifying config.json
and without the need to restart homebridge.

If you use the wonderful UI plugin [homebridge-config-ui-x](https://www.npmjs.com/package/homebridge-config-ui-x)
modifying will be even more easier. Just open the settings dialog of homebridge-prowl-notification
and make your changes. 
