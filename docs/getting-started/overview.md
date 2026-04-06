# MARS Overview

## What is MARS?

MARS (Modular Architecture for Robot Systems) is an architecture developed by STZ Robotics for building robot software. It implements modules for each mechanism and clearly separates them into different files to keep consistency, allowing teams to easily create and maintain complex robot systems in FRC competitions. This tool is designed to supercharge the workflow of FRC software teams by integrating project scaffolding, over-the-air (OTA) updates, and telemetry management directly into Visual Studio Code.

## Our mission

Our mission is to provide a user-friendly architecture for new teams while also offering advanced features for experienced teams to take their code to a new level.

## Key features of MARS

- **Project builder**: Forget about manual cloning and configuring. The Project Builder automatically fetches the latest MarsTemplate, clears the git history for a fresh start, and automatically injects your FRC Team Number directly into the WPILib preferences.
- **Advanced module scaffolding**: Stop writing boilerplate code. Right-click any folder inside your project to generate a complete MARS Module architecture in seconds.
- **Over-the-Air (OTA) ecosystem updates**: Keep your team on the same page without passing ZIP files around. With a single click from the Side Panel, the extension checks GitHub Releases to download, extract, and install the latest versions of: MARS GCS (Ground Control Station), Alloy Dashboard (Telemetry & Diagnostics), and MARS LogTool (Log requests).
- **Persistent Framework settings**: Configure your default Team Number, workspace paths. The extension saves your preferences globally in VS Code, ready to be injected into any new project you create.
