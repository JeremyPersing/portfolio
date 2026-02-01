# Useful DAX Expressions

### Date Table
After creating,
- Mark table as date table
- sort `Month` by `Month Number`
- sort `Weekday` by `Weekday Number`

```sql
Date = ADDCOLUMNS(
    CALENDARAUTO(),
    "Year", YEAR([Date]),
    "Month", FORMAT([Date], "mmm"),
    "Month Number", MONTH([Date]),
    "Weekday", FORMAT([Date], "ddd"),
    "Weekday Number", WEEKDAY([Date]),
    "Day", DAY([Date]),
    "Quarter", "Q" & TRUNC((MONTH([Date]) - 1) / 3) + 1
)
```
or

```sql
Date = ADDCOLUMNS(
    CALENDAR(MIN(Sales[Sale Date]), MAX(Sales[Sale Date])),
    "Year", YEAR([Date]),
    "Month", FORMAT([Date], "mmm"),
    "Month Number", MONTH([Date]),
    "Weekday", FORMAT([Date], "ddd"),
    "Weekday Number", WEEKDAY([Date]),
    "Day", DAY([Date]),
    "Quarter", "Q" & TRUNC((MONTH([Date]) - 1) / 3) + 1
)
```