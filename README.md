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


~~~

### NOTE : target Android 13 or higher [ Required Runtime permission for notification ]

~~~
<uses-permission android:name="android.permission.POST_NOTIFICATIONS"/>
~~~

### Example of FCM Token
- f9iTLySfQUuD_F38o945_y:APA91bHD1twz3LN0wRYuKrEIjlhJOk77gtAGsyI0AWOaYJD1zSNlW2nCINfZvEmQHzgq5HEJTSVoNg3L6TFqaZ6_rwWMzXNa4n1b1FZf2BpgrWeCdO09baNfzw5Lm10BlSgG3qfqtdT8

------------------------------------------------------------
### Reference
- https://developer.android.com/develop/ui/views/notifications/notification-permission
- https://stackoverflow.com/questions/38834020/sending-push-via-postman-using-firebase-messaging/55795189#55795189
