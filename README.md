# Unity Packaging

[Apply automation to your project](./documentation/use-automation.md)

## Environment
- Local
  
  ![OS - macOS](https://img.shields.io/badge/OS-macOS-blue?logo=apple&logoColor=white)
  ![Generic badge](https://img.shields.io/badge/Unity-2022.1.12f1-lightgray?logo=unity&logoColor=white)

- Dockerised Unity Editor
  
  [![Use Docker](https://img.shields.io/badge/Docker-unityci/editor-blue?logo=docker&logoColor=white)](https://hub.docker.com/r/unityci/editor)

## Unity license
Get Unity licenses for Personal plan.

- [Where is my Unity license file stored?](https://docs.unity3d.com/Manual/ActivationFAQ.html#licensefilefolders)
  
  | OS | Path |
  | --- | --- |
  | macOS | `/Library/Application\ Support/Unity` |
  | Linux | `~/.local/share/unity3d/Unity/Unity_lic.ulf` |
  | Windows | `C:\ProgramData\Unity\` |

- Submit a license request from a command line and browser

  - [Windows](https://docs.unity3d.com/Manual/ManualActivationCmdWin.html)
  - [macOS and Linux](https://docs.unity3d.com/Manual/ManualActivationCmdMac.html)

 ### Procedure

 1. Create a **license request file** ( `.alf` ) from the command line.
    
     ```bash
     /Applications/Unity/Hub/Editor/2022.1.12f1/Unity.app/Contents/MacOS/Unity \
     -nographics \
     -batchmode \
     -createManualActivationFile \
     -logfile
     ```
     <details>
     <summary><i>result</i></summary>
    
     ```
     Unity Editor version:    2022.1.12f1 (916d9c03b898)
     Branch:                  2022.1/staging
     Build type:              Release
     Batch mode:              YES
     macOS version:           Version 14.2.1 (Build 23C71)
     Darwin version:          23.2.0
     Architecture:            arm64
     Running under Rosetta:   NO
     Available memory:        8192 MB
     [LicensingClient] Error: Code 10 while verifying Licensing Client signature (process Id: 854, path: "/Applications/Unity Hub.app/Contents/Frameworks/UnityLicensingClient_V1.app/Contents/MacOS/Unity.Licensing.Client")
     [Licensing::Module]  Error: LicensingClient has failed validation; ignoring
     [LicensingClient] Handshaking with LicensingClient:
	     version: 1.15.0+66d4389
	     Session Id: 9342ce6809954a45a76f80bc08e4135f
	     Machine Id: 1tHzQC2UBVo6fy+/N3i02Etdd74=
     [Licensing::Module] Successfully connected to LicensingClient on channel: "LicenseClient-pokeum" (connect: 0.00s, validation: 0.02s, handshake: 0.30s)
     Entitlement-based licensing initiated
     [Licensing::Module]  Error: Access token is unavailable; failed to update
     [LicensingClient] Error: Code 200 while updating license in client (status: Licenses updated.)
     [Licensing::Module] Generating manual activation license file: /Users/pokeum/Unity_v2022.1.12f1.alf
     [LicensingClient] Successfully processed ALF generation request: /Users/pokeum/Unity_v2022.1.12f1.alf
     [Licensing::Module] Manual activation license file successfully saved.
     ```
     </details>
     
 2. Use that `.alf` file to generate a **Unity license file** ( `.ulf` ) from Unity.
    
     [Generate a Unity license file](./documentation/generate-ulf.md)

 3. Use that `.ulf` file to **activate your license** from the command line.
    
     ```bash
     /Applications/Unity/Hub/Editor/2022.1.12f1/Unity.app/Contents/MacOS/Unity \
     -nographics \
     -batchmode \
     -manualLicenseFile "/Users/pokeum/Downloads/Unity_v2022.x.ulf" \
     -logfile
     ```

## Unity packaging
Use the [Unity Editor command line arguments](https://docs.unity3d.com/Manual/EditorCommandLineArguments.html) to package unity assets from the command line.

```bash
/Applications/Unity/Hub/Editor/2022.1.12f1/Unity.app/Contents/MacOS/Unity \
-batchmode \
-quit \
-nographics \
-logfile \
-projectPath "/Users/pokeum/Git/pokeum/unity-packaging/myproject" \
-exportPackage "Assets/MyPackage/Include" "Assets/Scenes/IncludeScene.unity" \
"mypackage-0.0.0.unitypackage"
```

> [!NOTE]
> **Export package location**
> <br/>: `/Users/pokeum/Git/pokeum/unity-packaging/myproject/mypackage-0.0.0.unitypackage`
> <br/>(relative to the Unity project root)
