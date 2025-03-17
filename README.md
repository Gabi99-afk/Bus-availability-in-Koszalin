# Bus-availability-in-Koszalin
# Bus Stop Accessibility Analysis in Koszalin, Poland

This project analyzes the accessibility of bus stops in Koszalin, Poland, by calculating walking times from various locations to the nearest bus stops. It utilizes OpenStreetMap data, Google Sheets, and Python libraries such as `osmnx`, `networkx`, `pandas`, `geopandas`, and `folium`. This project was inspired by the work described in **Spatial Analysis of Public Transport Infrastructure** by **Felix Doppelbauer** (8 min read), available at [https://doppelfelix.medium.com/spatial-analysis-of-public-transport-infrastructure-8f0972fb8f11](https://doppelfelix.medium.com/spatial-analysis-of-public-transport-infrastructure-8f0972fb8f11).

## Project Overview

The project performs the following steps:

1.  **Data Acquisition:**
    * Imports bus stop location data and minimum stop times from a Google Sheet.
    * Downloads a walkable street network graph of Koszalin from OpenStreetMap.
2.  **Data Processing:**
    * Calculates the nearest street network node for each bus stop.
    * Calculates the great-circle distance between each bus stop and its nearest node.
    * Calculates the shortest walking distance and time from each node in the street network to the nearest bus stop.
    * Combines the walking time with the minimal stop time from the google sheet.
3.  **Data Visualization:**
    * Generates histograms of walking times and total times.
    * Creates interactive maps using `folium` to visualize bus stop locations and accessibility.
    * Creates a map that colors the nodes based on walking time to the closest bus stop.
    * Creates a map that colors the nodes based on total time to the closest bus stop (walking time + minimal stop time).

## Requirements

* Python 3.x
* Libraries:
    * `osmnx`
    * `networkx`
    * `pandas`
    * `geopandas`
    * `matplotlib`
    * `folium`
    * `branca`
    * `google-auth-oauthlib`
    * `gspread`
    * `google-colab`

## Installation

1.  Install the required Python libraries:

    ```bash
    pip install osmnx networkx pandas geopandas matplotlib folium branca google-auth-oauthlib gspread
    ```
2.  If you are running this code from google colab, the google colab library will be required.

## Usage

1.  Authenticate with Google Sheets using Google Colab's authentication.
2.  Ensure you have a Google Sheet with bus stop location data (latitude, longitude) and minimal stop times in the specified format.
3.  Run the Python script.
4.  The script will generate:
    * Histograms of walking times and total times.
    * Interactive HTML maps (`poi_map.html`, `poi_circle_map.html`, `walking_time_map.html`, `total_time_map.html`).

## Data Source

* Bus stop location and minimal stop time data is obtained from a CSV
"Koszalin Bus Stops"
* Street network data is obtained from OpenStreetMap using the `osmnx` library.

## Output

* Histograms showing the distribution of walking times and total times.
* Interactive maps visualizing bus stop locations and accessibility.
* HTML files containing the maps.

## Author

\Gabriel Wasilewski


