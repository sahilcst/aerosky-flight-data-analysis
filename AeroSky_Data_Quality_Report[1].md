# AeroSky – Data Quality Report

## 1. What I checked

I first looked at the dataset to understand the columns, data types, missing values, duplicate rows and the range of the numeric columns.

The main things I found were:
- Some columns had missing values.
- There were duplicate rows.
- Some airline names were written in different ways.
- Some latitude and longitude values were outside the normal range.
- Some numeric values such as altitude, ground speed and vertical speed had unusual values.

I used these findings to decide what needed to be cleaned.

## 2. Missing values

I checked missing values using:

```python
df.isnull().sum()
```

Missing values were present in fields such as:
- registration
- airline
- aircraft_type
- origin
- destination
- latitude
- longitude
- altitude_ft
- ground_speed_kts
- vertical_speed_fpm

I did not replace all missing values with 0 because a missing value does not always mean that the real value was zero.

For latitude and longitude, after cleaning, some values were still missing. There were 269 missing latitude values and 269 missing longitude values.

## 3. Duplicate rows

I checked duplicate rows using:

```python
df.duplicated().sum()
```

The duplicate rows were checked and they were actually repeated rows. They were removed during cleaning so that the same observation would not be counted more than once.

## 4. Airline names

I checked the values in the airline column using:

```python
df["airline"].value_counts(dropna=False)
```

There were some different versions of the same airline name, for example differences in capital letters.

These were standardized during cleaning so that the same airline would be counted as one airline.

## 5. Timestamp

I checked the first and last timestamps and converted the timestamp into a proper datetime format so that it could be used for time-based analysis.

After that, I was able to create:
- date
- hour
- day of week

for the time-series analysis.

## 6. Latitude and longitude

I checked whether latitude and longitude were within their valid ranges.

Latitude should be between -90 and +90.

Longitude should be between -180 and +180.

I found invalid coordinate values, for example latitude values of 95 and -95 and longitude values of 195 and -195.

These values are not valid geographic coordinates, so they were treated as invalid and handled during cleaning.

## 7. Altitude, ground speed and vertical speed

I used descriptive statistics to look at:
- altitude
- ground speed
- vertical speed

There were some unusual/extreme values.

I did not simply delete every extreme value because an unusual value is not automatically a wrong value. I treated these as values that may need further checking.

## 8. Problems found in the data

Based on the checks above, the main data-quality problems were:

1. Missing values in several columns.
2. Duplicate observations.
3. Inconsistent airline names.
4. Invalid latitude and longitude values.
5. Some unusual values in altitude, ground speed and vertical speed.

## 9. What I did because of these problems

- Removed duplicate observations.
- Standardized inconsistent airline names.
- Converted the timestamp to datetime.
- Handled invalid latitude and longitude values.
- Kept genuine missing values instead of filling them with random values.
- Checked unusual numeric values instead of automatically deleting them.

## 10. Limitations

This analysis is based only on the supplied flight-tracking data.

Some missing and unusual values still need domain knowledge to decide whether they are truly wrong or are caused by the source/tracking system.

I also did not complete a full tracking-continuity analysis or an airport-summary CSV, so these are not presented as completed results in this report.
