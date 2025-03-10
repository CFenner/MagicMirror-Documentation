# Weather Module

This module is aimed to be the replacement for the current `currentweather` and `weatherforcast` modules. The module will be configurable to be used as a current weather view, or to show the forecast. This way the module can be used twice to fulfill both purposes.

The biggest change is the use of weather providers. This way we are not bound to one API source. And users can choose which API they want to use as their source.

The module is in a very early stage, and needs a lot of work. It's API isn't set in stone, so keep that in mind when you want to contribute.

## Example

![Screenshot of current weather](./screenshots/current.png)
![Screenshot of forecast](./screenshots/forecast.png)

## Usage

To use this module, add it to the modules array in the `config/config.js` file:

````javascript
modules: [
	{
		module: "weather",
		position: "top_right",
		config: {
			// See 'Configuration options' for more information.
			type: 'current'
		}
	}
]
````

## Configuration options

The following properties can be configured:

### General options

| Option                       | Description
| ---------------------------- | -----------
| `weatherProvider`            | Which weather provider should be used. <br><br> **Possible values:** `openweathermap` , `darksky` , `weathergov`, `ukmetofficedatahub`, `ukmetoffice`, `weatherbit`, or `envcanada`<br> **Default value:** `openweathermap`
| `type`                       | Which type of weather data should be displayed. <br><br> **Possible values:** `current` , `hourly` , `daily` , or `forecast` <br> **Default value:** `current` <br><br> **Note:** The `daily` type is another name for the `forecast` type, and the two are interchangeable. <br><br> The `hourly` type is currently only implemented for: <br> **Environment Canada** (`envcanada`) provider <br> **OpenWeatherMap** provider, and only when `/onecall` is used as the specified endpoint.
| `units`                      | What units to use. Specified by config.js <br><br> **Possible values:** `config.units` = Specified by config.js, `default` = Kelvin, `metric` = Celsius, `imperial` = Fahrenheit <br> **Default value:** `config.units`
| `tempUnits`                  | What units to use for temperature. If not specified, the module uses the `units` value from `config.js`. <br><br> **Possible values:** `config.units` = Specified by config.js, `default` = Kelvin, `metric` = Celsius, `imperial` = Fahrenheit <br> **Default value:** `units`
| `windUnits`                  | What units to use for wind speed. If not specified, the module uses the `units` value from `config.js`. <br><br> **Possible values:** `config.units` = Specified by config.js, `mps` = metres per second, `kmh` or `metric` = kilometres per hour, `mph` or `imperial` = miles per hour **Default value:** `units`
| `roundTemp`                  | Round temperature value to nearest integer. <br><br> **Possible values:** `true` (round to integer) or `false` (display exact value with decimal point) <br> **Default value:** `false`
| `degreeLabel`                | Show the degree label for your chosen units (Metric = C, Imperial = F, Kelvin = K). <br><br> **Possible values:** `true` or `false` <br> **Default value:** `false`
| `updateInterval`             | How often does the content needs to be fetched? (Milliseconds) <br><br> **Possible values:** `1000` - `86400000` <br> **Default value:** `600000` (10 minutes)
| `animationSpeed`             | Speed of the update animation. (Milliseconds) <br><br> **Possible values:** `0` - `5000` <br> **Default value:** `1000` (1 second)
| `timeFormat`                 | Use 12 or 24 hour format. <br><br> **Possible values:** `12` or `24` <br> **Default value:** uses value of _config.timeFormat_
| `showPeriod`                 | Show the period (am/pm) with 12 hour format <br><br> **Possible values:** `true` or `false` <br> **Default value:** `true`
| `showPeriodUpper`	           | Show the period (AM/PM) with 12 hour format as uppercase <br><br> **Possible values:** `true` or `false` <br> **Default value:** `false`
| `lang`                       | The language of the days. <br><br> **Possible values:** `en`, `nl`, `ru`, etc ... <br> **Default value:** uses value of _config.language_
| `decimalSymbol`              | The decimal symbol to use.<br><br> **Possible values:** `.`, `,` or any other symbol.<br> **Default value:** `.`
| `initialLoadDelay`           | The initial delay before loading. If you have multiple modules that use the same API key, you might want to delay one of the requests. (Milliseconds) <br><br> **Possible values:** `1000` - `5000` <br> **Default value:** `0`
| `appendLocationNameToHeader` | If set to `true`, the returned location name will be appended to the header of the module, if the header is enabled. This is mainly interesting when using calender based weather. <br><br> **Default value:** `true`
| `calendarClass`              | The class for the calender module to base the event based weather information on. <br><br> **Default value:** `'calendar'`

