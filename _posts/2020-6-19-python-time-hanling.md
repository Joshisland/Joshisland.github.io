# Time string to epoch
## "1 Jan 1970 00:00:00" -> 0: int

convert to struct_time using time.strptime and then convert to epoch

```
>>> import calendar, time
>>> s="1 Jan 1970 00:00:00"
>>> time.strptime(s, "%d %b %Y %H:%M:%S")
time.struct_time(tm_year=1970, tm_mon=1, tm_mday=1, tm_hour=0, tm_min=0, tm_sec=0, tm_wday=3, tm_yday=1, tm_isdst=-1)
>>> calendar.timegm(time.strptime(s, "%d %b %Y %H:%M:%S"))
0
```

## "2020-06-18T07:52:45.000000Z" -> 1592466765: epoch

another example

```
>>> s = "2020-06-18T07:52:45.000000Z"
>>> calendar.timegm(time.strptime(s.split('.')[0], "%Y-%m-%dT%H:%M:%S"))
1592466765
```

## From python doc
| From | To | Use |
| ---- | -- | --- |
| seconds since the epoch | struct_time in UTC | gmtime() |
| seconds since the epoch | struct_time in local time | localtime() |
| struct_time in UTC | seconds since the epoch | calendar.timegm() |
| struct_time in local time | seconds since the epoch | mktime() |

## Reference
[1] Python dev version time doc: https://docs.python.org/dev/library/time.htmlmodule-time