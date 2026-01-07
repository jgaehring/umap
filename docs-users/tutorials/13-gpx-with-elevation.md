!!! abstract "What We'll Learn"

    - Create a map from a GPX file
    - Add an altitude curve in popup


## 1. Create a map from a GPX file

Simply drag and drop a GPX file to the map for a layer to be automatically created from that data.

![Capture the window of a browser on which a GPX](../static/tutoriels/gpx-import-drag-and-drop.png)

A line should then appear on the map and potentially pre-defined points according to the source file:

![Capture the browser window with the map with a plot](../static/tutoriels/gpx-import-result.png)


## 2. Add an altitude curve

Right-click **on the line** and choose the editing pencil.

Open the `Interaction Options` and move the `Popup Shape` to `Great` to have the place to view the graph.
Then change the `Present popup Template` from `By default` to `Route`.

You should see the popup in the background get rich from an altitude graph:

![Capture a browser window with the map, control panel and popup](../static/tutoriels/gpx-configuration-popup.png)

You will notice that by scanning the graph, the current position is made visible on the map (orange point on the line) and its altitude is dynamically updated in the popup:

![Capture a browser window with the map and altitude curve](../static/tutoriels/gpx-elevation-graph.png)

*Good walk!*
