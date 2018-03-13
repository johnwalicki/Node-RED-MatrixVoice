# MAtrix Voice, Node-RED and Watson Cognitive APIs

## Introduction
This repository contains examples of how I set up my Matrix Voice to record
speech via Node-RED running on the Raspberry Pi. There are a few Node-RED flows
which demonstrate the evolution of my experiments.

Before you can use these examples, upgrade [Node-RED](http://nodered.org) on
your Raspberry Pi. Older versions of Node.js and Node-RED are pre-installed
on the default Raspbian image.  I started with [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/),
applied distro updates, then installed [Matrix Core](https://matrix-io.github.io/matrix-documentation/matrix-core/getting-started/installation/) only. I also used npm to install node-red-dashboard, node-red-contrib-microPi, node-red-contrib-snowboy, node-red-noe-weather-underground and node-red-node-watson

I started at the command line and made certain that I could record audio.
> /usr/bin/arecord -d 5 --device=mic_channel0 -r 16000 -c 1  -f S16_LE /home/pi/test.wav

The Node-RED flows and screenshots include:
* **arecord with Matrix Voice** - Simple flow which records a .wav file via the Matrix Voice 8 MEMs microphones and sends it to Watson Speech to Text for transcription.
* **arecord with Matrix Voice controlled by a Node-RED Dashboard** - Same flow but controlled by a Node-RED dashboard.
* **MicroPi with Watson Speech to Text** - Replace the arecord exec node with a hacked MicroPi node.
* **Snowboy wake word example** - Use the Matrix Voice speaker to listen for a wake word "Hey Watson" using [Snowboy](https://flows.nodered.org/node/node-red-contrib-snowboy)
* **Full example of Matrix Voice with a wake word and Watson Cognitive API to implement a ChatBot** - A bit more sophisticated example that lets you talk with your Raspberry Pi . I pass the streaming speech to node-red-contrib-snowboy to listen for a wake word. In my case “Hey Watson”. That wakes up a Node-RED flow that uses Watson Speech to Text, Watson Conversation (in another version) and Watson Text to Speech to interact with the user.

### Import a prebuilt flow from GitHub
Since configuring Node-RED nodes and wiring them together requires many steps to document in screenshots, there is an easier way to build a flow by importing a prebuilt flow into your Node-RED editor.

* Some of the sections below will have a **Get the Code** link.

* When instructed, open the **Get the Code** github URL, mark or Ctrl-A to select all of the text, and copy the text for the flow to your Clipboard.
* Click on the Node-RED Menu **(6)**, then Import **(7)**, then Clipboard **(8)**.
![Node-RED import screenshot](https://github.com/johnwalicki/IoT-AssetTracking-Perishable-Network-Blockchain/blob/master/Node-RED/screenshots/IBMCloud-NodeRED-import.png?raw=true)
* Paste the text of the flow into the **Import nodes** dialog and press the red **Import** button.
![Node-RED import from clipboard screenshot](https://github.com/johnwalicki/IoT-AssetTracking-Perishable-Network-Blockchain/blob/master/Node-RED/screenshots/IBMCloud-NodeRED-pastefromclipboard.png)
* The new flow will be imported into **new tabs** in the Node-RED Editor.

## Get the flow
As a first step, copy the code from GitHub to your Clipboard and import it into your Node-RED editor.

Get the Code - [Node-RED Matrix Voice flows](flows/MatrixNodeREDSnowboy.json)

## Screenshots
**arecord with Matrix Voice** - Simple flow which records a .wav file via the Matrix Voice 8 MEMs microphones and sends it to Watson Speech to Text for transcription.
![arecord with Matrix Voice](screenshots/NodeRED-arecord-STT-flow.png?raw=true)

**arecord with Matrix Voice controlled by a Node-RED Dashboard** - Same flow but controlled by a Node-RED dashboard.
![arecord with Matrix Voice controlled by a NR Dashboad](screenshots/NodeRED-arecord-STT-dashboard-flow.png?raw=true)
![Matrix Voice controlled by a NR Dashboad](screenshots/NodeRED-arecord-STT-dashboard.png?raw=true)

**MicroPi with Watson Speech to Text** - Replace the arecord exec node with a hacked MicroPi node.
![MicroPi with Watson Speech to Text](screenshots/NodeRED-micropi-STT-flow.png?raw=true)

**Snowboy wake word example** - Use the Matrix Voice speaker to listen for a wake word "Hey Watson" using [Snowboy](https://flows.nodered.org/node/node-red-contrib-snowboy)
![Snowboy wake word example](screenshots/NodeRED-micropi-HeyWatson-flow.png?raw=true)

**Full example of Matrix Voice with a wake word and Watson Cognitive API to implement a ChatBot**
![Watson Chatbot with Matrix Voice](screenshots/NodeRED-micropi-HeyWatson-STT-flow.png?raw=true)
