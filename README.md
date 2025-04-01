# Animal Shelter CRUD & Dashboard – CS340 Project

## Overview

This project provides a Python-based CRUD interface and a dashboard application to manage and visualize animal shelter records stored in a MongoDB database. Developed using **Jupyter Notebooks**, it includes both backend operations (via a custom CRUD module) and a frontend interface (using Dash) for **Grazioso Salvare**, a client organization seeking to identify dogs suited for rescue training.

---

## Purpose

The application is designed to:
- Enable secure and efficient management of animal shelter data.
- Support **Create, Read, Update, and Delete** operations directly in a MongoDB database.
- Offer an **interactive dashboard** for exploring and filtering animal records.
- Assist Grazioso Salvare in identifying animals for **specific rescue missions** based on traits like breed, age, and sex.

---

## Features

### ✔ CRUD Module (`animal_shelter.py`)
A class-based interface for performing CRUD operations on a MongoDB collection:
```Courier New
# Instantiate the AnimalShelter class
shelter = AnimalShelter("aacuser", "SNHU1234")

# Create
shelter.create({"name": "Milo", "age": 3, "species": "Cat"})

# Read
cats = shelter.read({"species": "Cat"})

# Update
shelter.update({"name": "Milo"}, {"age": 4})

# Delete
shelter.delete({"name": "Milo"})
```

### ✔ Interactive Dashboard (`ProjectTwoDashboard.ipynb`)
- Implemented with **Dash** and **JupyterDash**.
- Filters animals by mission type (Water Rescue, Mountain Rescue, Disaster Tracking).
- Displays results in a sortable **data table**, **geolocation map**, and **age distribution pie chart**.

---

## Technologies Used

- **Python 3**
- **MongoDB**
- **Dash & Plotly** for dashboard UI
- **Pandas** for data manipulation
- **Dash Leaflet** for map integration
- **Jupyter Notebook** for development environment

---

## Setup Instructions

### 1. Prerequisites

- Install MongoDB (follow official instructions)
- Install Python 3.x
- Install Jupyter Notebook

### 2. Install Required Packages
```bash
pip install pymongo dash jupyter-dash dash-leaflet plotly pandas matplotlib
```

### 3. Set Up Database

#### Create User
```bash
mongosh

use admin
db.createUser({
  user: "aacuser",
  pwd: "SNHU1234",
  roles: [{ role: "readWrite", db: "aac" }]
})
```

#### Import Dataset
```bash
mongoimport --username="aacuser" --password="SNHU1234" --port=31932 --host=nv-desktop-services.apporto.com \
--db aac --collection animals --authenticationDatabase admin \
--type csv --file ./aac_shelter_outcomes.csv --headerline
```

---

## Running the Dashboard

1. Open `ProjectTwoDashboard.ipynb` in Jupyter.
2. Run all cells sequentially to initialize the dashboard.
3. Use the radio buttons to filter rescue categories.
4. View interactive data table, map, and chart outputs.

---

## Testing the CRUD Module

Basic test cases are included in `test_animal_shelter.ipynb`. To validate:
- Insert, update, query, and delete a mock record.
- Check console output for operation success.

---

## Future Improvements

- Replace hardcoded credentials with environment variables.
- Add authentication to the dashboard.
- Deploy dashboard as a web app for broader access.

---

## Author

Dennis Ward II  
Southern New Hampshire University – CS340  
