In this project, we will explore one of the best digital twin creation tools available today: Metahumans. You can follow a detailed guide to create your own Metahuman, which can be seamlessly imported into any project. Using the Optitrack system for motion tracking, the Metahuman can be brought to life in any virtual scenario - in real-time with no latency.


# Requirements:
1. OPTITRACK:
* Optitrack system
* Motive application
* Motion tracking suits
* (Passive markers)
2. LAPTOP/PC:
* Laptop/PC with a LAN port
* LAN cable connection to Optitrack system

Beispiel:
![requiredItems](https://github.com/Digital-Media/sco_2023/assets/116873186/cf3e1e2e-9148-4f68-8b70-d307e0204fa1)

# Setup:
## 1. Motive Settings
### a) Since you will need a license for Motion and the Optitrack system anyway as well as the suits, you need a PC with Motive installed. Make also sure there is one LAN port available which you can connect your PC to later on. Open the Motion application.
### b) Place the "Calibration-Triangle" on the ground in sight of the cameras and return to the PC. Click onto "eSync 2" on in the rider "Devices" on the top right. Select "Internal Free Run" from the "Source" options in the "Sync Input Settings" section. Check if the markers are shown in the camera view in the bottom mid of the screen.
### c) Remove the "Calibration-Triangle" from the cameras sight to not interfere with the "Wanding". Calibrate the system now using the "Wand" and ensure that you cover as much as possible on each camera. Put the "Calibration-Triangle" in the middle of the room and select it to set the ground plane correctly.
### d) Open the "Settings" menu and switch to the rider "Streaming". Make sure that the following settings are met to correctly stream the data in Unreal Engine later:
* Transmission Type: Unicast
* Skeleton Coordinates: Local
* Bone Naming Convention: UnrealEngine
* Up-Axis: Y-Axis   

## 1. Install the Epic Games Launcher
Download and install the Epic Games Launcher from the website (https://store.epicgames.com/en-US/download). Open it and create your Epic Games Account or log in directly if you already have one.

## 2. Install Unreal Engine
Once the login has worked, the launcher opens. Click on "Unreal Engine" on the left side and pick "Library" from the riders above. Behind the "Engine-Version" a yellow "Plus-Button" is visible. Click it and select your Unreal Engine version from the dropdown in the top right from the now appearing container. Afterwards hit install and select install in the now appearing window. Unreal Engine is now getting downloaded which can take a while depending on your network. You can see the progress or pause the download in the bottom left of the launcher if necessary.

## 3. Install and activate the Live-Link plugin
Open Unreal Engine using the Launch button in the top right once the Engine is downloaded. Pick one of the standard projects and wait until it is opened. Once the project has been created select "Edit" from the top left menu and pick "Plugins". Search for "Live Link", tick the first option available and restart Unreal Engine to activate it. You can now customize the scene if you want to make the interaction with the MetaHumans more interesting later on.

## ... FAQ:

### What is Unreal Engine? ...

## Recommended sources:
[Live-Link Plugin](https://docs.optitrack.com/plugins/optitrack-unreal-engine-plugin/unreal-engine-optitrack-live-link-plugin/quick-start-guide-real-time-retargeting-in-unreal-engine-with-live-link-content) - detailed explanation of how the plugin works

# Digital-Twin Creation:
## 1. Metahuman-Creation:
Open the following Website in your Browser: https://metahuman.unrealengine.com/, log into your Epic Games account and pick your preferred Unreal Engine Version (in our case 5.4, but it should work with every version) from the dropdown menu. Open the MetaHuman Creator by clicking onto "Launch MetaHuman Creator" (this might take a while)
Customize the Metahuman to your needs and export it as a ? file to later import in Unreal Engine.

## 2. Retarget Skeleton:
### a) Now import the created MetaHuman via Drag and Drop into your Unreal Engine project. Add a "Live Link Source" and deactivate "Animate Y forward" in it.
### b) AnimationBP: Create a new AnimBP using the skeleton of your MetaHuman. Pick "Live Link Pose" for the input pose and retarget the asset in Optitrack. Use the correct Live Link name (the name of your object in Motion) to synchronize the animation correctly.
### c) Settings in the MetaHumanBP: Ensure that "LODYSync" is set to >= 1 and select the created Anim BP for the skeletal mesh. Also ensure to live link the skeletal animation component.

## 3. Synchronize Metahuman with Yourself:
Hop into the Motion-Tracking suit and open the Builder in the Motion application. Pick one of the skeletons (we picked Baseline (41), since we wanted both to be tracked) and place the markers as shown. Create a new object and name it as you like.

## ... FAQ:

### What is a MetaHuman? …
