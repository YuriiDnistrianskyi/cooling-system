# Cooling System

## Overview

**Cooling System** is an automatic cooling platform designed to monitor object temperatures and dynamically control cooling devices. Although originally developed for computers and laptops, the system can be adapted for any temperature-controlled object.

The project consists of several independent components:

* **Backend Server** (FastAPI)
* **ESP8266-based Cooling Device**
* **Temperature Monitoring Script**
* **Flutter Application**

The system collects temperature measurements, stores historical data, automatically adjusts fan speed, and provides visualization through a mobile application.

---

## Architecture

<img width="827" height="583" alt="cooling-system- drawio" src="https://github.com/user-attachments/assets/b1aaa0bd-379d-488c-af91-b13a5b475598" />


---

## Components

### Backend

The backend is responsible for:

* User management
* Device management
* Object management
* Authentication and authorization
* WebSocket communication
* Cooling decision logic
* Data storage

#### Technologies

* Python
* FastAPI
* SQLAlchemy
* Alembic
* WebSocket
* PostgreSQL
* InfluxDB

---

### PostgreSQL

Stores relational data:

* Users
* Devices
* Objects
* Permissions
* Configuration

---

### InfluxDB

Stores time-series data:

* Temperature measurements
* Fan RPM measurements
* Historical telemetry

---

### ESP8266 Device

Hardware controller built on:

* ESP8266 WEMOS
* PWM Fan

Responsibilities:

* Receive commands from the backend
* Change fan speed using PWM
* Measure fan rotation speed (RPM)
* Send telemetry to the backend

#### Technologies

* C++
* PlatformIO

---

### Temperature Monitoring Script

A lightweight client application that:

* Reads CPU temperature data
* Uses LibreHardwareMonitor API
* Sends measurements to the backend via WebSocket

#### Technologies

* Python
* LibreHardwareMonitor
* WebSocket

---

### Flutter Application

Provides user interface for:

* Authentication
* Device management
* Object management
* Monitoring temperatures
* Monitoring fan speed
* Viewing historical charts

#### Technologies

* Flutter
* Dart

---

## Cooling Logic

1. Temperature monitoring script reads current temperature.
2. Temperature data is sent to the backend.
3. Backend analyzes the received value.
4. Backend determines whether fan speed should:

   * Increase
   * Decrease
   * Remain unchanged
5. Command is sent to the ESP8266 device.
6. Device adjusts PWM output.
7. Device sends RPM telemetry back to the server.
8. All measurements are stored in InfluxDB.

---

## Repository Structure

---

## Features

* Real-time temperature monitoring
* Automatic fan speed control
* Historical telemetry storage
* Device authentication
* Object authentication
* WebSocket communication
* Mobile application

---
