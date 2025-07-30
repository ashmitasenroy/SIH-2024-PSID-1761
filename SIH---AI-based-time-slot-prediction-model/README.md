# 📦 Intelligent Postal Delivery Route Optimization System

A **Smart India Hackathon 2024** project that simulates and optimizes postal delivery routes across Kolkata using real-world parameters like traffic, region-wise behavior, delivery success/failure, and geographic distance. The project combines:

- 🔁 Python-based delivery simulation
- 📍 OpenStreetMap-based geospatial inputs
- 🧠 Route optimization using Google OR-Tools
- 🌐 A Node.js API server for frontend/backend integration

---

## 📁 Project Structure

```

sih/
├── fake\_data.py           # Generates realistic delivery data using SimPy + Faker
├── optimize\_route.py      # Route optimizer using Google OR-Tools + OpenStreetMap coordinates
├── server.js              # Node.js backend that serves optimized routes
├── delivery\_data.csv      # Simulated dataset (generated)
├── public/                # Static frontend (optional)
├── requirements.txt       # Python dependencies
└── README.md              # Project documentation


## 🎯 Problem Statement

Simulate real-world delivery activity across urban regions and compute optimized postal delivery routes. This solution integrates:

- Geospatial intelligence using **OpenStreetMap coordinates**
- Distance calculation using Haversine (great-circle) formula
- Delivery failure simulation and retry patterns
- Time-based traffic modeling
- Region-specific routing

---

## 🧪 1. Simulated Dataset Generation

### `fake_data.py`

This Python script generates 180 days of simulated delivery data in Kolkata using:

- **SimPy** for discrete-event delivery simulation
- **Faker** for customer names
- Kolkata-based **PIN codes** and postal zone distances
- **Traffic pattern modeling** by time of day

### Sample Features:

- `Region`: Central, North, East, etc.
- `Time Slot`: Randomized 1-hour delivery windows
- `Traffic Pattern`: Peak, Heavy, Moderate, Light
- `Success Indicator`: Realistic delivery failure chance
- `User Rating`: Based on delivery outcome

### Run:

```bash
python fake_data.py
````

📁 Output: `delivery_data.csv`

#### Example Output:

| Timestamp        | UserID    | Customer Name | Area Pincode | Distance | Time Slot   | Traffic | Region | Success | Rating |
| ---------------- | --------- | ------------- | ------------ | -------- | ----------- | ------- | ------ | ------- | ------ |
| 2024-04-01 09:00 | UID000012 | Ravi Verma    | 700017       | 6.0      | 09:00–10:00 | Peak    | East   | 1       | 5      |

---

## 🧭 2. Route Optimization

### `optimize_route.py`

This script accepts **OpenStreetMap-style GPS coordinates** and finds the shortest possible delivery path using **Google OR-Tools**.

#### How it works:

* Takes a list of `[lat, lon]` waypoints (from OpenStreetMap or any map API)
* Uses `geopy.distance.great_circle` to build the distance matrix
* Solves the Traveling Salesman Problem (TSP) using `ortools.constraint_solver`

### Example Input (waypoints from OpenStreetMap):

```bash
python optimize_route.py "[[22.5726, 88.3639], [22.5853, 88.4028], [22.5769, 88.3741]]"
```

### Example Output:

```json
{
  "routes": [[0, 2, 1, 0]]
}
```

This means: Start → Point 2 → Point 1 → Return to start

---

## 🌐 3. API Backend (Node.js + Python)

### `server.js`

A lightweight **Express** server that exposes an API endpoint:

```
GET /optimize-route?waypoints=[URL-encoded GPS coordinates]
```

#### Input:

* A JSON-encoded array of `[latitude, longitude]` pairs (e.g., from OpenStreetMap)

#### Example:

```http
GET http://localhost:3000/optimize-route?waypoints=[[22.57,88.36],[22.59,88.38],[22.58,88.40]]
```

#### Output:

```json
{
  "routes": [[0, 2, 1, 0]]
}
```

Internally, it runs the Python script `optimize_route.py` and returns the optimized path.

### Start the Server:

```bash
node server.js
```

Visit: `http://localhost:3000`

---

## 🗺️ Why OpenStreetMap?

* Our route optimizer accepts **OpenStreetMap-style latitude-longitude coordinates**
* This allows easy integration with **Leaflet**, **Mapbox**, or **Overpass API**
* You can extract real coordinates from OpenStreetMap manually or programmatically for simulation or live demos

---

## 📦 Installation

### Python Dependencies:

```bash
pip install -r requirements.txt
```

`requirements.txt`:

```
simpy
faker
pandas
numpy
geopy
ortools
```

### Node.js Dependencies:

```bash
npm install express node-fetch
```

---

## 🧠 Realism in Simulation

| Feature                  | Description                      |
| ------------------------ | -------------------------------- |
| 📍 PIN-based location    | Based on real Kolkata pincodes   |
| 🚦 Traffic patterns      | Adjusted by delivery time        |
| 📉 Success/Failure logic | Retry if failed, affects rating  |
| 🗂️ Ratings              | User feedback depends on outcome |
| 🗺️ Coordinates          | From OpenStreetMap-style lat/lon |

---

## 📌 Future Work

* Visualize route using **Leaflet.js** + OpenStreetMap tiles
* Predict failure using ML models
* Add weather, holidays as features
* Build full-stack dashboard with delivery analytics

---

## 👩‍💻 Author

**Anisha Singh**
🔗 [GitHub](https://github.com/anisha-singh-2004)
🎓 SIH 2024 Participant(Team-The Ensembles)

---

## 📜 License

This project is licensed under the MIT License.


