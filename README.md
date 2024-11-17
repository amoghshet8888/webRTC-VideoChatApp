# webRTC-VideoChatApp
A vide chat application using webRTC
Workflow of the Real-Time Video Chat Application
User Enters Lobby:

The user opens the application and lands on the Lobby screen.
They enter their email and a room number to join a specific chat room.
Join Room:

Upon submitting the form, a "room
" event is emitted to the backend with the user's email and room number.
The backend handles the "room
" event by mapping the user's email to their socket ID and notifying other users in the room about the new participant.
The user is then navigated to the Room page.
Room Page Initialization:

On the Room page, the application listens for several events: "user
", "incomming
", "call
", "peer:nego
", and "peer:nego
".
When another user joins the room, the application updates the state with the new participant's socket ID.
Initiating a Call:

The user clicks the "CALL" button to start a video call.
The application captures the user's media stream (audio and video) using navigator.mediaDevices.getUserMedia.
An offer is created via WebRTC's RTCPeerConnection and sent to the backend using the "user
" event.
The backend forwards the offer to the targeted user.
Receiving a Call:

The targeted user receives the "incomming
" event with the offer.
The application captures the targeted user's media stream and creates an answer to the offer.
The answer is sent back to the caller through the backend using the "call
" event.
Stream Negotiation:

If further negotiation is needed, the application handles "peer:nego
" and "peer:nego
" events to exchange offers and answers, ensuring both peers are properly connected.
Streaming Media:

Once the call is accepted and streams are negotiated, media tracks are exchanged between users.
The application listens for the "track" event on the RTCPeerConnection to handle incoming media streams and updates the remote stream state.
Displaying Streams:

The application uses ReactPlayer to display the local and remote media streams on the Room page.
By following these steps, the application enables users to have real-time video and audio communication with efficient stream management.
