![](../../../misc/attachments/Notion%20公式实践%20——%20日历、进度条-20220928.png)

```text
BOM: dateSubtract(now(), date(now()) - 1, "days")
EOM: dateSubtract(dateAdd(now(), 1, "months"), date(now()), "days")
BOY: dateSubtract(dateSubtract(now(), month(now()), "months"), date(now()) - 1, "days")
EOY: dateAdd(dateSubtract(dateAdd(now(), 1, "years"), month(now()) + 1, "months"), 31 - date(now()), "days")
Day of year: dateBetween(now(), prop("BOY"), "days")
Day of week: if(day(now()) == 0, 7, day(now()))
Week: ceil((dateBetween(now(), prop("BOY"), "days") + 1 - prop("Day of week")) / 7) + 1
Weeks: ceil((dateBetween(now(), prop("BOY"), "days") + 1 - prop("Day of week")) / 7) + 1
CountDown Today: format(23 - hour(now())) + " 小时 " + format(60 - minute(now())) + " 分钟"
%Today: round(hour(now()) / 24 * 10000) / 100
%Week: round(if(day(now()) == 0, 7, day(now())) / 7 * 10000) / 100
%Month: round(date(now()) / date(prop("EOM")) * 10000) / 100
%Year: round((dateBetween(now(), prop("BOY"), "days") + 1) / (dateBetween(prop("EOY"), prop("BOY"), "days") + 1) * 10000) / 100
Calendar: slice("00 00 00 00 00 00 00 ", 0, prop("_Offset") * 3) + slice("01 02 03 04 05 06 07 08 09 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 ", 0, (date(now()) - 1) * 3) + "🚩 " + slice("01 02 03 04 05 06 07 08 09 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 ", date(now()) * 3, date(prop("EOM")) * 3)
_Offset: if(day(prop("BOM")) == 0, 7, day(prop("BOM"))) - 1
```
