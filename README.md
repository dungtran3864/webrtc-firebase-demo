# Video Chat with WebRTC and Firebase

Build a 1-to-1 video chat feature with WebRTC, Firestore, and JavaScript. 

# How it works?
1. Request access to video and audio permissions from the browser
2. Create a new global WebRTC connection in the application
3. Push local stream to WebRTC connection so that any other receivers can access your video stream.
4. Pull remote stream 
so that you can access to any video streams from other people.
5. As a caller 
   1. Click on call offer to generate a unique room ID. 
   2. Create a new call offer in WebRTC connection and set local description of WebRTC connection of the caller with that new call offer. 
As soon as that that's set, a list of ICE offer candidates are generated. Save them in offerCandidates of the current call in DB.
   3. Save the call offer in DB
6. As a receiver
   1. Paste the given room ID and click answer
   2. Retrieve the call offer saved in DB and set remote description of WebRTC connection of the receiver with that call offer.
   3. Create a new call answer in WebRTC connection and set local description of WebRTC connection of the receiver with that new call answer.
As soon as that that's set, a list of ICE answer candidates are generated. Save them in answerCandidates of the current call in DB.
   4. Save the call answer in DB
7. Receiver receives an updated list of ICE offer candidates and add all of those in the WebRTC connection.
8. Caller receives the call answer in DB and set remote description of WebRTC connection of the caller with that call answer.
9. Caller receives an updated list of ICE answer candidates from answerCandidates collection and adds all of those in the WebRTC connection.
10. WebRTC connection algorithm automatically determines the best connection between ICE offer and answer candidates and establish the call.


```
git clone <this-repo>
npm install

npm run dev
```