#### Current weather options

| Option                       | Description
| ---------------------------- | -----------
| `onlyTemp`                   | Show only current Temperature and weather icon without windspeed, sunset, sunrise time and feels like. <br><br> **Possible values:** `true` or `false` <br> **Default value:** `false`
| `useBeaufort`                | Pick between using the Beaufort scale for wind speed or using the default units. <br><br> **Possible values:** `true` or `false` <br> **Default value:** `true`
| `showWindDirection`          | Show the wind direction next to the wind speed. <br><br> **Possible values:** `true` or `false` <br> **Default value:** `true`
| `showWindDirectionAsArrow`   | Show the wind direction as an arrow instead of abbreviation <br><br> **Possible values:** `true` or `false` <br> **Default value:** `false`
| `showHumidity`               | Show the current humidity <br><br> **Possible values:** `true` or `false` <br> **Default value:** `false`
| `showIndoorTemperature`      | If you have another module that emits the `INDOOR_TEMPERATURE` notification, the indoor temperature will be displayed <br> **Default value:** `false`
| `showIndoorHumidity`         | If you have another module that emits the `INDOOR_HUMIDITY` notification, the indoor humidity will be displayed <br> **Default value:** `false`
| `showFeelsLike`              | Shows the Feels like temperature weather. <br><br> **Possible values:** `true` or `false`<br>**Default value:** `true`
| `showSun`                    | Shows Sunrise and Sunset time. <br><br> **Possible values:** `true` or `false`<br>**Default value:** `true`

#### Weather forecast options

| Option                       | Description
| ---------------------------- | -----------
| `tableClass`                 | The class for the forecast table. <br><br> **Default value:** `'small'`
| `colored`                    | If set to `true`, the min and max temperature are color coded. <br><br> **Default value:** `false`
| `showPrecipitationAmount`    | Show the amount of rain/snow in the forecast <br><br> **Possible values:** `true` or `false` <br> **Default value:** `false`
| `fade`                       | Fade the future events to black. (Gradient) <br><br> **Possible values:** `true` or `false` <br> **Default value:** `true`
| `fadePoint`                  | Where to start fade? <br><br> **Possible values:** `0` (top of the list) - `1` (bottom of list) <br> **Default value:** `0.25`
| `maxNumberOfDays`            | How many days of forecast to return. Specified by config.js <br><br> **Possible values:** `1` - `16` <br> **Default value:** `5` (5 days) <br> This value is optional. By default the weather module will return 5 days.
| `maxEntries`                 | How many entries of an OpenWeatherMap One Call hourly or daily forecast type to return. Specified by config.js <br><br> **Possible values:** `1` - `48` for `'hourly'` , `1` - `7` for `'daily'` <br> **Default value:** `5` (5 entries) <br> This value is optional and specifically meant to be used with the OpenWeatherMap provider and its `'/onecall'` endpoint. By default the weather module will return 5 entries. Intended to act as a more generalized of the `maxNumberOfDays` option.
| `ignoreToday`                | If set to `true`, today's weather will not be displayed. <br><br> **Possible values:** `true` or `false` <br> **Default value:** `false`

### Openweathermap options

