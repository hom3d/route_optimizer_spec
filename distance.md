# Distance matrix

# Objective

The primary goal of Stage 1 is to establish a solid foundation for solving the routing problem. This involves:

* Preparing input data by reading delivery points from a file.
* Implementing basic distance calculations to compute the distance between delivery points.
* Generating a distance matrix for use in later optimization stages.
* Providing a simple command-line interface (CLI) to interact with the tool.

# Features to Implement

* Input Data Handling
    * Read delivery point data from a structured file (e.g., CSV format).
    * Validate input data to ensure completeness and correctness (e.g., no missing coordinates).
* Distance Calculation Methods
    * Implement two basic distance calculation methods:
        * Euclidean Distance: For straight-line approximations.
        * Haversine Formula: For more accurate geographic distances using latitude and longitude.
    * Provide a mechanism to choose the desired distance method.
* Distance Matrix Generation
    * Compute pairwise distances between all delivery points using the selected method.
    * Store the results in a 2D matrix (distance matrix) for further use.
* Command-Line Interface (CLI)
    * A simple CLI for:
        * Loading the delivery points file.
        * Selecting the distance calculation method.
        * Displaying the generated distance matrix.

# Tools and Libraries

* Core Libraries:
    * csv: For reading delivery point data from CSV files.
    * math: For mathematical operations (used in distance calculations).
* Geographic Distance Calculation:
    * geopy: For implementing the Haversine formula to calculate distances between GPS coordinates.
* Data Validation and Matrix representation:
    * pandas (optional): For efficient handling and validation of tabular data.
    * numpy: For creating and manipulating the distance matrix efficiently.

# Approaches to Use

* Input Data Handling
    * File Format:
        * Use a CSV file with the following columns:
        * ID: A unique identifier for each delivery point.
        * Latitude: Latitude in decimal degrees.
        * Longitude: Longitude in decimal degrees.
    * Validation:
        * Check for missing or invalid entries (e.g., non-numeric coordinates).
        * Ensure no duplicate delivery points.
* Distance Calculations:
    * Euclidean Distance: Treat latitude and longitude as Cartesian coordinates for simplicity.
      Use the Pythagorean theorem to calculate the straight-line distance.
    * Haversine Formula: Use the Earth’s curvature to compute the great-circle distance.
      Convert latitude and longitude from degrees to radians before applying the formula.
* Distance Matrix Generation
    * Represent delivery points as a list or DataFrame.
    * Compute pairwise distances for all points.
    * Store results in a square matrix where:
        * Row i and column j represent the distance from point i to point j.
* Command-Line Interface
    * Use Python’s built-in input() function to collect user input.
    * Provide prompts to:
        * Load a delivery points file.
        * Select the desired distance calculation method.
        * Display the generated distance matrix in the console.

# Deliverables

* Python Script:
    * A script capable of:
        * Reading a CSV file with delivery point data.
        * Computing distances using Euclidean or Haversine methods.
        * Generating and displaying a distance matrix.
* Sample Input File:
    * Example delivery points file (delivery_points.csv) for testing.
* Documentation:
    * Instructions for running the script.
    * Description of the input file format and expected outputs.

# Usage

```
Welcome to OpenRouteOptimizer (Stage 1)
Enter the name of the delivery points file (e.g., delivery_points.csv): delivery_points.csv
Select distance method (euclidean/haversine): haversine

Distance Matrix:
[0, 252.23, 279.35]
[252.23, 0, 334.80]
[279.35, 334.80, 0]
```

# Test inputs

## Basic example

This example includes three delivery points with unique IDs and valid geographic coordinates.
File Name: `delivery_points_basic.csv`

```
ID,Latitude,Longitude
1,52.2297,21.0122
2,50.0647,19.9450
3,52.4064,16.9252
```

## Example with Larger Dataset

```
ID,Latitude,Longitude
1,40.7128,-74.0060
2,34.0522,-118.2437
3,41.8781,-87.6298
4,29.7604,-95.3698
5,39.7392,-104.9903
```

## Example with Missing and Invalid Data

This example includes an invalid latitude, missing longitude, and missing rows to test error handling.

```
ID,Latitude,Longitude
1,52.2297,21.0122
2,50.0647,        # Missing Longitude
3,,19.9450        # Missing Latitude
4,abc,16.9252     # Invalid Latitude
5,52.4064,16.9252
```