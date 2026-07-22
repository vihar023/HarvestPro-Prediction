<img width="1408" height="550" alt="Image" src="https://github.com/user-attachments/assets/3e3b3ad0-cef3-4909-bd04-d2bc4bdbb644" />

# 🌱 HarvestPro

HarvestPro is a Machine Learning-based crop recommendation system that helps farmers select the most suitable crops based on current weather conditions and geographical location. The application analyzes temperature, humidity, rainfall, and location data to provide intelligent crop predictions through a Flask REST API.

## Table of Contents

- [Project Description](#project-description)
- [Setup](#setup)
- [Running the Application](#running-the-application)
- [API Endpoints](#api-endpoints)
  - [POST /api/predict](#post-apipredict)
  - [POST /api/forecast](#post-apiforecast)


## Project Description

HarvestPro is an intelligent agricultural decision-support system that uses Machine Learning and weather analytics to recommend suitable crops for specific locations. The system evaluates important environmental factors such as temperature, humidity, rainfall, latitude, and longitude to identify optimal crop choices based on current climate conditions.

The application integrates a trained Machine Learning model with a Flask REST API, allowing users to submit location coordinates and receive crop recommendations along with weather insights. The backend logic is implemented in `app.py`, which manages API routes, processes incoming requests, retrieves weather information, and generates predictions using the trained model.

The project follows an end-to-end Machine Learning workflow, including data collection, data preprocessing, exploratory data analysis, feature engineering, model training, algorithm comparison, model evaluation, and deployment. By combining Machine Learning, weather data analysis, and API development, HarvestPro provides a scalable smart farming solution that supports data-driven crop planning and climate-aware agricultural decisions.



## Setup

Follow these steps to set up the project locally.

1. **Clone the repository**

   ```bash
   git clone <repository-url>
   cd HarvestPro
   ```

2. **Create a virtual environment**

   ```bash
   python3 -m venv env
   ```

3. **Activate the virtual environment**

   - On macOS/Linux:
     ```bash
     source env/bin/activate
     ```
   - On Windows:
     ```bash
     env\Scripts\activate
     ```

4. **Install the required dependencies**

   ```bash
   pip install -r requirements.txt
   ```

## Running the Application

Once dependencies are installed, start the Flask application with:

```bash
python3 app.py
```

By default, the app will be available at `http://localhost:5000` (or whichever host/port is configured in `app.py`).

## API Endpoints

### POST `/api/predict`

Returns predicted crops best suited to the current weather conditions at the given coordinates.

**Request payload**

```json
{
    "latitude": 19.0728,
    "longitude": 72.8826
}
```

**Response**

```json
{
    "conditions": {
        "humidity": 63.809895833333336,
        "rainfall": 0.0,
        "temperature": 28.35866275926431
    },
    "predicted_crops": [
        "muskmelon (53.00%)",
        "mothbeans (24.00%)",
        "lentil (21.00%)"
    ]
}
```

| Field | Type | Description |
|---|---|---|
| `conditions.humidity` | float | Relative humidity (%) at the given location |
| `conditions.rainfall` | float | Rainfall (mm) at the given location |
| `conditions.temperature` | float | Temperature (°C) at the given location |
| `predicted_crops` | array of strings | Recommended crops with confidence percentage, ordered by suitability |

### POST `/api/forecast`

Returns the raw weather forecast data for the given coordinates.

**Request payload**

```json
{
    "latitude": 19.0728,
    "longitude": 72.8826
}
```

**Response**

```json
{
    "response": {
        "humidity": 63.809895833333336,
        "rainfall": 0.0,
        "temperature": 28.35866275926431,
        "weather_data": []
    }
}
```

| Field | Type | Description |
|---|---|---|
| `response.humidity` | float | Relative humidity (%) at the given location |
| `response.rainfall` | float | Rainfall (mm) at the given location |
| `response.temperature` | float | Temperature (°C) at the given location |
| `response.weather_data` | array | Additional raw weather data points, if available |

