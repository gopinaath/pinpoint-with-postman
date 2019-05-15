# pinpoint-with-postman -- sample

First, configure Postman with AWS Creds - API Key, API Secret, Region.  Ensure that the credential has privileges to execute Pinpoint APIs.  

https://docs.aws.amazon.com/pinpoint/latest/developerguide/tutorials-using-postman-iam-user.html
https://docs.aws.amazon.com/pinpoint/latest/developerguide/tutorials-using-postman-configuration.html

https://docs.aws.amazon.com/cli/latest/reference/pinpoint/send-messages.html

![Screenshot](page-2.png)


Please note that the following schema does not have ```SenderId``` and ```Substitutions```.  ```SenderId``` is not used in the US.  ```Substitutions``` is needed only to dynamically replace text in the message.

```
{
  "Addresses": {
    "+1<<Customer US Phone Number>>": {
      "ChannelType": "SMS"
    }
  },
  "MessageConfiguration": {
    "SMSMessage": {
      "Body": "SMS-Body-1-from ..",
      "Keyword": "<<Pinpoint Keyword>>",
      "MessageType": "TRANSACTIONAL",
      "OriginationNumber": "+1<<Pinpoint US Phone Number>>"
    }
  }
}
```

*** AWS CLI
```
aws pinpoint send-messages --debug --region us-west-2 --application-id <<Pinpoint-project-ID>> --message-request '{"Addresses": {"+<<Customer Phone Number>>":{"ChannelType": "SMS"}}, "MessageConfiguration": {"SMSMessage": {"Body": "SMS-Body-1", "Keyword": "<<Pinpoint Keyword>>", "MessageType": "TRANSACTIONAL", "OriginationNumber": "+<<Pinpoint US Phone Number>>", "SenderId": "MySenderID"}}}'
``` 
