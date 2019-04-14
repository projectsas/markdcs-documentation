# MarkDCS IntelliJ Plugin

MarkDCS IntelliJ Plugin allows to edit and compile MarkDCS applications using Jetbrains' IntelliJ IDEA IDE.

{% hint style="info" %}
Before starting using the MarkDCS plugin, it is recommended that you familiarize yourself a bit with IntelliJ IDEA
{% endhint %}

## Installation

1. If you don't have it, download and install [IntelliJ IDEA](https://www.jetbrains.com/idea/), both Community and Ultimate versions work, the choice is up to you
2. Start IntelliJ IDEA
3. Add a MarkDCS plugin repository to IntelliJ IDEA:
   1. Open plugins settings in _File \| Settings \| Plugins_
   2. Click on the gear icon in the top toolbar
   3. Select _Manage Plugin Repositories_
   4. Click on the "+" button
   5. Insert the following URL`https://www.projectsas.it/markdcs/intellij/updatePlugins.xml`
   6. Click OK
4. Install the MarkDCS plugin:
   1. Open plugins settings in _File \| Settings \| Plugins_
   2. Go to the _Marketplace_ tab
   3. Search for "MarkDCS"
   4. Click on the _install_ button
5. Restart IntelliJ IDEA

## Creating a MarkDCS SDK

TODO

## Creating a project

To create a new MarkDCS project:

1. Open the _New Project_ dialog in IntelliJ IDEA
2. Select MarkDCS in the list on the left
3. Click _Next_
4. Select a valid MarkDCS SDK or [create one](markdcs-intellij-plugin.md#creating-a-markdcs-sdk)
5. Click _Next_
6. Enter project name and location
7. Click _Finish_

MarkDCS plugin automatically creates the default project structure, in project root directory, with sources folder and a basic configuration file.

