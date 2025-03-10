# Calendar
The `calendar` module is one of the default modules of the MagicMirror.
This module displays events from a public .ical calendar. It can combine multiple calendars.

## Using the module

To use this module, add it to the modules array in the `config/config.js` file:
````javascript
modules: [
	{
		module: "calendar",
		position: "top_left",	// This can be any of the regions. Best results in left or right regions.
		config: {
			// The config property is optional.
			// If no config is set, an example calendar is shown.
			// See 'Configuration options' for more information.
		}
	}
]
````

## Configuration options

The following properties can be configured:

| Option                       | Description
| ---------------------------- | -----------
| `maximumEntries`             | The maximum number of events shown. / **Possible values:** `0` - `100` <br> **Default value:** `10`
| `maximumNumberOfDays`        | The maximum number of days in the future. <br><br> **Default value:** `365`
| `displaySymbol`              | Display a symbol in front of an entry. <br><br> **Possible values:** `true` or `false` <br> **Default value:** `true`
| `defaultSymbol`              | The default symbol. <br><br> **Possible values:** See [Font Awesome](https://fontawesome.io/icons/) website. <br> **Default value:** `calendar`
| `showLocation`               | Whether to show event locations. <br><br> **Possible values:** `true` or `false` <br> **Default value:** `false`
| `maxTitleLength`             | The maximum title length. <br><br> **Possible values:** `10` - `50` <br> **Default value:** `25`
| `maxLocationTitleLength`     | The maximum location title length. <br><br> **Possible values:** `10` - `50` <br> **Default value:** `25`
| `wrapEvents`                 | Wrap event titles to multiple lines. Breaks lines at the length defined by `maxTitleLength`. <br><br> **Possible values:** `true` or `false` <br> **Default value:** `false`
| `wrapLocationEvents`         | Wrap event location titles to multiple lines. Breaks lines at the length defined by `maxLocationTitleLength`. <br><br> **Possible values:** `true` or `false` <br> **Default value:** `false`
| `maxTitleLines`              | The maximum number of lines a title will wrap vertically before being cut (Only enabled if `wrapEvents` is also enabled). <br><br> **Possible values:** `0` - `10` <br> **Default value:** `3`
| `maxEventTitleLines`         | The maximum number of lines a location title will wrap vertically before being cut (Only enabled if `wrapLocationEvents` is also enabled). <br><br> **Possible values:** `0` - `10` <br> **Default value:** `3`
| `fetchInterval`              | How often does the content needs to be fetched? (Milliseconds) <br><br> **Possible values:** `1000` - `86400000` <br> **Default value:** `300000` (5 minutes)
| `animationSpeed`             | Speed of the update animation. (Milliseconds) <br><br> **Possible values:** `0` - `5000` <br> **Default value:** `2000` (2 seconds)
| `fade`                       | Fade the future events to black. (Gradient) <br><br> **Possible values:** `true` or `false` <br> **Default value:** `true`
| `fadePoint`                  | Where to start fade? <br><br> **Possible values:** `0` (top of the list) - `1` (bottom of list) <br> **Default value:** `0.25`
| `tableClass`                 | Name of the classes issued from `main.css`. <br><br> **Possible values:** xsmall, small, medium, large, xlarge. <br> **Default value:** _small._
| `calendars`                  | The list of calendars. <br><br> **Possible values:** An array, see _calendar configuration_ below. <br> **Default value:** _An example calendar._
| `titleReplace`               | An object of textual replacements applied to the tile of the event. This allow to remove or replace certain words in the title. <br><br> **Example:** `{'Birthday of ' : '', 'foo':'bar'}` <br> **Default value:** `{	"De verjaardag van ": "", "'s birthday": ""	}`
| `displayRepeatingCountTitle` | Show count title for yearly repeating events (e.g. "X. Birthday", "X. Anniversary") <br><br> **Possible values:** `true` or `false` <br> **Default value:** `false`
| `dateFormat`                 | Format to use for the date of events when using absolute dates. (version <= 2.16.0) From version 2.16.0, this option will be used to format absolute and relative dates. (e.g. DD/MM/YY to change from the default MM/DD/YYYY) <br><br> **Possible values:** See [Moment.js formats](https://momentjs.com/docs/#/parsing/string-format/) <br> **Default value:** `MMM Do` (e.g. Jan 18th)
| `dateEndFormat`              | Format to use for the end time of events <br><br> **Possible values:** See [Moment.js formats](https://momentjs.com/docs/#/parsing/string-format/) <br> **Default value:** `HH:mm` (e.g. 16:30)
| `showEnd`                    | Show end time of events  <br><br> **Possible values:** `true` or `false` <br> **Default value:** `true`
| `fullDayEventDateFormat`     | Format to use for the date of full day events (when using absolute dates) <br><br> **Possible values:** See [Moment.js formats](https://momentjs.com/docs/#/parsing/string-format/) <br> **Default value:** `MMM Do` (e.g. Jan 18th)
| `timeFormat`                 | Display event times as absolute dates, or relative time, or using absolute date headers with times for each event next to it <br><br> **Possible values:** `absolute` or `relative` or `dateheaders` <br> **Default value:** `relative`
| `showEnd`                    | Display the end of a date as well <br><br> **Possible values:** `true` or `false` <br> **Default value:** `true`
| `getRelative`                | How much time (in hours) should be left until calendar events start getting relative? <br><br> **Possible values:** `0` (events stay absolute) - `48` (48 hours before the event starts) <br> **Default value:** `6`
| `urgency`                    | When using a timeFormat of `absolute`, the `urgency` setting allows you to display events within a specific time frame as `relative`. This allows events within a certain time frame to be displayed as relative (in xx days) while others are displayed as absolute dates <br><br> **Possible values:** a positive integer representing the number of days for which you want a relative date, for example `7` (for 7 days) <br><br> **Default value:** `7`
| `broadcastEvents`            | If this property is set to true, the calendar will broadcast all the events to all other modules with the notification message: `CALENDAR_EVENTS`. The event objects are stored in an array and contain the following fields: `title`, `startDate`, `endDate`, `fullDayEvent`, `location` and `geo`. <br><br> **Possible values:** `true`, `false` <br><br> **Default value:** `true`
| `hidePrivate`                | Hides private calendar events. <br><br> **Possible values:** `true` or `false` <br> **Default value:** `false`
| `hideOngoing`                | Hides calendar events that have already started. <br><br> **Possible values:** `true` or `false` <br> **Default value:** `false`
| `excludedEvents`             | An array of words / phrases from event titles that will be excluded from being shown. <br><br>Additionally advanced filter objects can be passed in. Below is the configuration for the advance filtering object.<br>**Required**<br>`filterBy` - string used to determine if filter is applied.<br>**Optional**<br>`until` - Time before an event to display it  Ex: [`'3 days'`, `'2 months'`, `'1 week'`]<br>`caseSensitive` - By default, excludedEvents are case insensitive, set this to true to enforce case sensitivity<br>`regex` - set to `true` if filterBy is a regex. For those not familiar with regex it is used for pattern matching, please see [here](https://regexr.com/) for more info.<br><br> **Example:** `['Birthday', 'Hide This Event', {filterBy: 'Payment', until: '6 days', caseSensitive: true}, {filterBy: '^[0-9]{1,}.*', regex: true}]` <br> **Default value:** `[]`
| `broadcastPastEvents`        | If this is set to true, events from the past `maximumNumberOfDays` will be included in event broadcasts <br> **Default value:** `false`
| `sliceMultiDayEvents`        | If this is set to true, events exceeding at least one midnight will be sliced into separate events including a counter like (1/2). This is especially helpful in "dateheaders" mode. Events will be sliced at midnight, end time for all events but the last will be 23:59 <br> **Default value:** `false`
| `nextDaysRelative`           | If this is set to true, the appointments of today and tomorrow are displayed relatively, even if the timeformat is set to absolute. <br> **Default value:** `false`
| `customEvents`               | An array of `keyword`/`symbol`/`color` that will customize events based on keyword in title. <br> <br> `keyword` is a case-insensitive string that if present in event title will trigger the use of custom symbol and/or color for that event, `symbol` is the Font Awesome icon to use as symbol and `color` is the CSS color to use for the event. `keyword` and at least one of `symbol` and `color`is required. <br> <br> **Example:** `customEvents: [{keyword: 'Birthday', symbol: 'birthday-cake', color: 'Gold'}]`
| `limitDays`                  | If this property is set to a value greater than zero, the number of unique days displayed will be limited to `limitDays` days. <br><br> **Default value:** `0` (no limit)
| `hideTime`                  | If this property is set to true the time portion on relative times will be hidden.<br><br> **Default value:** `false`

### Calendar configuration

The `calendars` property contains an array of the configured calendars.
The `colored` property gives the option for an individual color for each calendar.
The `coloredSymbolOnly` property will apply color to the symbol only, not the whole line. This is only applicable when `colored` is also enabled.

#### Default value:

````javascript
config: {
	colored: false,
	coloredSymbolOnly: false,
	calendars: [
		{
			url: 'https://www.calendarlabs.com/templates/ical/US-Holidays.ics',
			symbol: 'calendar',
			auth: {
			    user: 'username',
			    pass: 'superstrongpassword',
			    method: 'basic'
			}
		},
	],
}
````

#### Calendar configuration options:

| Option                | Description
| --------------------- | -----------
| `url`	                | The url of the calendar .ical. This property is required. <br><br> **Possible values:** Any public accessible .ical calendar.
| `symbol`              | The symbol to show in front of an event. This property is optional. <br><br> **Possible values:** See [Font Awesome](https://fontawesome.io/icons/) website. To have multiple symbols you can define them in an array e.g. `["calendar", "plane"]`
| `color`               | The font color of an event from this calendar. This property should be set if the config is set to colored: true. <br><br> **Possible values:** HEX, RGB or RGBA values (#efefef, rgb(242,242,242), rgba(242,242,242,0.5)).
| `repeatingCountTitle`	| The count title for yearly repeating events in this calendar.  <br><br> **Example:** `'Birthday'`
| `maximumEntries`      | The maximum number of events shown.  Overrides global setting. **Possible values:** `0` - `100`
| `maximumNumberOfDays` | The maximum number of days in the future.  Overrides global setting
| `name`                | The name of the calendar.  Included in event broadcasts as `calendarName`.
| `auth`                | The object containing options for authentication against the calendar.
| `symbolClass`         | Add a class to the cell of symbol.
| `titleClass`          | Add a class to the title's cell.
| `timeClass`           | Add a class to the time's cell.
| `broadcastPastEvents` | Whether to include past events from this calendar.  Overrides global setting

#### Calendar authentication options:

| Option                | Description
| --------------------- | -----------
| `user`                | The username for HTTP authentication.
| `pass`                | The password for HTTP authentication. (If you use Bearer authentication, this should be your BearerToken.)
| `method`              | Which authentication method should be used. HTTP Basic, Digest and Bearer authentication methods are supported. Basic authentication is used by default if this option is omitted. **Possible values:** `digest`, `basic`, `bearer` **Default value:** `basic`


## Syncing your Microsoft, Google and Apple calendars

To be able to use your calendar with Microsoft Outlook, Google Calendar and Apple iCal calendars, 
you need to either add each, individually or find a way to sync them into one. There are several 
free and non-free software that can help you do this.

For example, in [this forum thread](https://forum.magicmirror.builders/topic/5327/sync-private-icloud-calendar-with-magicmirror/50?page=1) are instructions how to sync with `iCal`. 

### Two-way Syncing

Here are some various projects that can be used to sync your calendars into one. 

* https://github.com/phw198/OutlookGoogleCalendarSync
* https://github.com/Dashbrd/CalendarSyncplus
* https://www.sync2.com/Download.aspx
* https://www.pppindia.com/calendar-sync/index.html
* https://www.fieldstonsoftware.com/software/gsyncit5/Download.aspx
* https://tools.google.com/dlpage/gappssync
* https://www.lifewire.com/how-to-sync-google-calendar-outlook-and-iphone-calendar-1172188
* https://www.makeuseof.com/tag/how-to-sync-microsoft-outlook-with-google-calendar/

### Office 365 Calendar Support

Office 365 calendars create date formats that are incompatible with MM2.
Here are the instructions to fix it:

1. Import your Office 365 calendar into a Google Calendar. This will take care of all the previous events of your calendar.
2. Go to [Microsoft Flow](https://flow.microsoft.com) and setup a Flow trigger that will create a new event in your Google Calendar whenever an event in Office 365 is created. [Here is a guide to help with this task.](https://shift.newco.co/sync-your-calendars-using-microsoft-flow-and-yes-google-calendar-works-too-a28be5a604dd)
3. Go to Google Calendar and create a private address to use in the calendar module for your Magic Mirror.

This trigger will run every 5 minutes. Make sure to give it time after you create a new event in Office 365 to appear in Google Calendar. Past events will NOT be created using Flow; to do this, follow step 1 to import your calendar into Google Calendar.
