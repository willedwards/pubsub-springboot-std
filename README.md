# Getting started on Google Cloud Platform for Java® 

##This is a demo for STANDARD AppEngine and google pubsub ![Build Status](https://travis-ci.org/willedwards/pubsub-springboot-std.svg?branch=master)

>mvn clean install


You now need to replace YOUR_PROJECT_ID in the following files:

application.properties          (appengine.projectId=YOUR_PROJECT_ID)

application-web.xml

======================


The idea, is that an appengine can send and receive messages asynchronously using GCloud pub sub.

This can then be used as a basis for microservices using multiple appengines, each with their own datastore.

To test it out: ensure you have a projectID set up in gcloud.
( To see this, type the following in your terminal )

``` > gcloud config list ```

run

```> mvn gcloud:deploy```

This will push the code remotely to https://<projectId>.appspot.com


The project uses Swagger as the endpoint so you can open your browser at:

https://yourprojectId.appspot.com/swagger-ui.html

You can create topics and subscriptions with ease, and list them.

Once a subscription is created, then register it via /register/callback on the swagger ui.

Then click the /send/{topic}/{message} GET

So

1) Open the pub-sub-controller (from the above link)

2) POST /topic, and you can make this : 
```
{
  "topicPrefix": “customTopic"
}
```
Hi try it out (then call GET /topic to see it’s there).

3)  POST /register/callback

with:
```
{
  "callback": "https://myprojectId.appspot.com/messages/async",
  "subscriberKey": “myFirstSubscriber",
  "topicKey": “customTopic"
}
```
Hit try it out.
This will register the subscriber for the topic = LesTopic, and call the endpoint.

4) Finally

```
GET /send/{topic}/{message}

where topic = customTopic
message = HappyBirthday
```

Hit try it out.

The callback /messages/async will receive the message “HappyBirthday” via the pubsub cloud, and you can see this in your appengine logs !

## Licensing

* See [LICENSE](LICENSE)

Java is a registered trademark of Oracle Corporation and/or its affiliates.
