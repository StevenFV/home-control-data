# home-control-data

This repository contains the setup configuration for services Zigbee2MQTT and EMQX. This backend server have to be used with [Home-Control-App](https://github.com/StevenFV/home-control-app).  

**Prerequisites**

* Ubuntu server (lastest version recommanded)
* Basic understanding of Linux administration
* Compatible router

**Getting Started**

1. **Server Setup**
   * Install Ubuntu server on your designated machine.
   * **Strongly Recommended:** Create a non-root user with sudo privileges for enhanced security.
   * Update and upgrade packages:  `sudo apt update && sudo apt upgrade` 

2. **Security**
   * **SSH:** 
      * Configure the SSH connection to the server.

3. **Database Installation**
   * Install a PostgreSQL database.
   * Create a databases who will be used for the Home-Control-App.

5. **Router Configuration - If you want access the application data remotely**
   * **Port Forwarding:**
      * Configure a Dynamic DNS on your Router.
      * Forward the following ports from your router to your internal server:
          * 22:2222 -> Server's SSH
          * 1883:1883 -> Your EMQX server's MQTT port
          * 80 -> Web server (if applicable)

6. **EMQX Installation and Configuration**
   * Refer to the EMQX documentation: https://www.emqx.io/
   * Configure EMQX from the dashboard.
   * Set up strict username/password authentication.

7. **Zigbee2MQTT Installation and Configuration**
   * **Docker:** If not already present, install Docker: https://docs.docker.com/get-docker/ 
   * **Zigbee2MQTT:** Install using Docker (https://www.zigbee2mqtt.io/guide/installation/02_docker.html)
   * Update the `mqtt.server` and `serial.port` parameters in your Zigbee2MQTT configuration file to match your specific setup.

8. **Security (MQTT)**
   * In both EMQX and Zigbee2MQTT:
       * Enforce username/password authentication.
       * Consider enabling TLS/SSL if supported.

9. **Device Pairing** 
   * Follow manufacturer instructions for your smart devices (Jasco Enbrighten, Stelpro thermostat, etc.).
   * Refer to Zigbee2MQTT documentation for pairing and network setup. 

10. **Backup**
    * Develop a robust backup strategy for:
       * Database
       * Configuration files
       * Zigbee network data
