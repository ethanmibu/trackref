# Agent Instructions for TrackRef

This document provides instructions for an AI agent on how to interact with and contribute to the TrackRef VST/AU plugin project.

## Project Overview

TrackRef is a VST/AU plugin for A/B testing audio mixes. It has two stereo inputs and one stereo output, and a single parameter to switch between the two inputs. The plugin is written in C++.

## Getting Started

To get started with the project, you need to set up the development environment and build the project.

### 1. Set up the development environment

The project requires the VST3 SDK. You can download and set it up by running the `setup.sh` script:

```bash
sh setup.sh --platform mac
```

This will download the VST3 SDK into the `vendor` directory.

### 2. Build the project

To build the plugin, run the `build.sh` script:

```bash
sh build.sh
```

This will build the VST3 plugin and place it in the `build/VST3` directory.

## How to Contribute

You can contribute to the project by adding new features or fixing bugs.

### Adding a new parameter

To add a new parameter to the plugin, you need to:

1.  **Update `generateModel.js`:** Add a new entry to the `MODEL` array in `generateModel.js`. This will define the parameter's name, description, range, and UI properties.
2.  **Regenerate the C++ files:** Run `node generateModel.js` to update the C++ files with the new parameter.
3.  **Implement the parameter's logic:** In `src/vst.cpp`, use the new parameter in the `process` method to modify the audio processing.

### Modifying the processing logic

The audio processing logic is located in the `process` method in `src/vst.cpp`. You can modify this method to change how the plugin processes audio.

## How to Release

To create a release build of the plugin, you can use the `build.sh` script with the `--type` flag to create VST2 and AU versions.

```bash
# Build VST2
sh build.sh --type vst2

# Build Audio Unit
sh build.sh --type au
```

You can also create a release build with a specific version number by modifying the `CMakeLists.txt` file.
