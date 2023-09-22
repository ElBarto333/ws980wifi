# ELV WS980WiFi - Weatherstation

The ELV WS980WiFi sensor platform provides a range of sensor values of your weather station

| Titel | Description | ha_category | ha_release | ha_iot_class | ha_domain |
| :--- | :--- | :---: | :---: | :---: | :---: |
| ELV WS980WiFi | Instructions on how to integrate ELV WS980WiFi sensor within Home Assistant. | Sensor, Weather | 0.7 | Configurable | ws980wifi |

## Installation
### Install with HACS (recommended)

Add the link to this github repo to your custom repositories in HACS. The integration should show up as a new integration so click on it and install.

### Manual installation

Clone or copy this repository and copy the folder 'ws980wifi' which can be found [here](https://github.com/eXtgmA/ws980wifi/tree/master/custom_components) into your '/custom components' folder.
Restart Home Assistant and then continue with the configuration:

## Configuration

To use WS980WiFi sensors in your installation, add the following to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry
sensor:
  - platform: ws980wifi
    host: 192.168.178.2
```
|Parameter            |Description                           |Requiered     |Type           |Default           |
|---------------------|--------------------------------------|--------------|---------------|------------------|
|name                 |The name of the device                |`false`       |`string`         |                  |
|host                 |IP address of your weather station    |`true`        |`string`         |                  |
|port                 |Port of your weather station          |`false`       |`string`         |45000             |
|unique_id            |Vendors Product ID                    |`false`       |`string`         |                  |
|monitored_conditions |Conditions to display in the frontend |`false`       |`list`           |inside_temperature|

|Keys for monitored_conditions |Unit |Description                                                               |
|------------------------------|-----|--------------------------------------------------------------------------|
|inside_temperature   |`°C`       |The current inside temperature measured by your control panel       |
|outside_temperature  |`°C`       |The current outside temperature measured by your weather station   |
|dew_point            |`°C`       |Dew point in °C
|apparent_temperature |`°C`       |Apparent temperature in °C
|heat_index           |`°C`       |Heat index in °C
|inside_humidity      |`%`        |The current inside humidity measured by your control panel
|outside_humidity     |`%`        |The current outside humidity measured by your weather station
|pressure_absolute    |`hPa`      |The current absolute air pressure
|pressure_relative    |`hPa`      |The current relative air pressure
|wind_direction       |`°`        |Where the wind is coming from in degrees, with true north at 0° and progressing clockwise
|wind_speed           |`km/h`     |The wind speed (usually measured over the period of 2 minutes)
|gust                 |`km/h`     |The wind gust (usually measured over the period of less than 20 seconds)
|rain                 |`mm`       |Current rain
|rain_day             |`mm`       |Total rain of the current day
|rain_week            |`mm`       |Total rain of the current week
|rain_month           |`mm`       |Total rain of the current month
|rain_year            |`mm`       |Total rain of the current year
|rain_total           |`mm`       |Total rain of all time
|light                |`lx`       |The current Illuminance level
|uv_value             |`uW/m²`    |The current UV value
|uv_index             |`UV Index `|The current UV index


A full configuration example can be found below:

```yaml
# Example configuration.yaml entry
sensor:
  - platform: ws980wifi
    name: WeatherStation
    host: 192.168.178.2
    port: 45000
    unique_id: ELV-2504508-94 # vendor-productid-sensorid
    monitored_conditions:
      - inside_temperature
      - outside_temperature
      - dew_point
      - apparent_temperature
      - heat_index
      - inside_humidity
      - outside_humidity
      - pressure_absolute
      - pressure_relative
      - wind_direction
      - wind_speed
      - gust
      - rain
      - rain_day
      - rain_week
      - rain_month
      - rain_year
      - rain_total
      - light
      - uv_value
      - uv_index
```
