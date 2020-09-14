## Introduction
This **quick** tutorial will walk through how to setup the Shimmer watch-like device to collect time series data of our wrist motion and visualize it using a visualization software, called EatMon.ext.

## Outline
This tutorial will cover the following sections:
1. Requirements of hardward, software
2. Hardware setup
3. Software setup. 
To copy the data from the device into our laptop, we need a software of Shimmer Device, called __Consensys__. It helps us get data in the csv format, recorded from the device

4. Label Data
We will use a software called __MakerParser.exe__ to add some labels to the time series data

5. Data Visualization with software called __EatMon.exe__
## Requirements
### Hardware 
1. Charging station for Shimmer with a USB cable to connect to your laptop. 
This charging station is both a charger and a connector of your Shimmer Device to your laptop. You will need to combine it with Consensys software to read the data from Shimmer device
<img src=/images/charger.png>

2. Shimmer Device:
This device has only two buttons: one on the side of the case, which is the power button. When you push it up, it is power on. 
The second button is the orange circle button. It is the button to start/stop your recording.
<img src=/images/Shimmer.png width=300, height=200>

### Software
You will need to download the following softwares from this 
[Link](http://cecas.clemson.edu/tracking/ShimmerData/Programs/)

1. **Consensys_v0.2.0.zip**: it reads and manage the data (CSV file) from the SD card in Shimmer Device.
2. **MarkerParser.exe**: This software help you mark/label the your data and convert the CSV file and markers of data into txt file. However, in order to visualize the data using EatMon.exe file, you will need to conver the suffix of ".txt" to ".shm". This will be mentioned later.
3. **EatMon.exe** with its dependencies: 
    + 	6minrtc.pb
    +	10minrtc.pb
    +	tensorflow.dll
**EatMon.exe** is a software that load ".shm" data file and visualize the data.

## Hardware Setup
1. **Turn on your Shimmer Device**
    Push the button on the left side of the case up to power on the shimmer. When it is powered on,  the LED B will flash in green light.
<img src=/images/Shimmer.png width=300 height=200>

2. **Charge yoru Device and connect it to your laptop**:  you will need to use a USB cable to connect charging station to your laptop and plug your Shimmer device to your charging station. This will charge your Shimmer device. 

3. **Recording data**
After charging your device and Battery is more than 90%, it is usually safe to plug it out and record data.
**Steps to record data:**
    + **Start Recording:** Press the big orange button for about 5 second until LED B turn green. 
    **Note: Since the device's button is not sensitive, it may not turn green even you press it for a long time. In this case, you may power it off and then turn it on again. Then press the orange button using your nail.**
    + **During recording:** the LED B will flash with blue light about every 10 seconds. 
    + **Stop recording, not turn off your device:** Press the orange button for about 5 seconds again until the green light flashs again
    + **After recording**: plug the Shimmer back to the charging station and use hte Consensys to read the data. 

## Software Setup
1. **Read data from your Device with Consensys software**
Once you open this software after connecting the device to your laptop, you will see the following interface. Check your Battery status.
+ **If your Battery Status show 0.0%:**
**right-click the green cell of your device ->  select Reset -> check the status again.**
This command allow the station to reset Shimmer and get the information of Shimmer.
<img src=/images/consenssys-reset.png width=500 height=300>

+ **To Read your data**
    - Click **IMPORT** to load data from Shimmer to Consensys software
    Then you will see a window pop up 
    <img src=/images/import.png width=500 height=300>

    Just click next or OK for the following pop-up window to import data to the session folder.
    - **Select the data folder** you want to import in the left window and then **Click Right Arrow button**. Finally **Click "Next"**
    <img src=/images/import-2.png>

    - Go to  MANAGE DATA tag
    - Export data to **your own folder**.
    You need to **select the data folder** you want to your own folder, like this figure. Then **Click "EXPORT"**
    <img src=/images/export.png width=500 height=300>


2. **Label your Data** 
    + Check if the data is exported to your selected folder correctly. The generated folder should contain csv data files. 
    + Open MarkerParser.exe and Click "Select input File" to select the CSV file. 
    Note: the *Config Time* is just the time indicating when you label your data. It doesn't matter a lot.
    <img src=/images/marker-1.png width=600 height=300>

    + Click "Read Data"
    + **Make sure you close the CSV data file you input before you use MarkerParser.exe** to label data. 
    Otherwise, you will see this error:
    <img src=/images/marker-2.png width=300 height=300>

    + Add some labels about your meal like this figure and give some information about when you take this meal, what meal you take, and so on, and then Click "Write Events"
    <img src=/images/marker-3.png width=600 height=300>

    + Check the generated txt file in the directory shown in the bar "Output File"

    + Change the file name "Shimmer-Data.txt" to "Shimmer-Data.shm" so that we can use EatMon.exe to load and visualize it.

3. **Data Visualization**
    + Install EatMon.exe and download its dependencies. **Put all files into the same folder**
    + After you change the file name to .shm file, open your Eatmon.exe
    + Click "file" -> "Load file" to load your .shm file
    + Zoom in the data by pressing "+" button, since when not zooming in your data, you may be unable to see your data.
    + You can also select which data you want to view by  selecting items in "View" tab.
    Here I just show the raw data I collected
    <img src=/images/EatMon-1.png width=500 height=300>

    + For more operations about using this software, Click "Help"
    
## Explore more Information
Since this is just a Quick Tutorial about using tools to collect data, there are some details not mentioned.
+ For more information about Using Shimmer and Consensys, Read this [document](/doc/Shimmer_User_Manual_rev3p.pdf) or this [tutorial](/doc/debrief.docx)
+ For documents about other softwares, Read [this](http://cecas.clemson.edu/tracking/ShimmerData/Programs/)
