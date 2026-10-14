<h1 align="center">Wildfire Detection System 🔥</h1>

<div align="center">

[![Python](https://img.shields.io/badge/Python-3.10.13-blue.svg?logo=python)](https://www.python.org/downloads/release/python-31013/)
[![Flask](https://img.shields.io/badge/Flask-3.0.3-lightgrey.svg?logo=flask)](https://flask.palletsprojects.com/en/3.0.x/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.16.1-orange.svg?logo=tensorflow)](https://www.tensorflow.org/)
[![License](https://img.shields.io/badge/License-Apache%202.0-green.svg)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Active-brightgreen.svg)](https://github.com/username/repo)

**Built by Touseef Ur Rehman**
</div>

## Demo 🎥

https://github.com/user-attachments/assets/7fb2bc93-6a12-4339-9da1-d7dd11948fdb

---

## Table of Contents 📚

1. [Background on Wildfires 🌍](#background-on-wildfires-)
2. [Project Overview 🚀](#project-overview-)
3. [Features 🌟](#features-)
4. [Demo 🎥](#demo-)
5. [Screenshot 📸](#screenshot-)
6. [Installation 🛠️](#installation-%EF%B8%8F)
7. [Usage 💻](#usage-)
8. [File Structure 📁](#file-structure-)
9. [Requirements 📦](#requirements-)
10. [Improvements ✨](#improvements-)
11. [Contributing 🤝](#contributing-)
12. [License 📜](#license-)

---

## Background on Wildfires 🌍

Wildfires are one of the most destructive forces on the planet, causing widespread environmental damage and economic loss. Their frequency and severity continue to rise, driven largely by climate change.

### Key Facts

- **Global Impact**: Wildfires devastate regions across the globe. In 2020, California alone saw over 4.2 million acres burned — a record-breaking figure [(Cal Fire)](https://www.fire.ca.gov/incidents/2020/).
- **Frequency**: More than 100,000 wildfires occur every year in the U.S. [(National Geographic)](https://www.nationalgeographic.com/environment/article/wildfires).
- **Economic Cost**: Annual wildfire damage in the U.S. is estimated at $5 billion [(Insurance Information Institute)](https://www.iii.org/fact-statistic/facts-statistics-wildfires).
- **Climate Change**: Rising temperatures and increasingly dry conditions are directly amplifying wildfire risk and intensity [(NASA)](https://climate.nasa.gov/news/2878/the-link-between-climate-change-and-wildfires/).

These numbers make a strong case for smarter, faster detection. This project was built to address exactly that — using modern deep learning to catch wildfires early.

---

## Project Overview 🚀

I built this system to combine three data sources — satellite imagery, camera feeds, and live weather data — into a single wildfire detection and alerting platform. The backend runs on Flask, and the models are trained using TensorFlow with a ResNet50v2 architecture.

The system includes three models:

- **Satellite CNN** — Detects wildfire probability from satellite images. Accuracy: **97%**.
- **Camera/Image CNN** — Identifies active fire in uploaded photos or drone footage. Accuracy: **98%**.
- **Weather Risk Model** — Predicts wildfire likelihood from meteorological inputs. Accuracy: **100%** *(note: trained on a small dataset)*.

---

## Features 🌟

- **Satellite Detection** — Analyze high-resolution satellite imagery for fire hotspots.
- **Camera Detection** — Upload images from cameras or drones for real-time fire identification.
- **Weather Prediction** — Assess wildfire risk using current meteorological conditions.
- **Email Alerts** — Get hourly email notifications for wildfire risk in any location you specify.

---

## Installation 🛠️

### 1. Clone the repository

```bash
git clone https://github.com/ZephyrusBlaze/Wildfire-Detection
cd Wildfire-Detection
```

### 2. Create and activate a virtual environment

```bash
python -m venv venv

# Windows
venv\Scripts\activate

# macOS/Linux
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Train and save the models

The camera and satellite detection models need to be trained on Kaggle before you can run the app locally:

- Open `analysis/notebooks/wildfire-camera-detection.ipynb` in a Kaggle Notebook, run all cells, and download the saved `.keras` model file.
- Do the same for `analysis/notebooks/wildfire-satellite-detection.ipynb`.
- Place both `.keras` files inside the `analysis/models/` directory.

### 5. Set up environment variables

Create a `.env` file in the project root with the following keys:

```env
MAPBOX_TOKEN=your_mapbox_token
MAILERSEND_KEY=your_mailersend_key
```

### 6. Initialize the database

```bash
python -c "from src.app import init_db; init_db()"
```

### 7. Run the application

```bash
python src/app.py
```

The app will be available at `http://127.0.0.1:5000`.

---

## Usage 💻

Once the app is running, open your browser and go to `http://127.0.0.1:5000`. Here's what each page does:

| Page | Description |
|---|---|
| **Home** | Overview and system introduction |
| **Camera Detection** | Upload an image to check for fire |
| **Satellite Detection** | Analyze satellite data for wildfire hotspots |
| **Alert Service** | Subscribe for location-based wildfire email alerts |

---

## File Structure 📁

```
.
├── .env.example                        # Environment variable template (copy to .env)
├── .gitignore
├── CONTRIBUTING.md
├── LICENSE
├── README.md
├── requirements.txt
│
├── analysis/
│   ├── data/
│   │   └── forestfire-classification.csv      # Training dataset for weather model
│   ├── models/
│   │   ├── meteorological-detection-classification.keras
│   │   ├── std_scaler_weather.pkl
│   │   ├── wildfire_camera_detection_model.keras     # Generate via Kaggle
│   │   └── wildfire_satellite_detection_model.keras  # Generate via Kaggle
│   └── notebooks/
│       ├── meteorological-detection-classification.ipynb
│       ├── wildfire-camera-detection.ipynb
│       └── wildfire-satellite-detection.ipynb
│
└── src/
    ├── app.py                          # Flask application entry point
    ├── camera_functions.py             # Camera image prediction logic
    ├── email_alert.py                  # Hourly email alert scheduler
    ├── meteorological_functions.py     # Weather data prediction logic
    ├── satellite_functions.py          # Satellite image prediction logic
    ├── static/
    │   ├── images/
    │   │   └── Screenshot.png
    │   └── js/
    │       ├── alert_map.js            # Alert page map
    │       ├── camera.js               # Camera detection page
    │       └── map.js                  # Satellite detection map
    └── templates/
        ├── base.html
        ├── home.html
        ├── detect_camera.html
        ├── detect_satellite.html
        └── alert.html
```

---

## Requirements 📦

| Package | Version |
|---|---|
| Python | 3.10.13 |
| Flask | 3.0.3 |
| TensorFlow | 2.16.1 |
| Pandas | 2.2.2 |
| Scikit-Learn | 1.5.0 |
| Mailersend | 0.5.6 |
| OpenMeteo SDK | 1.11.7 |

Full dependency list: [requirements.txt](requirements.txt)

---

## Improvements ✨

A few areas I'd like to improve in future iterations:

- **Larger, more diverse datasets** — The weather model especially would benefit from more training data across different regions and climates.
- **Real-time processing** — Streaming satellite and camera feeds instead of static uploads would make the system much more responsive.
- **Better model generalization** — Training on data from more geographies would make satellite and camera detection globally applicable.
- **UI/UX polish** — The interface works but there's room to make it cleaner and more intuitive.
- **Advanced architectures** — Experimenting with vision transformers or ensemble models could push accuracy even higher.

---

## Contributing 🤝

Contributions are welcome. To get started:

1. Fork the repository.
2. Create a branch: `git checkout -b feature/your-feature`.
3. Commit your changes: `git commit -m 'Add your feature'`.
4. Push: `git push origin feature/your-feature`.
5. Open a Pull Request using the [PR template](.github/PULL_REQUEST_TEMPLATE.md).

For bugs or feature requests, use the [issue templates](.github/ISSUE_TEMPLATE/bug_report.md).

---

## License 📜

Licensed under the Apache 2.0 License. See [LICENSE](LICENSE) for details.
