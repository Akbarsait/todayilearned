# Adding Adhan Automation with Home Assistant and Nest Mini
Add the following codes in respective files. Detailed instructions posted by the author [Sahar](https://community.home-assistant.io/t/adhan-automation-using-home-assistant-and-google-home-mini/135622) at Home Assistant. Customization is added for Fajr and to the rest of the Prayer times. 

> **Created**: 12/29/2020 **Updated**: 02/07/2024

Requires the following two integrations. 
- [Islamic Prayer Times](https://www.home-assistant.io/integrations/islamic_prayer_times)
- [Time & Date](https://www.home-assistant.io/integrations/time_date)

1. Add the following code to `configuration.yaml`. Don't forget to change **latitude, longitude, elevation and time zone** to match your location. You can use [Timezone DB](https://timezonedb.com/) to get the information. 

```yaml
# Configure a default setup of Home Assistant (frontend, api, etc)
# to find lat and long - https://www.maps.ie/coordinates.html
homeassistant:
  latitude: 43.75167
  longitude: -79.26541
  unit_system: metric
  time_zone: America/Toronto
  media_dirs:
    media: "/media"

default_config:
discovery:
#media_extractor:
sun:

# Islamic prayer times integration starts updated 12/04/22
# Sensors
sensor:
  - platform: time_date
    display_options:
      - "time"
      - "date"
      - "date_time"
      - "time_date"
    calculation_method: Shafi
    sensors:
      - fajr
      - dhuhr
      - asr
      - maghrib
      - isha

# Text to speech
tts:
  - platform: google_translate

group: !include groups.yaml
automation: !include automations.yaml
script: !include scripts.yaml
scene: !include scenes.yaml
```

2. In `automation.yaml`, add the following codes. The code includes references of my system ID and path. Kindly update it accordingly. 
   - replace **nest_mini_office** with your Google Home Mini entity ID. 
   - replace the media content location. 

```yaml
# Automation for Fajr Adhan
- action:
    - alias: "FajrAdhan"
      data:
        entity_id: media_player.nestmini8653
        media_content_id: http://localip:8123/local/adhan/fajr-adhan-mansoor.mp3
        media_content_type: audio/mp3
      service: media_extractor.play_media
    - data:
        entity_id: media_player.nestmini8653
        volume_level: "0.6"
      service: media_player.volume_set
  alias: Fajr_Adhan
  condition: []
  id: "1517693013922"
  trigger:
    - platform: template
      value_template: '{{ now().timestamp()|int == as_timestamp(states("sensor.fajr_prayer")) }}'

# Automation for 4 times Azan
- action:
    - alias: "FourAdhan"
      data:
        entity_id: media_player.nestmini8653
        media_content_id: http://localip:8123/local/adhan/all-adhan-mishary.mp3
        media_content_type: audio/mp3
      service: media_extractor.play_media
    - data:
        entity_id: media_player.nestmini8653
        volume_level: "0.8"
      service: media_player.volume_set
  alias: Four_Adhan
  condition: []
  id: "1517694139312"
  trigger:
    - platform: template
      value_template: '{{ now().timestamp()|int == as_timestamp(states("sensor.dhuhr_prayer")) }}'
    - platform: template
      value_template: '{{ now().timestamp()|int == as_timestamp(states("sensor.asr_prayer")) }}'
    - platform: template
      value_template: '{{ now().timestamp()|int == as_timestamp(states("sensor.maghrib_prayer")) }}'
    - platform: template
      value_template: '{{ now().timestamp()|int == as_timestamp(states("sensor.isha_prayer")) }}'

```