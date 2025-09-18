# Plant IQ 🌱➡️🤖

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python Version](https://img.shields.io/badge/python-3.8%2B-blue)](https://www.python.org/)
[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/your-username/plant-iq/issues)

**Don't just grow plants, understand them.** Plant IQ is an open-source, end-to-end system that uses IoT sensors and machine learning to monitor plant health, diagnose issues, and provide actionable care advice to keep your plants thriving.

---

## ✨ Features

*   **🤖 AI-Powered Health Scans:** Upload a photo of your plant's leaves. Our deep learning model detects common diseases (e.g., Early Blight, Leaf Spot) and pest damage.
*   **📊 Real-Time Environmental Monitoring:** Get live data on crucial plant metrics from our custom sensor node:
    *   Soil Moisture
    *   Ambient Temperature & Humidity
    *   Light Intensity
*   **💧 Smart Watering Alerts:** Receive notifications only when your plant's soil moisture drops below its unique threshold. No more overwatering or underwatering.
*   **🌿 Extensive Plant Database:** Access care guides and ideal condition parameters for a wide variety of houseplants and garden plants.
*   **📱 Responsive Web Dashboard:** View all your plant's data, history, and AI analysis in a clean, modern web interface.
*   **🔧 Open & Hackable:** Everything is open-source. Extend the hardware, retrain the model on new diseases, or build your own client.

---

## 🛠️ How It Works

Plant IQ is built from several interconnected components:

1.  **Hardware Sensor Node:** An ESP32/Arduino-based device with a suite of sensors (capacitive soil moisture, DHT22, LDR) collects data and sends it to the server via WiFi/MQTT.
2.  **Backend API (This Repo):** A Python FastAPI server that:
    *   Receives and stores sensor data.
    *   Hosts the machine learning model for image classification.
    *   Manages user data, plants, and notification rules.
    *   Provides a RESTful API for all operations.
3.  **Machine Learning Model:** A convolutional neural network (CNN) built with TensorFlow/Keras, trained on thousands of images of healthy and diseased plants from the [PlantVillage dataset](https://plantvillage.psu.edu/).
4.  **Web Frontend:** A React.js dashboard that allows users to visualize their data, submit plant images for analysis, and configure their settings.

```mermaid
graph TD
    A[Sensor Node] -- MQTT/HTTP --> B[Backend API];
    C[Web App] -- HTTP Requests --> B;
    D[User Uploads Image] --> B;
    B -- Query --> E[ML Model];
    E -- Prediction --> B;
    B -- Sends Alert --> F[User];
    B -- Stores Data --> G[(Database)];
