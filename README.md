# NodeTwitchHub
A local twitch overlay/integration system

## Installation
Grab the latest [release](https://github.com/AlenaTheCat/NodeTwitchHub/releases)

> In /userfiles/ rename configtemplate.json to config.json
> 
> In /userfiles/ rename secrettemplate.json to secret.json
> 
> In /userfiles/StampCard/ rename viewerstreakstemplate.json to viewerstreaks.json
> 
> (fix pending)


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

### Place audio files in /userfile/AlertBox/Audio/ folder
One will be picked randomly to play during a raid with a 50/50 chance
- Raid.mp3
- Raid2.mp3 
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

### Place audio files in /userfile/AlertBox/Audio/ folder
One will be picked randomly to play during a raid with a 50/50 chance
- Raid.mp3
- Raid2.mp3 
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
To do so, install the [ViGEmBus](https://github.com/nefarius/ViGEmBus/releases/tag/v1.22.0) driver (also located in the /Optional Drivers/ folder)
