---
title: Prep
nav: true
---

# Prep

For this workshop you will need a web browser (Firefox or Chrome) and OpenRefine. 

In the past, installing Java was required--however, this is *no longer necessary* on Windows and Mac!
Check the [official installation documentation](https://docs.openrefine.org/manual/installing) or follow the instructions for your system below:
{% capture windows %}
- **Download:** visit the [Refine download page](https://openrefine.org/download.html) and choose the latest "Windows kit with embedded Java" package. This is a self contained package that includes everything needed to run Refine on your system.
- **Extract:** the package you downloaded will be a zip file that needs to be extracted (e.g. "openrefine-win-with-java-3.4.1.zip"). Unzip the package by right clicking and selecting Extract All. Move the resulting folder to a sensible permanent location on your computer, e.g. "C:\openrefine\" or Documents.
- **Run:** inside the folder you extracted, double click "openrefine.exe" to start Refine. The first time you may get a warning that the publisher could not be verified, dismiss the warning and click *Run*. Once open, pin the Refine icon to your taskbar for easy access in the future! 

*Note:* if you would like to use the traditional Refine kit, check [notes on installing Java on Windows](https://evanwill.github.io/openrefine-b/content/win-java.html).
{% endcapture %}
{% capture mac %}
- **Download:** visit the [Refine download page](https://openrefine.org/download.html) and choose the latest "Mac kit". This is a self contained package that includes everything needed to run Refine on your system (e.g. "openrefine-mac-3.4.1.dmg").
- **Install:** drag the Refine kit from your downloads to the Applications folder.
- **Run:** click the Refine icon in your Applications folder. 
{% endcapture %}
{% capture linux %}
- **Java:** if you do not have Java JRE/JDK, install latest Java from your distro's repositories. For example, on Ubuntu/Debian: `sudo apt install default-jre`
- **Download:** visit the [Refine download page](https://openrefine.org/download.html) and choose the latest "Linux kit".
- **Extract:** the package you downloaded will be a compressed archive (e.g. "openrefine-linux-3.4.1.tar.gz"). Unpack the file using your Archive manager or Tar (e.g. `tar xzf openrefine-linux-3.4.1.tar.gz`) to a sensible permanent location (e.g. in your Home directory).
- **Run:** open a terminal in your OpenRefine directory and type `./refine`.
{% endcapture %}
{% include accordion.html title1="Windows" text1=windows title2="Mac" text2=mac title3="Linux" text3=linux %}

# Use Refine

Since Refine is a Java application, starting is a bit different than normal GUI programs. 
There is two parts to Refine: 1. a terminal window running the application in Java, 2. a GUI interface which is a "web page" in your browser.

{% include figure.html img="openrefine.png" alt="OpenRefine terminal and GUI" width="100%" %}

1. **Start the Java app:** Opening Refine differs depending on your OS, but in all cases the app will start running in a terminal window which you can ignore and minimize (but do not close!).
    - *Windows:* double click `openrefine.exe` (You may get a warning that the publisher could not be verified, ignore it, and click *Run*. Once open, pin the Refine icon to your taskbar for easy access in the future). 
    - *Mac:* click the Refine icon in the applications folder. 
    - *Linux:* in the OpenRefine directory open terminal and type `./refine`.
2. **Use the GUI:** Once Refine is running in a terminal, your default web browser should automatically open with the interface. If it does not open automatically or you close the browser tab, find the GUI by typing <http://127.0.0.1:3333> or `localhost:3333` in your address bar. 
3. **Shut down:** close any browser tabs with the GUI, then stop the host terminal window with `Ctrl+C` (or `Command-Q` on Mac). This will ensure any open projects are saved.

{% include alert.md text="The user interface is rendered by your web browser, but Refine is not a web application. 
Although it uses the term *upload* and *download*, no information is sent online and no internet connection is necessary.
For best results, use Firefox, Chrome, or Chromium browser." color="success" %}
