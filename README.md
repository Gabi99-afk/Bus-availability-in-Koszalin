# Walking Time Analysis to Bus Stops and Interactive Map Visualization

This project analyzes walking times from various locations (represented as nodes in a street network) to the nearest bus stops and visualizes the results on interactive maps. It uses OpenStreetMap data for street networks, Google Sheets for bus stop information, and Folium for map visualization.

## Project Overview

The core objective is to determine how long it takes to walk from any point within a given area to the closest bus stop, considering both the walking distance and the minimum waiting time at the bus stop. This analysis helps in understanding the accessibility of bus stops and can be useful for urban planning, real estate analysis, and public transportation studies.

## Key Steps

1.  **Data Acquisition:**
    * **Bus Stop Data:** Bus stop locations (latitude and longitude) and minimum waiting times are loaded from a Google Sheet.
    * **Street Network Data:** The street network for a specified area (e.g., Koszalin, Poland) is retrieved from OpenStreetMap using the `osmnx` library.
2.  **Nearest Node Calculation:**
    * For each bus stop, the nearest node (intersection or point in the street network) is identified using `osmnx`.
    * The great-circle distance between the bus stop and its nearest node is calculated.
3.  **Walking Time Calculation:**
    * For each node in the street network, the shortest walking distance to the nearest bus stop's nearest node is calculated using `networkx`.
    * Walking time is estimated based on a standard walking speed (1.4 m/s).
4.  **Total Time Calculation:**
    * The total time to reach a bus stop is calculated by adding the walking time to the minimum waiting time at the bus stop (obtained from the Google Sheet).
5.  **Data Visualization:**
    * Histograms are generated to visualize the distribution of walking times and total times.
    * Interactive maps are created using `folium` to display:
        * Bus stop locations.
        * Bus stop locations with circles colored by total time.
        * Network nodes colored by walking time to the nearest bus stop.
        * Network nodes colored by total time to the nearest bus stop.

## Libraries and Dependencies

-   `osmnx`: Retrieves and works with OpenStreetMap street network data.
-   `geopandas`: Handles geospatial data.
-   `networkx`: Performs network analysis, including shortest path calculations.
-   `pandas`: Manages and analyzes data.
-   `folium`: Creates interactive maps.
-   `branca`: Generates color maps for visualization.
-   `gspread`: Interacts with Google Sheets.
-   `google-auth`: Handles Google Sheets authentication.
-   `matplotlib`: Plots histograms.

## Setup and Usage

1.  **Google Sheets Setup:**
    * Create a Google Sheet with columns for bus stop latitude, longitude, and minimum waiting time (`min/stop_int`).
    * Share the sheet with the Google Cloud service account used for authentication.
    * Replace the `spreadsheet_url` in the script with your sheet's URL.
2.  **Google Cloud Authentication:**
    * Ensure you have a Google Cloud project with the Google Sheets API enabled.
    * Authenticate your environment (Colab or local) using Google Cloud credentials.
3.  **Run the Script:**
    * Execute the Python script.
4.  **View Results:**
    * The script generates HTML files (`bus_stop_map.html`, `bus_stop_circle_map.html`, `walking_time_map.html`, `total_time_map.html`) that can be opened in a web browser to view the interactive maps.
    * Histograms will be displayed showing the distribution of the travel times.

## Outputs

-   `bus_stop_map.html`: Shows the location of each bus stop.
-   `bus_stop_circle_map.html`: Displays bus stops with colored circles representing the total time (walking + waiting).
-   `walking_time_map.html`: Shows the walking time from each node to the nearest bus stop using a color gradient.
-   `total_time_map.html`: Shows the total time from each node to the nearest bus stop using a color gradient.
-   Histograms: Visual representations of walking time and total time distributions.

## Key Explanations

-   **Nodes:** In the context of this project, nodes represent intersections or points along the street network. They are used as starting points for calculating walking times.
-   **Great-Circle Distance:** This is the shortest distance between two points on the surface of a sphere, used to approximate distances on the Earth's surface.
-   **Shortest Path:** The shortest walking route between two nodes in the street network, calculated using `networkx`.
-   **Color Gradient:** Used in the maps to represent different walking or total times, making it easy to visualize areas with high or low accessibility.

This project provides a comprehensive analysis of walking times to bus stops, aiding in better understanding and improving public transportation accessibility.
