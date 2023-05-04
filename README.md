# MQTT Test

> This repository shows a simple example of how to use MQTT in Python.

## Setup

### Setting up MQTT Docker

1. Run the docker container with mosquitto
    ```sh
    docker run -d --name mosquitto -p 1883:1883 eclipse-mosquitto
    ```
2. Edit the config file
    1. Open a shell in the container
        ```sh
        docker exec -it mosquitto /bin/sh
        ```
    2. Install nano
        ```sh
        apk update && apk add nano
        ```
    3. Open the config file
        ```sh
        nano /mosquitto/config/mosquitto.conf
        ```
    4. Add following code into the config file
        ```
        allow_anonymous true
        listener 1883 0.0.0.0
        ```

### Setting up Python

Create an environment and install the paho-mqtt package

```sh
conda create -n mqtt
conda install -c conda-forge paho-mqtt
conda activate mqtt
```

## Usage

Run the publisher and subscriber in two different terminals

Publisher:

```sh
python mqtt_pub.py
```

Subscriber:

```sh
python mqtt_sub.py
```
