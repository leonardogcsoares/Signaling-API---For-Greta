# Signaling-API-for-Greta

This is a very simple Signaling API I created, inspired by the one found on [Greta](https://greta.io/documentation/signaling).
For the browser, the unique Greta script should be placed in the `</head>` tag. For Android, for now as well, the function:
```java
Greta.initializeGretaConnection("someRandomToken");
```
should be called to initialize the signaling API inside the activity.

####Connecting
-You need to call `Greta.Signaling.connected` with a callback for when the signaling system is connected.
```java
Greta.Signaling.connected(new Connected() {
       @Override
       public void onConnection() {
          Log.d(TAG, "Greta Signaling finished connecting");
       }
});
```
####Subscribe
-You can subscribe to a given channel and need to provide a callback for when a message arrives on the channel using 
`Greta.Signaling.subscribe`.
```java
Greta.Signaling.subscribe("channel", new Subscriber() {
       @Override
       public void messageReceived(String message) {
          Log.d(TAG, "Subscribe message received: " + message);
       }
});
```
####Publish
-To publish a message to a channel you call `Greta.Signaling.publish` with the channel name and String message.
```java
Greta.Signaling.publish("channel", "This is a new publish message");
```

#To-Do
- [ ] Instead of using `Greta.initializeGretaConnection` place the token inside the `AndroidManifest.xml` (Android representation of `</head>`)




