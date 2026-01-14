## juice_ptr plugin - JUICE pointing request plugin 🎯

### 🏃🏼‍♂️‍➡️🏃‍♀️‍➡️ Running the plugin: JUICE PTR

#### 🍎 macOS/ 🐧 Linux

* Open a terminal and navigate to the **ess-plugin** repository directory

      $ cd ess-plugin
* Execute the launcher

      $ .\plugin_launcher.sh juice_ptr

####  🪟 Windows (PowerShell terminal)
* Open a PowerShell terminal and navigate to the **ess-plugin** repository directory

      PS> cd ess-plugin
* Execute the launcher

      PS> .\plugin_launcher.ps1 juice_ptr



### Plugin Entry Point: Pointing Editor Dialog

This is the entry point of the plugin. The dialog accessible here drive the generation of the scene that will be displayed in the viewer. The scene creator uses as basis a JUICE metakernel. A SPICE metakernel is a text file that specifies and documents a collection of SPICE kernels to be loaded together, providing a reproducible and convenient way to configure a Cosmographia scene.

🙏 Remember that the plugin uses the **local metakernel** which is a metakernel included in the JUICE SKD (SPICE kernel dataset) whose internal PATH_VALUES are set to local file system path.

Additionally the user provides a **pointing request expressed in XML format**. This XML file is an interfase between SGS and Flight dynamics describing a request to implement an attitude profile for the spacecraft. The SGS has implemented a simulation software **(AGM/OSVE)** that is able to interpret this XML file and generate a SPICE CK file containing the expected attitude.
This CK together with the rest of the metakernel will be loaded by Cosmographia to create the scene. The CK is loaded in such a way that it has **precedence** over the JUICE metakernel contents ensuring that Cosmographia gets the attitude for JUICE from the pointing request.



<div style="text-align:center"><img src="images/dialog_ptr_editor.png" alt="Dialog Scenes" style="border:1px solid #000; border-radius:15px"></div>

When clicking the **Visualize** button, the pointing request is processed by OSVE in the background, the scene is created and visualized. The execution also extends the capabilities of Cosmographia extending the menus availble to the following. 

The new features are described in the following sections. 

<div style="text-align:center"><img src="images/main_menu_juice_ptr.png" alt="" style="border:1px solid #000; border-radius:15px"></div>

