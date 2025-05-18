# Morse Trainer Playground

## Overview
NOTE: This description is BETA and may not be accurate with SwiftPlaygrounds 4
Morse Trainer Playground is an **interactive Swift Playground** designed for iPad, enabling users to **play and adjust Morse code playback** in real time. This project showcases SwiftUI, AVFoundation, and structured concurrency techniques to ensure smooth audio processing and user interaction.
Swift Playgrounds is a free app from the iPad app store
## Features
- **Morse Code Playback**: Converts and plays a given text file (`story.txt`) as Morse code.
- **Real-Time Speed Adjustment**: Users can dynamically change the playback speed in **Words Per Minute (WPM)**.
- **Immediate Start/Stop Functionality**: Playback can be toggled using a button with instant stopping capability.
- **Live Text Display**: Users can view the full story text for reference.
- **Task Cancellation & Concurrency Optimization**: Ensures seamless playback handling without lingering tones.

## How to Load the Playground on iPad
### **Prerequisites**
### **Steps to download MorseTrainer app from github to iPad
- in a Browser go to https://github.com/bobh/SwiftPlaygrounds
- Go to the Green Code Button (don't select the file)
- select Download zip
- On the iPad go to the "Files" app--search for it if you have never used it
- In the Files app, you should see "SwiftPlaygrounds-main.zip" long press and "Uncompress"
- That will take you to the Browse Tab and you should see a folder "SwiftPlaygrounds-main"
- In that folder, are three files. Press MorseTrainer.swiftpm.zip
- Now you should see the MorseTrainer Swift Playgrounds app MorseTrainer
- Press it, and swift Playgrounds will open. Press the "Play" triangle button at the top.  

-
### **Steps to Set Up**
1. **Download the Playground**  
   - Clone the repository or download the `.swiftpm` file.
   - Open **Swift Playgrounds** on your iPad.

2. **Import the Playground**
   - Tap **"Open Playground"** and select the `.swiftpm` file.
   - Move the file into Swift Playgrounds.

3. **Add `story.txt` to Resources**
   - Open the sidebar and locate the `Resources` folder.
   - Add `story.txt` manually (it must be in plain text format).

4. **Run the Playground**
   - Tap **Run** to start the app.
   - Use the **Play/Stop** button to toggle Morse code playback.
   - Adjust **WPM slider** to modify playback speed dynamically.

## NOTE 1: 
When you select the MorsePlayer app and it loads at start up, wait for a while
 before pressing the “triangle” play button.
 I think it compiles the entire code when starting up.
 The AI has some thoughts!
 When you launch your MorsePlayer app in Swift Playgrounds 4+, especially for the first time or after edits:
 •    The entire SwiftUI codebase is compiled and type-checked.
 •    The runtime environment is initialized.
 •    Your .task {} modifier is queued to run after the UI is ready — but this may be slightly delayed.
 •    AVFoundation (engine, player, buffers) also takes a moment to set up under the hood.
 
 So pressing the play button too soon can race ahead of:
 •    initializeAudio()
 •    loadRandomStory()
 •    even AVAudioEngine’s full startup
 
##  NOTE 2:
The app will randomly pick one of the three text files to play at startup
 
## Adding Original Stories with AI (ChatGPT, Copilot, etc.)
You can create your own custom story for Morse code playback using agentic AI tools like ChatGPT. Here's how:

### **Generating a New Story**
Use an AI assistant like ChatGPT or Copilot to generate a text-based story with the following prompt:
"Compose an original 200 to 300-word story in UTF-8 ASCII text format on the topic of Morse Code or Amateur Radio.
The story should be a **plain text file** without special characters or formatting".

### **Adding the Story to `story.txt`**
1. **Copy the AI-generated story** into a new text file.
2. **Save the file as `story.txt`** in **UTF-8 ASCII format**.
3. **Move it to the `Resources` folder** inside the Swift Playground.
4. **Run the app**, and your new story will be played as Morse code.

## Sample Story: *Echoes Through the Ether*
Here’s an example of a custom story that can be added to `story.txt`:

---
### **Echoes Through the Ether**

Mark sat in his dimly lit ham shack, surrounded by old transceivers and blinking LEDs. His fingers hovered over the Morse key, ready to transmit a signal into the vast, unseen ether. Outside, the storm raged, sending occasional bursts of static across the airwaves.

It was on nights like these that Mark remembered his grandfather—an old radio enthusiast who taught him the rhythms of Morse code. "Every dot and dash tells a story," his grandfather had said, tapping out a message on the brass key.

Tonight, Mark wasn’t just listening for signals—he was searching. Earlier in the evening, he’d picked up faint transmissions, erratic yet deliberate. "CQ CQ," the sender had signaled. A call for anyone listening.

Adjusting the frequency, Mark responded.  
**"...CQ CQ DE K4MHZ, WHO CALLS?"**  

Silence. Then, a reply—weak but clear:  
**"...LOST IN STORM… NEED HELP..."**  

Mark’s pulse quickened. The message wasn’t automated; it was real. Someone was reaching out through the static, seeking help.

With precision, he transmitted back:  
**"...HOLD TIGHT. WHAT IS YOUR LOCATION?..."**  

The signal faded, then crackled back:  
**"...NO POWER… NEED RESCUE… GRID FN31..."**  

Mark pulled up a map. FN31—somewhere near the mountains. He relayed the information to emergency responders, transmitting updates with steady, practiced keystrokes.

An hour passed before a new signal arrived:  
**"...FOUND… THANK YOU..."**  

Mark exhaled, staring at the Morse key, now silent beneath his fingertips. His grandfather was right—Morse code was more than signals; it was **lifelines** in times of need.  

---

### **How to Use This Story**
1. Copy the text above into a **plain text file**.
2. Save the file as **`story.txt`** in **UTF-8 ASCII format**.
3. Move it to the **Resources folder** inside the Swift Playground.
4. Run the app—this story will now play as Morse code.


Future Improvements

🔊 1. Adjustable Tone Frequency

Let the user select the tone frequency (e.g. 400 Hz to 1200 Hz) to match their hearing comfort or training goals.
	•	UI: Add a Slider or a Stepper in the settings section.
	•	Effect: Update the freq dynamically.
	•	Challenge: You’ll need to rebuild the tone buffer with the new frequency each time.

⸻

✍️ 2. Copy Practice Mode (Interactive Typing Test)

Add a “Copy Mode” where users type what they hear in real time and get scored.
	•	UI: TextField for input, score shown below.
	•	Logic:
	•	Compare typed input to storyText.
	•	Highlight correct/incorrect characters.
	•	Track WPM and accuracy.
	•	Challenge: Syncing user typing with playback timing.

⸻

🎯 3. Segment Playback

Allow playback of only selected sentences or characters.
	•	UI: Add a list or buttons for sentence/paragraph navigation.
	•	Use Case: Users can focus on one section of a long story.

⸻

📊 4. Statistics Dashboard

Display:
	•	Time spent practicing.
	•	Characters played.
	•	Accuracy (if in copy mode).
	•	Average WPM speed used.
	•	Storage: Use UserDefaults for lightweight data storage.

⸻

🎧 5. Headphone Mode with Stereo Panning

Add a feature to pan Morse tones left/right gradually for concentration training.
	•	API: AVAudioEnvironmentNode or pan on AVAudioMixerNode.

⸻

🌙 6. Dark Mode Enhancements
	•	Adjust background/highlight colors to improve readability in dark environments.
	•	Optional sepia or amber-on-black “night” mode for eye comfort.

⸻

🕹️ 7. Game Mode / Contest Simulation

Simulate contests like ARRL Sweepstakes:
	•	Random call signs, serial numbers.
	•	Timer-based scoring.
	•	Fast-paced short messages.

⸻

📂 8. User-Added Stories

Let users drop custom .txt files into the Resources folder (or import via Share Sheet on iPadOS).
	•	Bonus: Save favorite stories or tag them for difficulty.

⸻

🧪 9. Real-Time Oscilloscope (Debug Panel)

Show waveform of current tone for educational/demo purposes.
	•	View: Use SwiftUI Canvas or MetalKit for visualization.
	•	Data Source: Stream from AVAudioEngine’s tap.

⸻

🌐 10. Online Story Fetching (Offline-safe)

Fetch new stories from a server or API, cache locally for offline use.

## Future Improvements
- **Character-by-character highlighting** during playback.
- **Waveform visualization** for better Morse code representation.
- **Expanded customization** for playback and tone generation.

##