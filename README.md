# RideScore DC

A comprehensive bike safety scoring system for Washington D.C. streets, implementing multiple methodologies including BNA (Bike Network Analysis), LTS (Level of Traffic Stress), and others.

## Project Overview

This project aims to create street-by-street safety scores specific to the needs of cyclists in order to help them move across the city safely.

## Project Structure

This repository is organized to facilitate parallel development of different scoring models.

RideScoreDC/
├── README.md # This file
├── requirements.txt # Core Python dependencies for the project
├── .gitignore # Files to ignore in version control
├── Products/ # Final, polished outputs for public use
│ ├── shp/ # Final shapefiles
│ └── GeoJSONs/ # Final GeoJSON files
├── Test/ # For testing code and data
└── Dev/ # Development workspaces
├── BNA/
│ └── Matt/ # Matt's BNA development space
├── LTS/
│ ├── EChO/ # Eleanor's LTS development space
│ └── Elia/ # Elia's LTS development space
├── EPJ/
│ ├── Phineas/ # Phineas's EPJ development space
│ └── Charlotte/ # Charlotte's EPJ development space
├── League of American Bicyclists/
└── Other Models/


## Scoring Models

### BNA (Bike Network Analysis)

* **Status**: Not Started
* **Methodology**: \[Description]
* **Lead**: TBD
* **Last Updated**: N/A

### LTS (Level of Traffic Stress)

* **Status**: In Progress
* **Methodology**: Furth method
* **Lead**: \[EChOdatascience]
* **Last Updated**: \[11/17/2025]
* \*\*Details

  * \[x] Repository structure setup
  * \[ ] Initial data collection from OpenStreetMap
  * \[ ] Data preprocessing
  * \[ ] LTS calculation implementation
  * \[ ] Validation analysis
  * \[ ] Visualization

### EPJ

* **Status**: Not Started
* **Methodology**: \[Description]
* **Lead**: TBD
* **Last Updated**: N/A

### League of American Bicyclist

* **Status**: In Progress
* **Methodology**:

### Other Models

* **Status**: Not Started
* **Methodology**: TBD
* **Lead**: TBD
* **Last Updated**: N/A

## Getting Started

### Prerequisites
- Python 3.8+
- Git
- VS Code (recommended) or JupyterLab

### Installation
1. Clone the repository: https://github.com/CivicTechDC/RideScoreDC.git
2. Create a virtual environment: python -m venv venv
3. Install dependencies: pip install -r requirements.txt


### Usage
Individual development work is contained within the `Dev/` subdirectories. Navigate to the model you are interested in to find the relevant notebooks and source code.

## Contributing

Please get in touch with Civic Tech DC.


