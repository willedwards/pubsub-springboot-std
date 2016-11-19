# Getting started on Google Cloud Platform for Java® 

##This is a demo for STANDARD AppEngine and google pubsub

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

https://<projectId>.appspot.com/swagger-ui.html

You can create topics and subscriptions with ease, and list them.

Once a subscription is created, then register it via /register/callback on the swagger ui.


Then click the /send/{topic}/{message} GET

Enter "topic-pubsub-api-appengine-sample" for topic

Enter "test25" for message

Press Try it out.

Now, back in your terminal window type

```>gcloud app logs read```


This will show the logs from the code, and most importantly, show that the callback url was triggered.


## Licensing

* See [LICENSE](LICENSE)

Java is a registered trademark of Oracle Corporation and/or its affiliates.
