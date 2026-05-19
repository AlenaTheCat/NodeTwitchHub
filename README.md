# NodeTwitchHub
A local twitch overlay/integration system

## Installation
Grab the latest [release](https://github.com/AlenaTheCat/NodeTwitchHub/releases)

Run CatTwitchHub.exe

open [localhost:3000](http://localhost:3000) in your browser

Press "Login to Twitch", then the ? button for login instructions
<img width="877" height="390" alt="image" src="https://github.com/user-attachments/assets/c8614761-5895-4ff1-9927-09224142a6f4" />

## Customize the existing overlays
all overlay customization is in /userfiles/[Overlayname]/
### Summaries of each here
<details>
<summary>Alert Box</summary>

  ### Place video files in /userfile/AlertBox/Video/ folder
  These play when someone follows
- 1.mp4
    - About 3/7 chance
- 2.mp4
    - About 3/7 chance
- Rare.mp4
    - About 1/7 chance
- ExtremelyRare.mp4
    - About 1/100 chance

### Place audio files in Audio folder
One will be picked randomly to play during a raid with a 50/50 chance
- Raid.mp3
- Raid2.mp3 
</details>
<details>
<summary>Fling Creature</summary>

  ### Add audio files to /userfiles/FlingCreature/Audio/ folder
- fling.mp3
    - played on redeem
- splat.mp3
    - played when the creature hits the screen
- slide.mp3
    - played when the creature starts sliding down the screen
- shine.mp3
    - if "yeet" is used, shine will play when the creature disappears in the distance


 ### Add image files to /userfiles/FlingCreature/Images/ folder
- Creature.png
    - the creature that's flung
- Shine.png
    - shown when the creature disappears in the distance
</details>
<details>
<summary>Redeem Counter</summary>

  ### Add audio files to /userfiles/RedeemCounter/Audio/ folder
- CounterHit1.mp3
    - plays for the first
- CounterHit2.mp3
    - plays for the second
- CounterHit3.mp3
    - plays for the third
- CounterHit4.mp3
    - plays for all subsequent
- CounterStart.mp3
    - plays when first redeemed
- CounterEnd.mp3
    - plays when the counter is over
- CounterHighScore.mp3
    - plays when the counter is over and there's a new highscore
 
 ### Add image files to /userfiles/RedeemCounter/ folder
- Counteroverlay.png
    - 600x600px can be animated
</details>
<details>
<summary>Shoutouts</summary>
  
- ShoutoutText.txt is the message sent when shouting out 
    - @Username is replaced with their username
    - @Category is replaced with their game category
    - @Link is replaced with a link to their twitch page

- ShoutoutUsers.txt is the list of usernames to auto shoutout, 1 per line
- Manually shoutout using !so
</details>
<details>
<summary>Sound Alerts</summary>

### Place audio files in /userfile/SoundAlerts/Audio/ folder
- Add audio file names in SoundAlertsSountsList.txt, one per line, including extension
- Add associated redeem text to to the same line in SoundAlertsRedeemList

Add "Play Sound Effect" as a redeem with user input enabled

</details>
<details>
<summary>Stamp Card</summary>

### Place audio files in /userfile/StampCard/ folder
- ding.mp3
    - plays when first redeemed
- punchcard.mp3
    - plays when card is stamped
- punchcard2.mp3
    - plays when card is stamped
- party.mp3
    - plays when user has finished a card
 
### Place stamp image files in /userfile/StampCard/ folder
- stampimage.png
    - should be square, at least 75x75px
</details>
<details>
<summary>TTS</summary>

### Place image files in /userfile/TTS/ folder
- TTSSilent.png
    - shown while not talking and between sentences
- TTSTalking.gif
    - shown while talking
 
Exports folder is where TTS audio is saved,
Exports folder will get emptied on program startup
 
Add "TTS" as a redeem with user input enabled
</details>
<details>
<summary>Welcome Message</summary>

### Place audio files in /userfile/TTS/Audio/ folder

- To add a user, add their name to WelcomeMessageUsers.txt
- Add a custom message to the same line in WelcomeMessageText.txt
    - "@Username" will be replaced with their username for sake of copy/pasting for multiple users
- Do the same in WelcomeMessageSounds.txt for the audio file, including extension
    - use "None" for no audio 
</details>

## Optional x360 control
The program has the ability to allow Twitch chat to control a virtual x360 controller
To do so, install the [ViGEmBus](https://github.com/nefarius/ViGEmBus/releases/tag/v1.22.0) driver
<details>
<summary>chat message variants</summary>
  
~~~
    Buttons format: [button] [modifier]
    a, A
    b, B
    x, X
    y, Y
    right_shoulder, rightshoulder, right_bumper, rb
    left_shoulder, leftshoulder, left_bumper, lb
    right_thumb, rightthumb, r3
    left_thumb, leftthumb, l3
    back, select
    start, pause

    Dpad format: [direction] [modifier]
    left, l
    right, r
    up, u
    down, d

    Trigger format: [trigger] [strength(0 to 100)] [modifier]
    left_trigger, lefttrigger, lt
    right_trigger, righttrigger, rt

    Stick format: [stick] [x(-100 to 100)] [y(-100 to 100)] [modifier]
    left_stick, leftstick, ls
    right_stick, rightstick, rs

    Modifiers: 
    duration in ms
    'hold'
    'release' (does not require specifying x/y or strength)

Example messages:
    A
    y hold
    up 300
    lefttrigger 100
    righttrigger 50 1000
    ls 50 -50
    right_stick -25 100 hold
    rightstick release

~~~

</details>

# Adding overlays

**HTML/CSS/JS knowledge is required**

- Overlays don't neccessarily need to have visuals to them, but they do need to be loaded and active.

- You can optionally use a standalone javascript application for that purpose, which is likely faster/more optimized, but not required. HTMLs should be fine, as having even a couple dozen "empty" html pages loaded in OBS won't really affect performance in any meaningful way.

### Option 1 - From Template HTML

Create a copy of the OverlayTemplate.html in /overlays/

The html is already setup to connect with the program

An example for a redeem event is already in place

<img width="604" height="86" alt="image" src="https://github.com/user-attachments/assets/6c4902dc-ae8b-4960-9179-831f066d6d20" />

modify or add as needed.

### Option 2 - From Scratch/Modifying Existing HTML

Create a new HTML file or move existing HTML file into the /overlays/ folder

Add `<script src="https://cdn.socket.io/4.8.1/socket.io.min.js"></script>` to your HTML

Add `const socket = io();` to an existing or new script area

<img width="850" height="93" alt="image" src="https://github.com/user-attachments/assets/5e744140-c9e9-480b-a7a1-8628e8c12dce" />

Add desired events to capture twitch events, modify or add as needed.

## List of socket events
<details>
<summary></summary>

~~~
Events:
socket.on("command", (user, command, flags, message) => {DO STUFF HERE}); sent when an !command is used
socket.on("message", (user, message, flags, self) => {DO STUFF HERE}); sent when a message is sent in chat
socket.on("redeem", (user, reward, message) => {DO STUFF HERE}); sent when a point redeem is used
socket.on("follow", (user, extra) => {DO STUFF HERE}); sent when a user follows
socket.on("raid", (user, viewers) => {DO STUFF HERE});sent when a user raids
socket.on("bits", (user, bits, message) => {DO STUFF HERE}); sent when a user gives bits (may not work if bits are used for external apps like soundalerts)
socket.on("sub", (user, subTierInfo, message) => {DO STUFF HERE}); sent when a user subscribes
socket.on("resub", (user, streamMonths, cumulativeMonths, subTierInfo, message) => {DO STUFF HERE}); sent when a user resubscribes
socket.on("giftsub", (gifterUser, streakMonths, recipientUser, senderCount, subTierInfo) => {DO STUFF HERE}); sent when a user gifts a sub to a specific user
socket.on("mysterysub", (gifterUser, numbOfSubs, senderCount, subTierInfo) => {DO STUFF HERE}); sent when a user gifts a sub or subs randomly to the community
socket.on("subcontinue", (user, sender) => {DO STUFF HERE}); sent when a user continues their giftsub
socket.on("HypeTrain", (status, level, progressToNextLevel, goalToNextLevel, totalHype, timeRemainingInMS) => {DO STUFF HERE}); sent during a hype train with various statuses (start, end, progress)
socket.on("Poll", (status, title, choices, votes, timeRemainingInMS, extra) => {DO STUFF HERE}); sent during a poll with various statuses (begin, progress, end, archive, close, delete)
socket.on("UserJoin", (user) => {DO STUFF HERE}); sent when a user enters your chat
socket.on("UserLeave", (user) => {DO STUFF HERE}); sent when a user leaves your chat
socket.on("Prediction", (status, title, outcomes, topPredictors, timeRemainingInMS) => {DO STUFF HERE}); sent during a prediction with various statuses (begin, progress, lock, end, cancel)
socket.on("TTSSpeak", () => {DO STUFF HERE});   Sent when tts starts speaking
socket.on("TTSSpeakEnd", () => {DO STUFF HERE});    Sent when tts stops speaking
socket.on("TTSStop", () => {DO STUFF HERE});    Sent when tts is force stopped

Emitters:
socket.emit("TTSMessage", message, voice, speed); Sends a message to the main program to generate a tts message file (only used for TTS overlay) 
socket.emit("WriteToFile", "FileName", JSONdata, append?[True/False], exitaftersave?[True/False]); writes data to a specified file
socket.emit("ChatMessage", message); Sends a message in your twitch chat as you
socket.emit("Log", data, color); sends custom log info to be displayed in the main program
    available colors: Red, Yellow, Green, Cyan, Blue, Purple

Relays info from one overlay to another, key is arbitrary, but is primarily intended as an easy way to mark and filter the relay
socket.emit('SendRelay', key, data);
socket.on('RecieveRelay', (key, data) => {DO STUFF HERE});



ViGEm xbox controller emulator events:
    socket.emit("pressButton", button, duration);
    socket.emit("holdButton", button);
    socket.emit("releaseButton", button);
    socket.emit("directionalPress", x, y, stick, duration); x and y are floats from -1 to 1
    socket.emit("directionalHold", x, y, stick); x and y are floats from -1 to 1
    socket.emit("directionalRelease",stick);
    socket.emit("triggerPress", value, trigger, duration); value is a float from -1 to 1
    socket.emit("triggerHold", value, trigger); value is a float from -1 to 1
    socket.emit("triggerRelease", trigger);

ViGEm valid buttons and sticks:
    LeftStick
    RightStick
    LeftTrigger
    RightTrigger
    DpadX
    DpadY

    START
    BACK
    LEFT_THUMB (L3)
    RIGHT_THUMB (R3)
    LEFT_SHOULDER
    RIGHT_SHOULDER
    A
    B
    X
    Y  
~~~
  
</details>

# Connecting to other apps or modding games

The game or app does not need to be built in Node or JavaScript, it just needs a compatible socket.io library.

Add applicable socket.io library to your mod/app, then adapt existing events to your chosen library's syntax. 

# Build from source
Created in Visual Studio 2026 using NodeJS v24.14.0
## Setup

Install Visual Studio and NodeJS

Open NodeTwitchHub.slnx

Install node packages
<details>
<summary>Package List</summary>

- @angablue/exe@3.2.5 `needed for build.bat to function`
- comfy.js@1.1.29
- dotenv@16.4.1
- express@4.21.2
- global-shortcuts@1.1.0
- node-fetch@3.3.2
- obs-websocket-js@5.0.8
- openurl@1.1.1
- sanitize-html@2.17.2
- say@0.16.0
- socket.io@4.8.3
- twitch-auth@4.6.7
- twitch-eventsub@4.6.7
- twitch-pubsub-client@4.6.7
- twitch@4.6.7
- vigemclient@1.5.3
- winston@3.19.0
- ws@8.19.0
  
</details>

## Build

Run /NodeTwitchHub/Build.bat
Place generated exe in folder with copies of /overlays/ and /userfiles/
### File Structure Example
- /Cat Twitch Hub/
    - /overlays/
        - overlay1.html
    - /userfiles/
        - /Overlay1Files/
        - config.json
        - secret.json
    - CatTwitchHub.exe
