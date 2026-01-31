# Useful DAX Expressions

### Calendar
```sql
Date = ADDCOLUMNS(
    CALENDARAUTO(),
    "Year", YEAR([Date]),
    "Month", FORMAT([Date], "mmm"),
    "Month Number", MONTH([Date]),
    "Weekday", FORMAT([Date], "ddd"),
    "Day", DAY([Date]),
    "Quarter", "Q" & TRUNC((MONTH([Date]) - 1) / 3) + 1
)
```