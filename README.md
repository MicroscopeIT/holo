# Holo Model Series

## Project location

Unity project is located in unity/Holo directory
To see initial model please load **AnimatedModels** scene located in *Assets/Scenes*

## Installation

### Prerequisites
  * Setup Hololens with Windows Device Portal enabled: https://docs.microsoft.com/en-us/windows/mixed-reality/using-the-windows-device-portal
  * Install Holo Model Series application on Hololens (use relasese versions: https://github.com/MicroscopeIT/holo/releases)
    Application instalation: https://docs.microsoft.com/en-us/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens

  **IMPORTANT**
      If you got *.NET CoreRuntime* invalid or missing version error please install application with additional dependencies. To do this select option: *Allow me to select framework packages*, and in next step select the *Microsoft.NET.CoreRuntime.1.1.appx* file from release archive (Dependencies -> x86).

  * Convert your input models into Asset Bundles.

      * You can import models as a series of VTK models. The [input format specification is here](https://github.com/MicroscopeIT/holo/tree/master/Input%20documentation). Example VTK model is inside `Test Model` subdirectory there. This is the advised format, that supports animation using blend shapes.

      * Or you can import models with each layer loaded from Unity assets (so it can be .obj, .prefab or any other model format supported by Unity). Example is inside `unity/Holo/Assets/Test Models/Skull/` in this repository.

  * Upload AssetBundles with models into Hololens headset
  * Run application

#### Converting VTK model series into Asset Bundles

Open Unity project from unity/Holo.

1. Run script: **Holo -> Convert VTK model to an AssetBundle's GameObject**
2. Choose the directory with model time series in VTK files
3. Your resulting AssetBundle is located in _**<repository location>/unity/Holo/Assets/StreamingAssets/<name of converted directory>\_bundle(.manifest)**_

#### Uploading AssetBundles to Hololens headset

1. Go to Windows Device Portal of Hololens headset
2. Go to _**System -> File Explorer**_
3. Navigate to: _**User Folders \ LocalAppData \ HoloModelSeries\_1.0.0.0_x86\_\_<hash/crc> \ LocalState**_
4. Upload Asset Bundle files (**\_bundle** along with **\_bundle.manifet**) in to **LocalState** directory one by one with the *Upload* button (first you need to select file from hard drive, you can drag and drop it as well)

## Usage

After starting the application, choose the "Shared Experience" mode in the UI:

- Click the "Start Session" button to be the server (like a teacher in the classroom) that dictates the view of other participants.

- Or choose a session name (corresponding to your Hololens name) and then click "Join Session" to be the student (observing  what teacher sets).

- Or choose "Offline Mode" to test the application on your own, without being any server or client. The effect in principle looks similar to clicking "Start Session", but the application doesn't listen on any port, doesn't synchronize anything etc.

Teacher can then choose a model, choose layers to display inside, transform it and so on.

Note that currently HoloModelSeries application loads only AssetBundles uploaded to Hololens headset. Models must be uploaded before application is run (rescanning of the collection's models is not yet implemented).

**IMPORTANT**: If you upload new models HoloModelSeries must be closed. For the moment you need to run other application for the system to unload completly HoloModelSeries application.
