# Radium-Releases

Radium is a research 3D Engine for rendering, animation and processing.
It is developed and maintained by the [STORM research group](https://www.irit.fr/STORM/site/).

The Radium ecosystem is composed of several components (e.g. libraries, apps, plugins).
The purpose of this repository is to provide a **unique entry point** to easily fetch, compile and run all the tools provided by Radium.
This repository also builds the ecosystem and provide [pre-compiled binaries](https://github.com/STORM-IRIT/Radium-Releases/releases) for the different releases.

## Related repositories

- **Radium Libraries** (<https://github.com/STORM-IRIT/Radium-Engine>): contains the Radium libraries.
- **Radium Apps** (<https://github.com/STORM-IRIT/Radium-Apps>): contains several applications, including MainApp, which is for now the default software with GUI. This repository also demonstrates command-line applications. Dependencies: Radium Libraries
- **Radium Plugins Example** (<https://github.com/STORM-IRIT/Radium-PluginExample>): contains plugins examples, demonstrating how to write, compile and use plugins with MainApp. Dependencies: Radium Libraries, Radium Apps.
- **Radium Official Plugins** (<https://gitlab.com/Storm-IRIT/radium-official-plugins>): general purpose plugins. Dependencies: Radium Libraries, Radium Apps.

## Am I using the right repository ?

Depending on you needs, you may want to:

- Use Radium as a viewer and processing software, with graphical user interface. That's the most simple case: simply download the latest release, and run. See <https://github.com/STORM-IRIT/Radium-Releases/releases>. You may also want to compile it from source, checkout [here](Cmake-builchain)
- Contribute to Radium, or develop your own application of plugin: **Radium Libraries** is the default and mandatory repository you need to fetch first. If you only want to _use_ Radium, you still need to compile and install the libraries (see [documentation](https://storm-irit.github.io/Radium-Engine/)).
 Then,
  - If you want to contribute to the application or plugins developments, fetch and compile the **Radium Apps** and **Radium Official Plugins** respectively.
  - If you want to write your own application of plugin, checkout the [HelloRadium](https://github.com/STORM-IRIT/Radium-Apps/tree/fix-compilation/HelloRadium) and **Radium Plugins Example** projects.

## Content of this repository

### Continuous Integration Scripts

Fetch and compile the whole ecosystem each time any of the `master` branch of the related repositories is updated.
