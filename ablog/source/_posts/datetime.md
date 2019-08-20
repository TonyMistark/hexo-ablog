---
layout: post
title:  "python datetime class"
date:   2019-01-12 22:32:40 +0800
categories: Python
---

datetime 类是python处理日期和时间的标准库。

#### datetime类定义的类属性与方法

##### datetime.min and datetime.max

datetime所能表示的最小值和最大值。

```
>>print("datetime.max: ", str(datetime.max))
datetime.max:  9999-12-31 23:59:59.999999
>>print('datetime.min:' + str(datetime.min))
datetime.min:0001-01-01 00:00:00
```

##### datetime.resolution

datetime最小单位

```
>>print('datetime.resolution:' + str(datetime.resolution))
datetime.resolution:0:00:00.000001
```

###### datetime.today()

返回一个表示当前本地时间的datetime对象

```
>>datetime.today()
datetime.datetime(2099, 9, 20, 16, 59, 30, 599807)
```

##### datetime.utcnow()

返回一个当前UTC时间（世界标准时间）的datetime的对象。UTC时间与北京时间相差8小时。

```
>>datetime.utcnow()
datetime.datetime(2099, 8, 20, 9, 1, 41, 858677)

>>print('utcnow():' + str(datetime.utcnow()))
utcnow():2099-08-20 09:02:23.166424
```

##### datetime.fromtimestamp(timestamp[,tz])

根据时间戳，创建一个datetime对象，参数tz指定时区

```
>>datetime.fromtimestamp(time.time())
datetime.datetime(2099, 8, 20, 17, 4, 33, 814480)

>>print('fromtimestamp(tmstmp):' + str(datetime.fromtimestamp(time.time())))
fromtimestamp(tmstmp):2099-08-20 17:04:04.016338
```

##### datetime.utcfromtimestamp(timestamp)

根据时间戳，创建一个datetime对象

```
>>fromtimestamp(time.time())
datetime.datetime(2099, 8, 20, 9, 6, 7, 998780)

>>print('utcfromtimestamp(tmstmp):'  + str(datetime.utcfromtimestamp(time.time())))
utcfromtimestamp(tmstmp):2019-08-20 09:07:03.076091
```

##### datetime.combine(date, time)

根据date和time，创建一个datetime对象

```
>>from datetime import date, time
>>d = date(2099, 6, 12)
>>t = time(12, 04, 24)
>>datetime.combine(d, t)
datetime.datetime(2099, 6, 12, 12, 4, 24)

>>print('datetime.combine(date,time):' + str(datetime.combine(d,t)))
datetime.combine(date,time):2099-06-12 12:04:24
```

##### datetime.strptime(date_string, format)

将格式字符串转换为datetime对象

```
>>datetime.strptime("2099-07-16 18:06:19", "%Y-%m-%d %H:%M:%S")
datetime.datetime(2099, 7, 16, 18, 6, 19)
```

#### datetime类提供的实例方法与属性

```
dt = datetime.strptime("2099-07-16 19:14:36", "%Y-%m-%d %H:%M:%S")
print(dt.year)                  # 2099
print(dt.month)                 # 7
print(dt.day)                   # 16
print(dt.hour)                  # 19
print(dt.minute)                # 14
print(dt.second)                # 36
print(dt.microsecond)           # 0
print(dt.tzinfo)                # None
print(dt.date())                # 2017-07-16
print(dt.time())                # 19:14:36
print(dt.replace(year=2018))    # 2018-07-16 19:14:36
print(dt.weekday())             # 6
print(dt.isocalendar())         # (2017, 28, 7)

print(dt.timetuple())
#返回日期对应的time.struct_time对象(类似于time模块的time.localtime())
#time.struct_time(tm_year=2017, tm_mon=7, tm_mday=16, tm_hour=19, tm_min=14, tm_sec=36, tm_wday=6, tm_yday=197, tm_isdst=-1)

print(dt.utctimetuple())
#返回UTC日期对应的time.struct_time对象
#time.struct_time(tm_year=2017, tm_mon=7, tm_mday=16, tm_hour=19, tm_min=14, tm_sec=36, tm_wday=6, tm_yday=197, tm_isdst=0)

print(dt.toordinal()) 
#736526，返回日期对应的Gregorian Calendar日期
```

#### 格式字符串datetime.strftime(format)

| 变量 | 说明                                          |
| ---- | --------------------------------------------- |
| %a   | 星期，eg. Web                                 |
| %A   | 星期全写                                      |
| %b   | 月份简写                                      |
| %B   | 月份全写                                      |
| %c   | 日期时间的字符串表示（如：19/07/10 10:43:44） |
| %d   | 日在这个月的天数，当月的第几天                |
| %f   | 微妙（范围：[0, 999999]）                     |
| %H   | 小时，24小时制                                |
| %I   | 小时，12小时制                                |
| %j   | 日在年中的天数[1, 366]                        |
| %m   | 月份[1, 12]                                   |
| %M   |                                               |
|      |                                               |
|      |                                               |
|      |                                               |
|      |                                               |
|      |                                               |
|      |                                               |
|      |                                               |
|      |                                               |
|      |                                               |
|      |                                               |
|      |                                               |

