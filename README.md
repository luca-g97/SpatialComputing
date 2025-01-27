![requiredItems](https://github.com/luca-g97/SpatialComputing/blob/main/Assets/teaser_image.jpg)

In this project, we will explore one of the best digital twin creation tools available today: Metahumans. You can follow a detailed guide to create your own Metahuman, which can be seamlessly imported into any project. Using the Optitrack system for motion tracking, the Metahuman can be brought to life in any virtual scenario - in real-time with little to no latency.

# Recommended Requirements:
1. Hardware:
* LAN network connection
* Optitrack motion capture system
* Optitrack motion tracking suits
* (Additionally: passive markers)
* Laptop/PC suited for real-time rendering (incl. LAN port)
* LAN cable
2. Software:
* Unreal Engine (we used Engine Version 5.4 but a different one should also work)
* Motive application

# Setup:

## 1. Install the Epic Games Launcher
Download and install the [Epic Games Launcher](https://store.epicgames.com/en-US/download) from the website. Open it and create your Epic Games Account or log in directly if you already have one.

## 2. Install Unreal Engine
After opening the laucher choose the "Unreal Engine" tab on the left. Navigate to "Library" at the top. Add your desired "Engine-Version" with the yellow "Plus-Button". Click it and select your Unreal Engine version from the dropdown in the top right from the now appearing container. Afterwards hit install and select install in the now appearing window. Unreal Engine is now getting downloaded which can take a while depending on your network. You can see the progress or pause the download in the bottom left of the launcher if necessary.

## 3. Install and activate the Live-Link plugin
Open Unreal Engine using the Launch button in the top right once the Engine is downloaded. Pick one of the standard projects and wait until it is opened. Once the project has been created select "Edit" from the top left menu and pick "Plugins". Search for "Live Link", tick the first option available and restart Unreal Engine to activate it. You can now customize the scene if you want to make the interaction with the MetaHumans more interesting later on.

## 4. Download and install Optitrack Plugin & ensure Motive Installation
Download the [Optitrack Plugin](https://www.optitrack.com/support/downloads/plugins.html) from the official website and put the plugin contents into the following folder:
* C:\Program Files\Epic Games\UE_5.4\Engine\Plugins\Marketplace\OptitrackLiveLink

Make sure that the optitrack system has a licensed version of [Motive](https://www.optitrack.com/support/downloads/) installed as well.

# Digital-Twin Creation

## 5. Metahuman-Creation
Open the following Website in your Browser: https://metahuman.unrealengine.com/, log into your Epic Games account and pick your preferred Unreal Engine Version (in our case 5.4, but it should work with every version) from the dropdown menu. Open the MetaHuman Creator by clicking onto "Launch MetaHuman Creator" (this might take a while)
Customize the Metahuman to your needs and export it as a ? file to later import in Unreal Engine.

# Final Steps 

## 6. Edit Motive Live Settings
#### a) Since you will need a license for Motion and the Optitrack system anyway as well as the suits, you need a PC with Motive installed. Make also sure there is one LAN port available which you can connect your PC to later on. Open the Motion application.
#### b) Place some markers in sight of the cameras and return to the PC. Click onto "eSync 2" on in the rider "Devices" on the top right. Select "Internal Free Run" from the "Source" options in the "Sync Input Settings" section. Check if the markers are shown in the camera view in the bottom mid of the screen.
#### c) Remove all markers from the cameras sight and mask any other visible detected objects to not interfere with the "Wanding". Calibrate the system now using the "Wand" and ensure that you cover as much as possible on each camera. Put the "Calibration-Square" in the middle of the room and select it to set the ground plane correctly.
#### d) Open the "Settings" menu and switch to the rider "Streaming". Make sure that the following settings are met to correctly stream the data in Unreal Engine later:
* Local Interface: 10.21.3.162
* Transmission Type: Unicast
* Skeleton Coordinates: Local
* Bone Naming Convention: UnrealEngine
* Up-Axis: Y-Axis

![requiredItems](https://github.com/luca-g97/SpatialComputing/blob/main/Assets/Setup.jpg)

#### IMPORTANT: Remember or write down the internal IP-Adress (10.21.3.162). You will need it to add the correct Live Link Source in Unreal Engine.

## 7. Add Live Link Source:
#### a) Open the Live Link Window by going to Window-->LiveLink
#### b) Add a new source and uncheck "automatic"
#### c) Open a command prompt and enter "ipconfig" to check your local IP-Address (begins with 10...) and enter it as the local address.
#### d) Enter the IP-Address (10.21.3.162) from Motive as the Source Address.
#### e) Finally Create the "Live Link Source", select it and deactivate "Animate Y forward" in the details section.

## 8. Retarget Skeleton:
#### a) Now import the created MetaHuman via Drag and Drop into your Unreal Engine project. 
#### b) AnimationBP: Create a new AnimBP using the skeleton of your MetaHuman. Pick "Live Link Pose" for the input pose and retarget the asset in Optitrack. (Use the correct Live Link name (the name of your object in Motion if you already have one) to synchronize the animation correctly)
#### c) Settings in the MetaHumanBP: Ensure that "LODSync" is set to >= 1 and select the created Anim BP for the skeletal mesh. Also ensure to live link the skeletal animation component.

![requiredItems](https://github.com/luca-g97/SpatialComputing/blob/main/Assets/live_link_pose.png)

## 9. Synchronize Metahuman with Yourself:
Hop into the Motion-Tracking suit and open the Builder in the Motive application. Pick one of the skeletons (we picked Baseline (41), since we wanted both to be tracked) and place the markers as shown. Create a new object and name it as you like. Ensure to set the correct Live Link name in the AnimationBP of your MetaHuman.

## Now everything is set up properly and only your own imagination is the limit of what your digital twin can do now!

## Some impressions of our session:
Ever wanted to recreate the scene from the Matrix movie? Here you go:
![requiredItems](https://github.com/luca-g97/SpatialComputing/blob/main/Assets/Matrix.gif)

Imagined to be a digital super hero saving everyone from a grenade? No problem anymore:
![requiredItems](https://github.com/luca-g97/SpatialComputing/blob/main/Assets/Grenade.gif)

Or just wanted to mess around to create funny clips? We got you covered:
![requiredItems](https://github.com/luca-g97/SpatialComputing/blob/main/Assets/DriveBy.gif)


## Recommended sources:
* [Live-Link Plugin](https://docs.optitrack.com/plugins/optitrack-unreal-engine-plugin/unreal-engine-optitrack-live-link-plugin/quick-start-guide-real-time-retargeting-in-unreal-engine-with-live-link-content) - detailed explanation of how the plugin works
* [Unreal Live Link Setup Tutorial](https://www.youtube.com/watch?v=rpd9KxQyeek&t=358s&ab_channel=TrashPraxis)
* [Motive Calibration](https://docs.optitrack.com/motive/calibration)


## ... FAQ:

### What is Unreal Engine? 
Unreal Engine is a powerful, real-time 3D creation tool developed by Epic Games. It is widely used for game development, filmmaking, architecture, simulation, and other industries that require high-quality visual content. Unreal Engine is known for its cutting-edge graphics, robust physics engine, and user-friendly interface, making it a popular choice for both indie developers and large studios.

### What is a MetaHuman?
MetaHuman is a framework developed by Epic Games for creating highly realistic digital humans in Unreal Engine. It is part of the MetaHuman Creator, a cloud-based tool that allows users to design and customize photorealistic human characters quickly and easily.

### What is a Digital Twin?
A digital twin is a virtual representation of a physical object, system, or person that mirrors its real-world counterpart in real-time. In this project, the digital twin is a MetaHuman character that replicates your movements using motion capture technology, allowing you to interact with virtual environments as if you were physically present.

### What is OptiTrack?
OptiTrack is a motion capture system that uses cameras and markers to track the movement of objects or people in real-time. It is widely used in animation, virtual reality, and robotics to capture precise movements and translate them into digital data. In this project, OptiTrack is used to track your movements and synchronize them with your MetaHuman digital twin.

### What is Live Link?
Live Link is a feature in Unreal Engine that enables real-time data streaming from external sources, such as motion capture systems, into the engine. It allows for seamless integration of live data, such as animations or positional tracking, into your Unreal Engine projects. In this project, Live Link is used to stream motion data from the OptiTrack system to animate your MetaHuman.

### Can I use a different motion capture system instead of OptiTrack?
Yes, Unreal Engine supports various motion capture systems through Live Link. While this guide focuses on OptiTrack, you can use other systems like Rokoko, Xsens, or Perception Neuron, provided they are compatible with Live Link and have the necessary plugins or integrations.

### Do I need programming skills to use Unreal Engine and MetaHuman?
No, Unreal Engine is designed to be accessible to users with varying levels of expertise. The Blueprint visual scripting system allows you to create complex logic without writing code. Additionally, tools like MetaHuman Creator and Live Link are designed to be user-friendly, making it easy to create and animate digital humans without extensive technical knowledge.

### What are the limitations of MetaHuman?
While MetaHuman offers highly realistic characters, there are some limitations:
*Performance: High-fidelity MetaHumans can be resource-intensive, requiring powerful hardware for real-time rendering.
* Customization: While MetaHuman Creator offers extensive customization options, there are limits to how much you can deviate from the provided templates.
* Animation: While MetaHumans are animation-ready, creating complex animations may require additional tools or expertise.

### Can I use MetaHumans for commercial projects?
Yes, MetaHumans created using MetaHuman Creator can be used in commercial projects without additional licensing fees. However, ensure you comply with Epic Games' licensing terms, especially if your project generates significant revenue.

### What are the benefits of using Unreal Engine for digital twin creation?
Unreal Engine offers several advantages for digital twin creation:
* Real-Time Rendering: Instantly visualize changes and interactions.
* High-Quality Graphics: Achieve photorealistic visuals with features like Nanite and Lumen.
* Cross-Platform Support: Deploy your digital twin across various platforms, including VR/AR, mobile, and desktop.
* Extensive Toolset: Access a wide range of tools and plugins, such as Live Link and MetaHuman Creator, to streamline development.

### How can I optimize performance when using MetaHumans?
To optimize performance:
* Use Level of Detail (LOD) settings to reduce the complexity of the MetaHuman model at a distance.
* Limit the number of active MetaHumans in a scene.
* Use efficient lighting and post-processing settings.
(Ensure your hardware meets the recommended requirements for real-time rendering)

