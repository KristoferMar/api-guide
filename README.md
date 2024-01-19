# API-Guide

### API Call back endpoint
A callback URL will be invoked by the API method you're calling after it's done. So if you call

```
POST /api.example.com/foo?callbackURL=http://my.server.com/bar
```

The callback URL is like that return envelope. You are basically saying, "I am sending you this data; once you are done with it, I am listening on this callback URL waiting your response." So the API will process the data you have sent then look at the callback to send you the response.

This is useful because sometimes you may take ages to process some data and it makes no sense to have the caller wait for a response. For example, say your API allows users to send documents to it and virus scan them. Then you send a report after. The scan could take maybe 3 minutes. The user cannot be waiting for 3 minutes. So you acknowledge that you got the document and let the caller get on with other business while you do the scan, then use the callback URL when done to tell them the result of the scan.
