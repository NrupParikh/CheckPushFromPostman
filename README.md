# Check Push From Postman


FIREBASE NOTIFICATION CHECK
---

- Request Type :  POST
- URL : https://fcm.googleapis.com/fcm/send


Headers
---
- Authorization:  "key=YOUR_Firebase_KEY"
- Content-Type : application/json

- **Example of Firebase Key**
- key=AAAANzv_N2A:APA91bHFK5EoObgzP41qZ_R_oj-VG-6GUp7y-HYcbJFTKee2u1UaMokMdSIIpxH613FEaz3KL3wla5uLddL0sSqEGGET2IlunphnsDu12TF4914-yzuwMjrrHsZ7k8qHkLvXJHlkho81


Body [ JSON ] 
---

~~~
{
    "to": "<FIREBASE_TOKEN>",
    "data": {
        "body": "Test Body",
        "title": "Test Notification Title",
        "key_1": "Value for key_1",
        "key_2": "Value for key_2"
    },
    "notification": {
        "body": "New announcement assigned",
        "OrganizationId": "2",
        "content_available": true,
        "priority": "high",
        "subtitle": "Elementary School",
        "title": "hello"
    }
}

### Example of FCM Token
- f9iTLySfQUuD_F38o945_y:APA91bHD1twz3LN0wRYuKrEIjlhJOk77gtAGsyI0AWOaYJD1zSNlW2nCINfZvEmQHzgq5HEJTSVoNg3L6TFqaZ6_rwWMzXNa4n1b1FZf2BpgrWeCdO09baNfzw5Lm10BlSgG3qfqtdT8


~~~

### NOTE : target Android 13 or higher [ Required Runtime permission for notification ]

~~~
<uses-permission android:name="android.permission.POST_NOTIFICATIONS"/>
~~~

### In Fragment onViewCreated()
~~~
    private fun checkNotificationPermission() {
        if (Build.VERSION.SDK_INT >= 33) {
            if (ContextCompat.checkSelfPermission(
                    requireContext(),
                    Manifest.permission.POST_NOTIFICATIONS
                ) != PackageManager.PERMISSION_GRANTED
            ) {
                ActivityCompat.requestPermissions(
                    requireActivity(),
                    arrayOf(Manifest.permission.POST_NOTIFICATIONS),
                    101
                );
            }
        }
    }


// Also set pending intent in Firebase messaging code

        var intentFlagType = PendingIntent.FLAG_ONE_SHOT
        if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.S) {
            intentFlagType = PendingIntent.FLAG_UPDATE_CURRENT or PendingIntent.FLAG_IMMUTABLE;  // or only use FLAG_MUTABLE >> if it needs to be used with inline replies or bubbles.
        }
        val pendingIntent =
            PendingIntent.getActivity(this, 0, intent, intentFlagType)
~~~
------------------------------------------------------------
### Reference
- https://developer.android.com/develop/ui/views/notifications/notification-permission
- https://stackoverflow.com/questions/38834020/sending-push-via-postman-using-firebase-messaging/55795189#55795189
