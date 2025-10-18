# Data Model Explained

This project uses a star schema model to support scalable, performant analytics across 40,000+ cybersecurity incidents.

## Fact Table: `cybersecurity_attacks`

Contains all incident-level data:
- Timestamp, Source/Destination IPs
- Protocol, Packet Length, Attack Type
- Severity Level, Anomaly Scores
- Malware Indicators, Alerts, Geo-location
- Action Taken, Device Information

## Date Table

A calculated table created using DAX:

```DAX
Date = 
VAR MinDate = MINX(ALL('cybersecurity_attacks'), 'cybersecurity_attacks'[Timestamp])
VAR MaxDate = MAXX(ALL('cybersecurity_attacks'), 'cybersecurity_attacks'[Timestamp])
RETURN
ADDCOLUMNS(
  CALENDAR(MinDate, MaxDate),
  "Year", YEAR([Date]),
  "MonthNumber", MONTH([Date]),
  "MonthName", FORMAT([Date], "MMMM"),
  "YearMonth", FORMAT([Date],"yyyy-MM"),
  "Quarter", "Q" & FORMAT([Date],"Q"),
  "WeekOfYear", WEEKNUM([Date],1),
  "DayOfWeek", FORMAT([Date],"dddd"),
  "Hour", HOUR([Date])
)
