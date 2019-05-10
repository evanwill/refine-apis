---
title: Prep
nav: true
---

# Prep

For this workshop you will need a web browser and OpenRefine. 

{% capture text %}
##### 1. Install Java 

OpenRefine is a [Java](http://java.com/en/){:target="_blank"} application and requires Java JRE to run. Download and install Java if you do not have it (you can check by typing `java -version` into a terminal). You want a 64-bit version, which is usually the default install. It is also a good idea to uninstall any old Java versions on your machine.

- *Windows and Mac:* Clicking "Free Java Download" on the [Java](http://java.com/){:target="_blank"} site will get you the correct installer. (When installing be sure to uncheck the "recommended" option to add any bundled spamware to your system!)
- *Linux:* Install from your distro's repositories, for example `sudo apt install default-jre` on Ubuntu/Debian (this is usually OpenJDK rather than Oracle's version).

-----------------

##### 2. Download Refine

Download the most recent [OpenRefine package](http://openrefine.org/download.html){:target="_blank"} for your OS. Releases are posted on the [OpenRefine site](http://openrefine.org/download.html){:target="_blank"} or [GitHub releases page](https://github.com/OpenRefine/OpenRefine/releases/){:target="_blank"}. (this workshop used OpenRefine V3.1) 

-----------------

##### 3. Extract Refine

Unzip the OpenRefine package to a permanent location, for example in your User directory, Home, or Documents.

- *Windows:* unzip by right clicking and selecting Extract All. 
- *Mac:* drag the `dmg` to the application folder (Mac has known [issues](https://github.com/OpenRefine/OpenRefine/wiki/Installation-Instructions#mac-osx){:target="_blank"}, try these [solutions](https://evanwill.github.io/_drafts/notes/open-refine-osx.html){:target="_blank"}). 
- *Linux:* unpack in desired location with with `tar`, for example `tar xzf openrefine-linux-3.1.tar.gz`. 
{% endcapture %}
{% include card.md text=text header="Setup OpenRefine" %}

Full documentation is available on the [official wiki](https://github.com/OpenRefine/OpenRefine/wiki/){:target="_blank"}.
