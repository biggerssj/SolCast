### Changes

v2.2.4
HA 2022.4 fix for event log 'Detected integration that accesses the database without the database executor; Use homeassistant.components.recorder.get_instance(hass).async_add_executor_job() for faster database operations. Please report issue to the custom component author for solcast_solar using this method at custom_components/solcast_solar/__init__.py, line 332: event_s: list[int] = [event.event_data for event in events]'

v2.2.3
Sensor Forecast_Today and Forecast_Tomorrow now includes in the attributes 'hourly' values in watts for the whole 24hr period

v2.2.2
added solcast data for pv_estimate10 and pv_estimate90 to the DB for those that want to use it

v2.2.1
added HA configurate migration

V2.2.0
github issue #25 should be fixed now
added new config offset for TZ for those that are having the odd graph drawing problem
If you already have this integration installed edit each rooftop and enter "0" for the offset value to remove any config errors

v2.1.8
possible fix for github issue #25

v2.1.7
added changes needed for HA 2021.12

v2.1.5
learnt some new ha api functions to make things nicer
move the forecast graph over by 30min. looks better now
some code clean up.. less messy

v2.1.4
got removed.. buggy

v2.1.3
forecast values for today and remaining today where not correct after the first api fetch

v2.1.2
Fixed the not updating every hour problem
Added a new event 'solcast_log_debug_data' to log out debug information 


v2.1.1
Better databasing of data
new events to control deleting all data and fetching all data

Complete re write. v2.0 now 
- uses recorder to save forecast data, api count, last api call datetime

Make sure that the Recorder setting in the configuration.yaml file include the solcast integration items.. something like
```
recorder:
  purge_keep_days: 31
  include:
    entity_globs:
      - sensor.solcast*
```


### Changes

- Lots
- New service call function for update forecasts and delete all forecast data
- saves forecast data into the DB
- limit api calls setting
- much much more

### Polling Imformation

Solcast has a 50 API poll limit per day.

You can set the total number of api polls for each day in the integration settings
You can also use the service items to call updates manually or using an automation or script