In the case of 🍎 macOS/ 🐧 Linux the **Timeline Dialog** appears automatically (see [timeline dialog section](#timeline-dialog-) for details).



The entry point can be accessed again using the scenes menu, that gives access to this entry point and to a simpler entry point for the basic scene (described in the following section).

<div style="text-align:center"><img src="images/menu_scenes.png" alt="Menu Navigation" style="border:1px solid #000; border-radius:15px"></div>


#### Additional entry point Basic Scene Dialog

In this alternative entry point, the metakernel contents are used directly to created the scena althoug the user can optionally provide extra kernels to be loaded.

<div style="text-align:center"><img src="images/dialog_basic.png" alt="Dialog Scenes" style="border:1px solid #000; border-radius:15px"></div>

The execution extends the capabilities of Cosmographia extending the menus availble to the following. The new features are described in the following sections. 

<div style="text-align:center"><img src="images/main_menu_juice_mk.png" alt="" style="border:1px solid #000; border-radius:15px"></div>


### Runtime Menu ⚙️

<div style="text-align:center"><img src="images/menu_runtime.png" alt="Menu Navigation" style="border:1px solid #000; border-radius:15px"></div>

<div style="text-align:center;"><img src="images/dialog_console.png" alt="Dialog Timeline" style="border:1px solid #000; border-radius:15px"></div>


‼️ **Danger Zone** 💥 ‼️
<div style="text-align:center"><img src="images/dialog_catalogs.png" alt="Dialog OSVE log" style="border:1px solid #000; border-radius:15px"></div>


### Pointing Menu 🎯

This menu appears once a pointing request is processed by OSVE in the background. It allows to access to the execution results and to a block navigation timeline.

<div style="text-align:center"><img src="images/menu_pointing.png" alt="Menu Navigation" style="border:1px solid #000; border-radius:15px"></div>

#### Timeline Dialog 🕒
This component allows the easy navigation through pointing blocks. It is connected with Cosmographia time control allowing to go back and forward in time using blocks as references.
The observation blocks in a request are displayed as purple bars in an interactive timeline that drive the time control. They are separated by gaps that represent the slew blocks between observations. 

The block timing information is summarized in a table below the timeline, including the block start and end times, its duration and the block content. **Double clicking** on a block boundary will jump the scene to that time.

‼️ **Not available in Windows Version** ‼️
<div style="text-align:center;"><img src="images/dialog_timeline.png" alt="Dialog Timeline" style="border:1px solid #000; border-radius:15px"></div>


#### OSVE Log Dialog 📝
The dialog shows the OSVE log for the pointing request executed in the background. The viewer allows the filtering of the log messages. This component will show the constraint violations detected by OSVE.
<div style="text-align:center"><img src="images/dialog_osve_log.png" alt="Dialog OSVE log" style="border:1px solid #000; border-radius:15px"></div>

#### OSVE Result Folder 🗂️
Clicking the button will open the OSVE results folder in the local filesystem. In this folder you will find:
* The OSVE log file in JSON format
* The resolved (time bounded) pointing request in XML format
* The SPICE CK file containing the spacecraft attitude for the pointing request in binary format

<div style="text-align:center"><img src="images/dialog_osve_results.png" alt="Dialog OSVE log" style="border:1px solid #000; border-radius:15px"></div>

### Jupiter structures Menu 🪐

This menu gives access to the dialogs and menu items controlling the visualization of bodies and science structures of the Jovian system. The tabbed dialogs, with a common user interfase, allow to control the visualization of this bodies and structures. Reference and sources for the science structures are provided in the help menu.

<div style="text-align:center"><img src="images/menu_structures.png" alt="Menu Jupiter Structures" style="border:1px solid #000; border-radius:15px"></div>

⚠️ **Jupiter Belt loading could take a significant amount of time and impact on the visualisation performance**

<div style="text-align:center;"><img src="images/dialog_moons.png" alt="Dialog Moons" style="border:1px solid #000; border-radius:15px"><img src="images/dialog_rings.png" alt="Dialog Rings and Torus" style="border:1px solid #000; border-radius:15px"></div>

### Navigation Menu 🔭 
The navigation menu gives access to the dialogs and menu items controlling the visualization of sensors and observations.

<div style="text-align:center"><img src="images/menu_navigation.png" alt="Menu Navigation" style="border:1px solid #000; border-radius:15px"></div>

#### Sensors Dialog
The sensons dialog is a convenience interface to control the visualization centered on the JUICE spacecraft. Tabbed by instruments/units, it allows to control the visibility and aspect of the field of view of each sensors. Additionally, functionalities to control the view perspective are provided:
* **Sensor View** that allows to switch the view perspective as seen along the different sensors.
* **JUICE** that centers the view and perspective on the JUICE spacecraft.

<div style="text-align:center;"><img src="images/dialog_sensors.png" alt="Dialog Sensors" style="border:1px solid #000; border-radius:15px"></div>

#### Observations Dialog 

The observations dialog allows to create and control of sensor observations. Based on the [Observation Catalogs](https://cosmoguide.org/catalog-file-defining-an-observation/) available in Cosmagraphia. The feature is considered experimental 🧪.

<div style="text-align:center"><img src="images/dialog_observations.png" alt="Dialog Observations" style="border:1px solid #000; border-radius:15px"></div>

### Help Menu  ℹ️ 
This menu entry is an index of resources containing reference information about plugin features. The OSVE version used by the plugin is also provided in the documentation links.
<div style="text-align:center"><img src="images/menu_help.png" alt="Menu Help"  style="border:1px solid #0d0c0c; border-radius:15px"></div>
<div style="text-align:center"><img src="images/link_science.png" alt="Link Science Structures"  style="border:1px solid #000; border-radius:15px;"><img src="images/link_osve.png" alt="Link OSVE Help" style="border:1px solid #000; border-radius:15px;"></div>
