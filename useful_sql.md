# Useful SQL

### Turning Row Categories into Column Counts

**base_data**
| user_id | time_stamp          | action    |
|---------|--------------------|-----------|
| 3       | 2021-01-06 03:30:46 | timeout   |
| 3       | 2021-07-14 14:00:00 | timeout   |
| 7       | 2021-06-12 11:57:29 | confirmed |
| 7       | 2021-06-13 12:58:28 | confirmed |
| 7       | 2021-06-14 13:59:27 | confirmed |
| 2       | 2021-01-22 00:00:00 | confirmed |
| 2       | 2021-02-28 23:59:59 | timeout   |

**return**
| user_id | total | timeout | confirmed |
|---------|-------|---------|-----------|
| 2       | 2     | 1       | 1         |
| 3       | 2     | 2       | 0         |
| 7       | 3     | 0       | 3         |

```sql
SELECT
    user_id,
    COUNT(*) AS total,
    SUM(CASE WHEN [action] = 'timeout' THEN 1 ELSE 0) AS timeout,
    SUM(CASE WHEN [action] = 'confirmed' THEN 1 ELSE 0) AS confirmed
FROM base_data
GROUP BY user_id
ORDER BY user_id DESC;
```