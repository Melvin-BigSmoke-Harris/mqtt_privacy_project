# Disaster Communication System with Privacy-Protected MQTT

## Overview

This project presents a simulation of a **privacy-focused real-time communication system** tailored for disaster response scenarios. It leverages **MQTT** as the messaging protocol to enable communication among disaster victims, drones (acting as brokers), and a central Command and Control (C2) unit.

The goal is to model message exchanges, identify potential privacy threats using the **LINDDUN framework**, and implement **Privacy Enhancing Technologies (PETs)** to secure sensitive user information.

---

## Tools and Libraries

| Tool / Library       | Description                                         |
|----------------------|-----------------------------------------------------|
| **Mosquitto**        | MQTT broker to manage message publishing/subscribing |
| **paho-mqtt**        | Python client for MQTT communications               |
| **cryptography**     | Encrypts and decrypts MQTT payloads (Fernet AES)    |
| **hashlib (SHA-256)**| Used for pseudonymizing user data and topic names   |
| **json**, `random`   | Handle data formats and simulate random messages    |

---

## Installation Instructions

### 1. Install Homebrew (macOS only)
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

##  Install Mosquitto Broker 
brew install mosquitto
brew services start mosquitto

##  Set Up Python Virtual Environment
python3 -m venv ~/mqtt_env
source ~/mqtt_env/bin/activate

## Install Required Python Packages
pip install --upgrade pip

pip install paho-mqtt cryptography

# Execution Guide

## Start Mosquitto MQTT Broker
brew services start mosquitto

## Run Basic Subscriber
source ~/mqtt_env/bin/activate
    
python3 subscriber.py

## Run Basic Publisher (New Terminal)
source ~/mqtt_env/bin/activate

python3 publisher.py

# Privacy Enhancements (PETs Applied)
The secure version of the system applies the following techniques:

Payload Encryption using AES (Fernet)

Topic Obfuscation with SHA-256 hashing

User ID Pseudonymization

Data Minimization by stripping excess metadata

## Run Secure Subscriber
source ~/mqtt_env/bin/activate
python3 secure_subscriber.py

## Run Secure Publisher (New Terminal)

source ~/mqtt_env/bin/activate
python3 secure_publisher.py

Once running, messages exchanged are encrypted, pseudonymized, and minimized for privacy.

# Results Comparison

| Metric                 | Basic Implementation | With PETs Applied     |
| ---------------------- | -------------------- | --------------------- |
| Payload encryption     | No                   | Yes (Fernet AES)      |
| User identity exposed? | Yes                  | No (hashed ID)        |
| Readable topic names?  | Yes                  | No (obfuscated)       |
| Data verbosity         | Full metadata        | Minimal fields only   |
| Privacy exposure       | High                 | Significantly reduced |


# Example Message Formats

  
Without PETS

{
  "user_id": "v_02",
  "location": "35.8044,-122.2711",
  "message": "I need a help!",
  "device_id": "Vivo"
}

with PETS 

{
  "id": "2c96c9b4d3f8...",
  "loc": "35.8044,-122.2711",
  "msg": "I need a help!"

}

# LINDDUN Threat Model

| Privacy Threat             | Mitigation Strategy                             |
| -------------------------- | ----------------------------------------------- |
| **Linkability**            | Obfuscated topics via SHA-256                   |
| **Identifiability**        | User IDs are hashed (pseudonymization)          |
| **Detectability**          | Encrypted payloads using Fernet                 |
| **Information Disclosure** | Encryption + minimal field exposure             |
| **Unawareness**            | Not currently addressed                         |
| **Non-compliance**         | Dependent on legal/regulatory adoption          |
| **Non-repudiation**        | Not implemented (would require logs/signatures) |


# By 
Thusif Amaan Mohammed

G01547322

Cyber Security Engineering

George Mason University