| Option                       | Description
| ---------------------------- | -----------
| `apiVersion`                 | The OpenWeatherMap API version to use. <br><br> **Default value:** `2.5`
| `apiBase`                    | The OpenWeatherMap base URL. <br><br> **Default value:** `'https://api.openweathermap.org/data/'`
| `weatherEndpoint`	           | The OpenWeatherMap API endPoint. <br><br> **Possible values:** `'/weather'` , `'/onecall'` , `'/forecast'` (free users) or `'/forecast/daily'` (paying users or old apiKey only) <br> **Default value:** `'/weather'`
| `locationID`                 | Location ID from [OpenWeatherMap](https://openweathermap.org/find) **This will override anything you put in location.** <br> Leave blank if you want to use location. <br> **Example:** `1234567` <br> **Default value:** `false` <br><br> **Note:** When the `location` and `locationID` are both not set, the location will be based on the information provided by the calendar module. The first upcoming event with location data will be used.
| `location`                   | The location used for weather information. <br><br> **Example:** `'Amsterdam,Netherlands'` <br> **Default value:** `false` <br><br> **Note:** When the `location` and `locationID` are both not set, the location will be based on the information provided by the calendar module. The first upcoming event with location data will be used.
| `lat`                        | Latitude of the location used for weather information. <br><br> **Example:** `40.7128` <br> **Default value:** `0` <br><br> **Note:** Latitude and longitude are **REQUIRED** if `weatherEndpoint` is set to `'/onecall'`. The `locationID` and `location` options are ignored when the OpenWeatherMap One Call API is used.
| `lon`                        | Longitude of the location used for weather information. <br><br> **Example:** `-74.0060` <br> **Default value:** `0` <br><br> **Note:** Latitude and longitude are **REQUIRED** if `weatherEndpoint` is set to `'/onecall'`. The `locationID` and `location` options are ignored when the OpenWeatherMap One Call API is used.
| `apiKey`                     | The [OpenWeatherMap](https://home.openweathermap.org) API key, which can be obtained by creating an OpenWeatherMap account. <br><br> This value is **REQUIRED**

### Darksky options

| Option                       | Description
| ---------------------------- | -----------
| `apiBase`                    | The DarkSky base URL. The darksky api has disabled [cors](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS), therefore a proxy is required. <br><br> **Possible value:** `'https://cors-anywhere.herokuapp.com/https://api.darksky.net'` <br> This value is **REQUIRED**
| `weatherEndpoint`	           | The DarkSky API endPoint. <br><br> **Possible values:** `/forecast` <br> This value is **REQUIRED**
| `apiKey`                     | The [DarkSky](https://darksky.net/dev/register) API key, which can be obtained by creating an DarkSky account. Please note Dark Sky no longer accept new signups. The API will continue to function through the end of 2021.<br><br> This value is **REQUIRED**
| `lat`                        | The geo coordinate latitude. <br><br> This value is **REQUIRED**
| `lon`                        | The geo coordinate longitude. <br><br> This value is **REQUIRED**

### Weather.gov options

| Option                       | Description
| ---------------------------- | -----------
| `apiBase`                    | The weather.gov base URL. <br><br> **Possible value:** `'https://api.weather.gov/points/'` <br> This value is **REQUIRED**
| `weatherEndpoint`	           | The weather.gov API endPoint. <br><br> **Possible values:** `/forecast` for forecast and `/forecast/hourly` for current. <br> This value is **REQUIRED**
| `lat`                        | The geo coordinate latitude. <br><br> This value is **REQUIRED**
| `lon`                        | The geo coordinate longitude. <br><br> This value is **REQUIRED**

### UK Met Office (`ukmetoffice`) options

| Option                       | Description
| ---------------------------- | -----------
| `apiBase`                    | The UKMO base URL. <br><br> **Possible value:**  `'https://datapoint.metoffice.gov.uk/public/data/val/wxfcs/all/json/'` <br>  This value is **REQUIRED**
| `locationID`	               | The UKMO API location code. <br><br> **Possible values:** `322942` <br>  This value is **REQUIRED**
| `apiKey`                     | The [UK Met Office](https://www.metoffice.gov.uk/datapoint/getting-started) API key, which can be obtained by creating an UKMO Datapoint account. <br><br>  This value is **REQUIRED**

### UK Met Office (`ukmetofficedatahub`) options

| Option                       | Description
| ---------------------------- | -----------
| `apiBase`                    | The UKMO DataHub base URL.<br><br> **Possible value:**  `'https://api-metoffice.apiconnect.ibmcloud.com/metoffice/production/v0/forecasts/point/'` <br> This value is **REQUIRED**
| `apiKey`                     | Your API key (MetOffice API ClientID). See the [Getting Started](https://metoffice.apiconnect.ibmcloud.com/metoffice/production/start) guide on the Met Office website for creating a new account. <br> This value is **REQUIRED**
| `apiSecret`                  | Your API secret (MetOffice API ClientSecret). <br> This value is **REQUIRED**
| `lat`                        | The latitude coordinate for the desired location. <br><br> **Possible value:** `50.7271915` <br> This value is **REQUIRED**
| `lon`                        | The longitude coordinate for the desired location. <br><br> **Possible value:** `-3.4776089` <br> This value is **REQUIRED**
| `windUnits`                  | Set the units for wind speed. If not specified, uses the `units` value from `config.js`. This option is useful for those in the UK, for example, where we use metric units but have wind speed in mph. <br><br> **Possible values:** `mps` = metres per second, `kmh` or `metric` = kilometres per hour, `mph` or `imperial` = miles per hour

### Weatherbit options
| Option                       | Description
| ---------------------------- | -----------
|`apiBase`                     | The Weather base URL.<br><br> **Possible value:** `https://api.weatherbit.io/v2.0` <br> This value is **REQUIRED**
|`weatherEndpoint`             | The Weatherbit API endPoint.<br><br> **Possible values:** `/current`, `/forecast/daily` <br> This value is **REQUIRED**
|`apiKey`                      | The [Weatherbit API](https://www.weatherbit.io) key which can be obtained by creating an WeatherBit account  <br><br> This value is **REQUIRED**
|`lat`                         | The geo coordinate latitude. <br><br> This value is **REQUIRED**
|`lon`                         | The geo coordinate longitude. <br><br> This value is **REQUIRED**

### SMHI options

| Option                       | Description
| ---------------------------- | -----------
| `lat`                        | The latitude coordinate for the desired location. <br><br> **Possible value:** `59.322665376` <br> This value is **REQUIRED**
| `lon`                        | The longitude coordinate for the desired location. <br><br> **Possible value:** `18.069666388` <br> This value is **REQUIRED**
| `precipitationValue`         | The type of precipitation to display (min, max, median, mean).  <br><br> **Possible values:** `'pmin'` , `'pmean'` , `'pmedian'`, `'pmax'`. <br> **Default value:** `'pmedian'`

### Environment Canada (`envcanada`) options

**Note** that `envcanada` supports Canadian locations only.

When using the `type: "forecast"` config, the module can display a max of 6 days (Today + the next 5 days). The forecast for each day reflects the daytime forecast. The Today forecast is a special case that will reflect the daytime forecast until late afternoon, after which Today will be reflecting the nightime forecast for the current day.

When using the `type: "hourly"` config, the module can display a max of 24 hours.


| Option                       | Description
| ---------------------------- | -----------
| `siteCode`                   | The city/town unique identifier for which weather is to be displayed. <br><br> **Example:** `siteCode: 's0000458'` is the value for Toronto, Ontario <br><br> To determine the `siteCode` value for a Canadian city/town, look at the Environment Canada document at https://dd.weather.gc.ca/citypage_weather/docs/site_list_en.csv (or site_list_fr.csv). There you will find a table with city/town names you can search under column B (English Names), with the corresponding `siteCode` under column A (Codes) <br><br> This value is **REQUIRED**
| `provCode`                   | The 2-character province code for the selected city/town `siteCode`. <br><br> **Example:** `provCode: 'ON'` is the value for Toronto, Ontario <br><br> To determine the `provCode` value for a Canadian city/town, look at the Environment Canada document at https://dd.weather.gc.ca/citypage_weather/docs/site_list_en.csv (or site_list_fr.csv). There you will find a table with city/town names you can search under column B (English Names), with the corresponding `provCode` under column C (Province) - and of course the `siteCode` under column A (Codes) <br><br> This value is **REQUIRED**
| `location`		       | The free-format text string intended to hold a location name (e.g. city) that should appear in the module header. <br><br> **Example:** `location: 'Toronto, ON'`

## API Provider Development

If you want to add another API provider checkout the [Guide](https://github.com/MichMich/MagicMirror/tree/master/modules/default/weather/providers).
