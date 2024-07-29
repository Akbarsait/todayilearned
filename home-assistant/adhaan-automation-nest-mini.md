# Adding Adhan Automation with Home Assistant and Nest Mini
Add the following codes in respective files. Detailed instructions posted by the author [Sahar](https://community.home-assistant.io/t/adhan-automation-using-home-assistant-and-google-home-mini/135622) at Home Assistant. Customization is added for Fajr and to the rest of the Prayer times. 

1. Add the following code to `configuration.yaml`. Don't forget to change **latitude, longitude, elevation and time zone** to match your location. You can use [Timezone DB](https://timezonedb.com/) to get the information. 

````yaml
homeassistant:
  latitude: 43.65107
  longitude: -79.347015
  unit_system: metric
  time_zone: America/Toronto
  
default_config:
discovery:
media_extractor:
sun:

# Islamic prayer times integration
islamic_prayer_times:
    calculation_method: mwl

# Sensors
sensor:
  - platform: time_date
    display_options:
      - 'time'
      - 'date'
      - 'time_date'
  - platform: template
    sensors:
      salah_fajr:
        friendly_name: "Salah Fajr"
        value_template: >
           {%- set a = states("sensor.fajr_prayer").split("T")[1].split(":")[0] -%}
           {%- set b = states("sensor.fajr_prayer").split("T")[1].split(":")[1] -%}
           {{ a + ":" + b }}
      salah_dhuhr:
        friendly_name: "Salah Dhuhr"
        value_template: >
           {%- set a = states("sensor.dhuhr_prayer").split("T")[1].split(":")[0] -%}
           {%- set b = states("sensor.dhuhr_prayer").split("T")[1].split(":")[1] -%}
           {{ a + ":" + b }}
      salah_asr:
        friendly_name: "Salah Asr"
        value_template: >
           {%- set a = states("sensor.asr_prayer").split("T")[1].split(":")[0] -%}
           {%- set b = states("sensor.asr_prayer").split("T")[1].split(":")[1] -%}
           {{ a + ":" + b }}
      salah_maghrib:
        friendly_name: "Salah Maghrib"
        value_template: >
           {%- set a = states("sensor.maghrib_prayer").split("T")[1].split(":")[0] -%}
           {%- set b = states("sensor.maghrib_prayer").split("T")[1].split(":")[1] -%}
           {{ a + ":" + b }}
      salah_isha:
        friendly_name: "Salah Isha"
        value_template: >
           {%- set a = states("sensor.isha_prayer").split("T")[1].split(":")[0] -%}
           {%- set b = states("sensor.isha_prayer").split("T")[1].split(":")[1] -%}
           {{ a + ":" + b }}
````

2. Open `automation.yaml` file to add the following code. Caution: In the code below, against entity_id, don’t forget to replace **nest_mini_office** with your Google Home Mini ID. In the code below you have to enter your google home mini name in small letters. If the name is more than a one-word name, you have to put under-score after every word. Let say the name of your device is My Home, it should be written as my_home. If it is one word name only, just type it in small letters.

````yaml
# Automation for Fajr  Adhan
- action:
    - alias: "FajrAdhan"
      data:
        entity_id: media_player.nest_mini_office
        media_content_id: https://soundcloud.com/androiddudes-onweb/adhanal-fajr-mansoor
        media_content_type: audio/mp3
      service: media_extractor.play_media
    - data:
        entity_id: media_player.nest_mini_office
        volume_level: "0.5"
      service: media_player.volume_set
  alias: Fajr_Adhan
  trigger:
    - platform: template
      value_template: '{{ as_timestamp(strptime(states("sensor.time_date"), "%H:%M, %Y-%m-%d")) == as_timestamp(strptime(states("sensor.fajr_prayer"), "%Y-%m-%dT%H:%M:%S")) }}'

# Automation for 4 times Adhan
- action:
    - alias: "FourAdhan"
      data:
        entity_id: media_player.nest_mini_office
        media_content_id: https://soundcloud.com/androiddudes-onweb/adhaan-mishary
        media_content_type: audio/mp3
      service: media_extractor.play_media
    - data:
        entity_id: media_player.nest_mini_office
        volume_level: "0.8"
      service: media_player.volume_set
  alias: Adhan
  trigger:
    - platform: template
      value_template: '{{ as_timestamp(strptime(states("sensor.time_date"), "%H:%M, %Y-%m-%d")) == as_timestamp(strptime(states("sensor.dhuhr_prayer"), "%Y-%m-%dT%H:%M:%S")) }}'
    - platform: template
      value_template: '{{ as_timestamp(strptime(states("sensor.time_date"), "%H:%M, %Y-%m-%d")) == as_timestamp(strptime(states("sensor.asr_prayer"), "%Y-%m-%dT%H:%M:%S")) }}'
    - platform: template
      value_template: '{{ as_timestamp(strptime(states("sensor.time_date"), "%H:%M, %Y-%m-%d")) == as_timestamp(strptime(states("sensor.maghrib_prayer"), "%Y-%m-%dT%H:%M:%S")) }}'
    - platform: template
      value_template: '{{ as_timestamp(strptime(states("sensor.time_date"), "%H:%M, %Y-%m-%d")) == as_timestamp(strptime(states("sensor.isha_prayer"), "%Y-%m-%dT%H:%M:%S")) }}'

```