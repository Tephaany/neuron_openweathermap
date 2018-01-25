# intelora-OpenWeatherMap_API
A Neuron that gives the weather for today and tomorrow, including other related data such as humidity, temperature, and etc. for a specific location

## Synopsis 

Make Intelora give you either the weather today or tomorrow, with the related data (humidity, temperature, etc ...) for a given location. 

## Installation
```
intelora install --git-url https://github.com/intelora/neuron_openweathermap.git
```

## Options

| parameter | required | default | choices                     | comment                                                                                           |
|-----------|----------|---------|-----------------------------|---------------------------------------------------------------------------------------------------|
| api_key   | YES      | None    |                             | User API key of the OWM API                                                                       |
| location  | YES      | None    |                             | The location                                                                                      |
| lang      | No       | en      | multiple                    | First 2 letters cf : section Multilingual support in : [lang](https://openweathermap.org/current) |
| temp_unit | No       | Kelvin  | Celsius, Kelvin, Fahrenheit |                                                                                                   |
| country   | No       | US      | multiple                    |  Frist 2 letters of the country cf API doc                                                        |

## Return Values

| Name                        | Description                                | Type   | sample                 |
|-----------------------------|--------------------------------------------|--------|------------------------|
| location                    | The current location                       | String | Grenoble               |
| weather_today               | Today : The weather sentence               | String | cloudy                 |
| sunset_today_time           | Today : The sunset time (iso)              | String | 2016-10-15 20:07:57+00 |
| sunrise_today_time          | Today : The sunrise time (iso)             | String | 2016-10-15 07:07:57+00 |
| temp_today_temp             | Today : Average temperature                | float  | 25                     |
| temp_today_temp_max         | Today : Max temperature                    | float  | 45                     |
| temp_today_temp_min         | Today : Min temperatue                     | float  | 5                      |
| pressure_today_press        | Today : Pressure                           | float  | 1009                   |
| pressure_today_sea_level    | Today : Pressure at the Sea level          | float  | 1038.381               |
| humidity_today              | Today : % of humidity                      | float  | 60                     |
| wind_today_deg              | Today : Direction of the wind in degree    | float  | 45                     |
| wind_today_speed            | Today : Wind speed                         | float  | 2.66                   |
| snow_today                  | Today : Volume of snow                     | float  | 0                      |
| rain_today                  | Today : Rain volume                        | float  | 0                      |
| clouds_coverage_today       | Today : % Cloud coverage                   | float  | 65                     |
| weather_tomorrow            | Tomorrow : The weather sentence            | String | sunny                  |
| sunset_time_tomorrow        | Tomorrow : The sunset time (iso)           | String | 2016-10-16 20:07:57+00 |
| sunrise_time_tomorrow       | Tomorrow : The sunrise time (iso)          | String | 2016-10-16 07:07:57+00 |
| temp_tomorrow_temp          | Tomorrow : Average temperature             | float  | 25                     |
| temp_tomorrow_temp_max      | Tomorrow : Max temperature                 | float  | 45                     |
| temp_tomorrow_temp_min      | Tomorrow : Min temperatue                  | float  | 5                      |
| pressure_tomorrow_press     | Tomorrow : Pressure                        | float  | 1009                   |
| pressure_tomorrow_sea_level | Tomorrow : Pressure at the Sea level       | float  | 1038.381               |
| humidity_tomorrow           | Tomorrow : % of humidity                   | float  | 60                     |
| wind_tomorrow_deg           | Tomorrow : Direction of the wind in degree | float  | 45                     |
| wind_tomorrow_speed         | Tomorrow : Wind speed                      | float  | 2.66                   |
| snow_tomorrow               | Tomorrow : Volume of snow                  | float  | 0                      |
| rain_tomorrow               | Tomorrow : Rain volume                     | float  | 0                      |
| clouds_coverage_tomorrow    | Tomorrow : % Cloud coverage                | float  | 65                     |

## Limitation

-Note: You need to create a free account on openweathermap.org to get your API key.
-Available Return Values:
The current location
Today : The weather sentence
Today : The sunset time (iso)
Today : The sunrise time (iso)
Today : Average temperature
Today : Max temperature
Today : Min temperatue
Today : Pressure
Today : Pressure at the Sea level
Today : % of humidity
Today : Direction of the wind in degree
Today : Wind speed
Today : Volume of snow
Today : Rain volume
Today : % Cloud coverage
Tomorrow : The weather sentence
Tomorrow : The sunset time (iso)
Tomorrow : The sunrise time (iso)
Tomorrow : Average temperature	
Tomorrow : Max temperature
Tomorrow : Min temperatue
Tomorrow : Pressure	
Tomorrow : Pressure at the Sea level
Tomorrow : % of humidity	
Tomorrow : Direction of the wind in degree	
Tomorrow : Wind speed	
Tomorrow : Volume of snow	
Tomorrow : Rain volume	
Tomorrow : % Cloud coverage


## Synapses example

Load the location from your order
```
  - name: "openweathermap"
    signals:
      - order: "what is the weather in {{ location }}"
      - order: "what's the weather in {{ location }}"
    neurons:
      - openweathermap:
          api_key: "644e1a900dd8f28ec1b4d613e3674015"
          lang: "en"
          temp_unit: "celsius"
          location: "{{ location }}"
          say_template:
          - "Today in {{ location }} the weather is {{ weather_today }} with a temperature of {{ temp_today_temp }} degrees. The forecast tomorrow will be {{ weather_tomorrow }} with a temperature of {{ temp_tomorrow_temp }} degrees."
          
```

## Templates example 

```
Today in {{ location }} the weather is {{ weather_today }} with a temperature of {{ temp_today_temp }} degree
```


## Notes

> **Note:** You need to create a free account on [openweathermap.org](http://openweathermap.org/) to get your API key.

## License

Copyright (c) 2016. All rights reserved.

Intelora is covered by the MIT license, a permissive free software license that lets you do anything you want with the source code, 
as long as you provide back attribution and ["don't hold you liable"](http://choosealicense.com/). For the full license text see the [LICENSE.md](LICENSE.md) file.
