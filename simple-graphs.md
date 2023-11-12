# HF24 Data Tutorial

## Preparation
Visit these two URLs [Goodwood](https://hf24exampledata.blob.core.windows.net/artefacts/eChook-GoodwoodFinal23-Race2.csv?sp=r&st=2023-11-12T00:00:00Z&se=2024-03-31T22:59:59Z&spr=https&sv=2022-11-02&sr=b&sig=5DYDVpJet6o8fif1kfWPuJIhtEbCg3KxQ7X9YBzaJo4%3D) and [Ford Dunton](https://hf24exampledata.blob.core.windows.net/artefacts/eChook-FordDunton23-Race1.csv?sp=r&st=2023-11-12T00:00:00Z&se=2024-03-31T22:59:59Z&spr=https&sv=2022-11-02&sr=b&sig=nx0mI9y7qSoDh6S3mBEMhS67OZZX5zQXqVTe1PREK1s%3D) and download the two files which have been collected by the eChook device on the HF24 car.  The files should go into the Downloads folder for your web browser.

_Note that the data in these files has undergone some pre-processing to calculate a regular date/time, create speed in miles per hour and to assign driver names to phases in the race._

_The links above will work until the end of March 2024.  All race data we've collected is stored in the HF24 Google Drive._

## Simplistic Charts
- Visit `www.csvplot.com` in your browser.  This is a free online tool which allows someone to upload some data and turn it into a graph.  We will use it to visualise some of the HF24 car data in the first part of the tutorial
- Click on the `Load CSV File` button.

![CSV Plot Homepage](images/CsvPlot-HomePage.PNG)
- The data that the eChook collects is formatted in CSV - Comma-separated values.  This is a simple, concise and common format for representing data, it works especially well with largely numerical data.
- Using the file selector, select the Goodwood file first.

![Choose File](images/CsvPlot-PickFile.PNG)
- Give the web page a few seconds to process the data.
- When it first renders the chart, it will plot Longitude against Latitude and colour code the **series** against each driver.  You'll notice (if you've ever seen it) that it looks exactly like a circuit diagram of Goodwood circuit - this is because it is plotting the GPS co-ordinates of where the car went and the car obviously went round the track!

![Default Chart](images/CsvPlot-DefaultGraph.PNG)
- We're going to plot some more useful information.  On the left hand side there are a list of all the **parameters** that were measured by the eChook at multiple times per second.
- We want to create what is called a **Time-Series** graph.  This shows how a parameter changes over time. 
- Find the `ISODateTime` parameter and drag it from the left of the screen to drop on top of the Longitude axis (or the X-axis).

![Drag to X axis](images/CsvPlot-DragTimeToX.PNG)
- Similarly, find the `Speed (mph)` parameter and drag that from the left of the screen and drop on top of the Latitude axis (or Y-axis).

![Drag to Y axis](images/CsvPlot-DragSpeedToY.PNG)
- The graph has now changed showing times on the X-axis and speed in miles per hour on the Y-axis. Using this web site, it starts off in the form of a scatter plot.  However we want a line graph - a continued line showing how the speed changes over time.
- To change it to the line graph we want we need to do the following:
   - At the top right of the graph window, click on the Line Graph icon to change it from scatter to line.

   ![Line Graph Icon](images/CsvPlot-ChangeToLine.PNG)
- We now have a time-series graph which shows how the speed varied over time.  
   - You can see the pit changes where the speed drops down to zero.
   - You can see what each driver was doing in terms of their speed.

![Time Series Chart](images/CsvPlot-TimeVsSpeed.PNG)
- Have a go at looking at another parameter to plot against time.  Meaningful ones to try would be:
   - Amp Hours
   - Amps
   - Aux Volts
   - Distance
   - Input Throttle
   - Speed (m/s)
   - Speed GPS
   - Temp 2
   - Volts

## Analysing the data 
Looking at the whole race which is 90 or so minutes of measurements (multiple times per second) gives a high level view of what happened and allows us to see trends.  For example you can see roughly when the speed drops off, so in turn you can work out the time that the car was able to sustain its highest speeds.

Sometimes you want to go into more detail with the data, for example how long did each changeover take.  At the moment you can't really see this detail because it is so small on the graph (i.e. it was a few seconds within 90 minutes of activity).

To see things in better detail, you can zoom into the data which would redraw the graph but with a much smaller timeframe.  To do this, use the mouse to draw a square around the first changeover point where the speed drops off from _Driver 1_.

![Zoom In](images/CsvPlot-ZoomBySelection.PNG)

Now the changeover is much more visible showing where the Speed is 0.  

![Zoomed In](images/CsvPlot-ZoomChangeover1.PNG)
If we want to zoom a bit more, we can draw another square or use the + or - icons at the top right of the screen.

![Zoom In Or Out](images/CsvPlot-ZoomInAndOut.PNG)

Now it should be possible to hover on over the graph and work out how long the first changeover took.

To get it back to the full screen view, press the last icon in the top right that looks like a house.

![Reset Zoom](images/CsvPlot-ResetZoom.PNG)

You can now play around and work out things like:
- What was the fastest speed clocked in the race and when did it happen?  Which driver?
- How long were the changeovers?
- Which drivers might be taking the best line around the track?

## Comparing Races
Open up another browser tab and revisit `www.csvplot.com`.  This time repeat the steps above and pick the Ford Dunton file.

Repeat the steps to produce a Time-Series graph showing time against speed in miles per hour. 

Now you can compare the two graphs by flicking between tabs and see the differences in the way the car was raced.

## Summary
The graph tool at `www.csvplot.com` is a simple, quick and easy way to see the data in graph form.  However to really analyse the data in detail we need a better capability.  

One scenario that can't be supported in this tool is to compare more than one parameter across time - for example battery volts and speed against time.  We would want to work out for example whether the battery volts (or amps) dropping to a certain level instigates a significant drop in speed.

The detailed graph tutorial uses a more advanced tool which will allow us to do this kind of analysis.