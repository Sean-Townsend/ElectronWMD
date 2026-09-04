# **Sony NW-HD1 Music Manager**

A modern Windows application for managing music on the Sony NW-HD1 Network Walkman without needing Sony SonicStage.

<br> <br>

## First things first

This project would not be possible without the great work already done by many people in the community, particularly Asivery and Stefano Brilli.

I have built on their already excellent work and made a number of improvements, particularly for the Sony NW-HD1, to make the software easier to use and help keep these fantastic Sony players alive.

I'm not trying to reinvent the wheel — I've taken already excellent software and tried to make it a little better for NW-HD1 owners.

A huge thank you to everyone who has contributed to the projects that came before this one.

<br> <br>

## What is this?

The Sony NW-HD1 is a fantastic little music player, but its original software, SonicStage, can make using the device on modern Windows PCs difficult and frustrating.

This project provides a modern Windows interface for managing your NW-HD1, while building on the excellent work of the Web MiniDisc and ElectronWMD projects.

<br> <br>

## What can it do?

🎵 Upload music to your NW-HD1

📥 Download music from your NW-HD1

🗑️ Delete tracks

✏️ Edit track and album information

📚 Browse your music by Tracks, Albums or Artists

📂 Collapse and expand albums and artists

🔍 Efficiently handle large music libraries

💻 Designed to run on Windows

🚫 No need to use Google Chrome

🚫 No need to use SonicStage

<br> <br>

## Screenshots
![nwhd1_start_S](docs/images/nwhd1_start_S.png)



![nwhd1_tracks_S](docs/images/nwhd1_tracks_S.png)


![nwhd1_artist_S](docs/images/nwhd1_artist_S.png)


![nwhd1_album_S](docs/images/nwhd1_album_S.png)


![nwhd1_rename_S](docs/images/nwhd1_rename_S.png)



![nwhd1_upload_S](docs/images/nwhd1_upload_S.png)

<br> <br>


## 📥 Download

If you're an NW-HD1 owner and just want to use the application, you don't need to build anything.

Go to the Releases page and download the latest Windows release.

Install/run the application, connect your NW-HD1 and start managing your music.

Windows users: You do not need Node.js, Git, Electron or any development tools to use the pre-built application.

<br> <br>

## 🎧 Sony NW-HD1

This fork has been developed specifically with the Sony NW-HD1 Network Walkman in mind.

<br> <br>

## ⚠️ Important

This is an unofficial community project and is not affiliated with Sony.
Always keep a backup of important music before making changes to an old device.

<br> <br>

## New features
- Virtualised track list
- Only visible rows are mounted, fixing severe scrolling lag when working with large libraries containing 3,000+ tracks.
- Tracks / Albums / Artists views
- Improved album and artist grouping
- Albums and artists are re-grouped using each track's own tags rather than relying solely on the device's stored group boundaries. This helps prevent albums from being fragmented into multiple groups when tagging is slightly inconsistent, such as differences in casing or whitespace.
- Albums and artists can be collapsed and expanded. Collapse state is tracked separately for each view.

<br> <br>

## Fixes
- Fixed collapsed albums silently re-expanding after deleting, renaming or uploading tracks.
- Fixed album collapse/delete buttons sometimes not responding to clicks.
- Fixed track numbers being clipped to a single digit on devices with more than 9 tracks.
- Fixed the Title column header not lining up with the actual track/album title text.
- Moved the upload button into the toolbar so that it no longer floats over the last track.
- Fixed the playback transport bar showing a misleading "ready to play" state on devices that do not support remote playback control. It is now hidden on those devices.
- Fixed NW-HD1, NW-HD2 and NW-HD3 all being identified as NW-HD3.
- Fixed a Windows-specific Electron issue which could prevent the application from loading correctly.
- Fixed Windows Git Bash/MSYS2/Cygwin detection in run-fixes.sh.
- Fixed Windows packaging issues caused by Electron Builder attempting to download unnecessary macOS code-signing tools.

<br> <br>

## This project is based on existing work

This project is a fork of Asivery/ElectronWMD.

ElectronWMD itself builds on the excellent Web MiniDisc project and the work of its contributors.

The webminidisc submodule in this repository points to Sean-Townsend/webminidisc rather than the original repository, as most of the changes made for this fork are contained there.

This project would not exist without the people who have already spent years researching these devices, reverse-engineering their protocols and developing the software that allows them to continue to be used today.

<br> <br>

## A note about SonicStage

The goal of this project is not to replace every feature that SonicStage ever provided.

Instead, it is about providing a simple, modern way of managing music on these old Sony players and helping keep hardware that is still perfectly usable alive.

If you still have an NW-HD1/2/3 sitting in a drawer, hopefully this gives you a reason to get it working again.

<br> <br>

## For developers

The project consists of two parts:

The main Electron application
The renderer (the Web MiniDisc project itself)

This repository contains the main Electron application. When building, it will clone the renderer repository and build that as well.

The webminidisc submodule points to the sean-townsend-changes branch of the Sean-Townsend Web MiniDisc fork.

<br> <br>

## Requirements

You will need Node.js and the appropriate development tools for your platform.

Install the Node modules:

npm i

Depending on your Node.js version, the --legacy-peer-deps switch may be required:

npm i --legacy-peer-deps

<br> <br>

## Development

Start the development version:

npm start

Build a production version:

npm run dist

Build the macOS version:

npm run dist-mac

<br> <br>

## Important development changes

Web MiniDisc Pro relies on older versions of packages including React and Material UI.

Depending on your Node.js version, build-renderer.sh may need to use:

npm i --legacy-peer-deps

instead of:

npm i

<br> <br>

## macOS development
Install Xcode Command Line Tools & Homebrew

In Terminal:

xcode-select install

and:

/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
Install gcc & libvips

In Terminal:

brew install --build-from-source gcc

Once this has finished:

brew install vips

The second command may install gcc again using a pre-built binary. This is normal if gcc is required by vips.

Build

Install the dependencies:

npm i --legacy-peer-deps

Then create the macOS binary packages:

npm run dist-mac
De-quarantine the application

macOS may quarantine locally built applications.

To remove the quarantine attribute:

xattr -d com.apple.quarantine "/path/to/your.app"
Sign the binary

To code-sign the local binary with a self-signing certificate:

codesign --sign - --force --deep "/path/to/your.app"

That should be everything required to build and run the application on macOS.

<br> <br>

## Issues and support

If you find a problem, please open an issue on this GitHub repository.

You can also reach out to the community through the MiniDisc.wiki Discord, particularly the #research and #software-help channels.

<br> <br>

Sony, Network Walkman, NW-HD1 and SonicStage are trademarks of Sony. This is an unofficial community project and is not affiliated with or endorsed by Sony.
