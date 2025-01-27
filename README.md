![requiredItems](https://github.com/luca-g97/SpatialComputing/blob/main/Assets/teaser_image.jpg)

In this project, we will explore one of the most advanced tools for creating digital twins: **MetaHumans**. By combining MetaHumans with the **OptiTrack motion capture system**, you can bring your digital twin to life in real-time with minimal latency. Follow this detailed guide to create your own MetaHuman, which can be seamlessly imported into any project and animated using motion tracking.

---

# Recommended Requirements:

## 1. Hardware:
- **LAN network connection**
- **OptiTrack motion capture system**
- **OptiTrack motion tracking suits**
- (Additionally: **passive markers**)
- **Laptop/PC** capable of real-time rendering (with a LAN port for connectivity)
- **LAN cable**

## 2. Software:
- **Unreal Engine** (we used Engine Version 5.4, but other versions should also work)
- **Motive application**

---

# Setup:

## 1. Install the Epic Games Launcher
Download and install the [Epic Games Launcher](https://store.epicgames.com/en-US/download) from the website. Open it and create your Epic Games Account or log in directly if you already have one.

## 2. Install Unreal Engine
After opening the launcher, choose the **"Unreal Engine"** tab on the left. Navigate to **"Library"** at the top. Add your desired **Engine Version** with the yellow **"Plus Button"**. Click it and select your Unreal Engine version from the dropdown in the top right of the now-appearing container. Hit **Install** and confirm in the next window. Unreal Engine will now begin downloading, which may take some time depending on your network speed. You can monitor the progress or pause the download in the bottom left of the launcher.

## 3. Install and Activate the Live Link Plugin
Open Unreal Engine using the **Launch** button in the top right once the Engine is downloaded. Pick one of the standard projects and wait until it opens. Once the project is created, select **"Edit"** from the top left menu and choose **"Plugins"**. Search for **"Live Link"**, tick the first option available, and restart Unreal Engine to activate it. You can now customize the scene to create an engaging environment for your MetaHuman interactions later.

## 4. Download and Install OptiTrack Plugin & Ensure Motive Installation
Download the [OptiTrack Plugin](https://www.optitrack.com/support/downloads/plugins.html) from the official website and place the plugin contents into the following folder:
`C:\Program Files\Epic Games\UE_5.4\Engine\Plugins\Marketplace\OptitrackLiveLink`

Make sure that the OptiTrack system has a licensed version of [Motive](https://www.optitrack.com/support/downloads/) installed as well.

---

# Digital Twin Creation

## 5. MetaHuman Creation
Open the following website in your browser: [MetaHuman Creator](https://metahuman.unrealengine.com/). Log into your Epic Games account and select your preferred Unreal Engine version (we used 5.4, but other versions should work) from the dropdown menu. Click **"Launch MetaHuman Creator"** (this may take a while). Customize the MetaHuman to your needs and export it as an `.fbx` or `.uasset` file for later import into Unreal Engine.

---

# Final Steps

## 6. Edit Motive Live Settings
1. Since you will need a license for Motive and the OptiTrack system, ensure you have a PC with Motive installed. Make sure there is one LAN port available to connect your PC later. Open the Motive application.
2. Place reflective markers within the cameras' field of view and return to the PC. Click on **"eSync 2"** in the **"Devices"** section on the top right. Select **"Internal Free Run"** from the **"Source"** options in the **"Sync Input Settings"** section. Check if the markers are visible in the camera view at the bottom middle of the screen.
3. Remove all markers from the cameras' sight and mask any other visible detected objects to avoid interference during **"Wanding"**. Calibrate the system using the **"Wand"** and ensure you cover as much of each camera's field of view as possible. Place the **"Calibration Square"** in the middle of the room and select it to set the ground plane correctly.
4. Open the **"Settings"** menu and switch to the **"Streaming"** tab. Ensure the following settings are configured to stream data correctly to Unreal Engine:
   - **Local Interface**: `10.21.3.162`
   - **Transmission Type**: Unicast
   - **Skeleton Coordinates**: Local
   - **Bone Naming Convention**: UnrealEngine
   - **Up-Axis**: Y-Axis

![requiredItems](https://github.com/luca-g97/SpatialComputing/blob/main/Assets/Setup.jpg)

#### IMPORTANT: Remember or write down the internal IP address (`10.21.3.162`). You will need it to add the correct Live Link Source in Unreal Engine.

## 7. Add Live Link Source
1. Open the Live Link window by navigating to **Window > Live Link**.
2. Add a new source and uncheck **"Automatic"**.
3. Open a command prompt and enter `ipconfig` to retrieve your local IP address (typically starting with `10.x.x.x`). Enter this as the local address.
4. Enter the IP address (`10.21.3.162`) from Motive as the **Source Address**.
5. Finally, create the **"Live Link Source"**, select it, and deactivate **"Animate Y Forward"** in the details section.

## 8. Retarget Skeleton
1. Import the created MetaHuman into your Unreal Engine project via drag and drop.
2. **Animation Blueprint (AnimBP)**: Create a new AnimBP using the skeleton of your MetaHuman. Select **"Live Link Pose"** for the input pose and retarget the asset in OptiTrack. Use the correct Live Link name (the name of your object in Motive) to synchronize the animation correctly.
3. **Settings in the MetaHumanBP**: Ensure that **"LODSync"** is set to `>= 1` and select the created AnimBP for the skeletal mesh. Also, ensure the skeletal animation component is linked to Live Link.

![requiredItems](https://github.com/luca-g97/SpatialComputing/blob/main/Assets/live_link_pose.png)

## 9. Synchronize MetaHuman with Yourself
Put on the motion-tracking suit and open the **"Builder"** tool in the Motive application. Pick one of the skeletons (we used **Baseline (41)**) and place the markers as shown. Create a new object and name it as you like. Ensure the correct Live Link name is set in the AnimationBP of your MetaHuman.

---

## Now everything is set up properly, and only your imagination limits what your digital twin can do! Beneath are some Impressions of Our Session:
Ever dreamed of recreating iconic scenes like the bullet-dodge from *The Matrix*? Now you can:
![requiredItems](https://github.com/luca-g97/SpatialComputing/blob/main/Assets/Matrix.gif)

Imagined yourself as a digital superhero saving everyone from a grenade? No problem anymore:
![requiredItems](https://github.com/luca-g97/SpatialComputing/blob/main/Assets/Grenade.gif)

Or just wanted to mess around and create funny clips? We’ve got you covered:
![requiredItems](https://github.com/luca-g97/SpatialComputing/blob/main/Assets/DriveBy.gif)

---

## Recommended Sources:
- [Live Link Plugin](https://docs.optitrack.com/plugins/optitrack-unreal-engine-plugin/unreal-engine-optitrack-live-link-plugin/quick-start-guide-real-time-retargeting-in-unreal-engine-with-live-link-content) - A step-by-step guide to setting up and using the OptiTrack Live Link plugin.
- [Unreal Live Link Setup Tutorial](https://www.youtube.com/watch?v=rpd9KxQyeek&t=358s&ab_channel=TrashPraxis) - A video tutorial for setting up Live Link in Unreal Engine.
- [Motive Calibration](https://docs.optitrack.com/motive/calibration) - Official documentation for calibrating the OptiTrack system.

---
---

## FAQ:

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
* Performance: High-fidelity MetaHumans can be resource-intensive, requiring powerful hardware for real-time rendering.
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

