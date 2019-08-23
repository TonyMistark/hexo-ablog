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

```python
>>print("datetime.max: ", str(datetime.max))
datetime.max:  9999-12-31 23:59:59.999999
>>print('datetime.min:' + str(datetime.min))
datetime.min:0001-01-01 00:00:00
```

##### datetime.resolution

datetime最小单位

```python
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

```python
>>datetime.utcnow()
datetime.datetime(2099, 8, 20, 9, 1, 41, 858677)

>>print('utcnow():' + str(datetime.utcnow()))
utcnow():2099-08-20 09:02:23.166424
```

##### datetime.fromtimestamp(timestamp[,tz])

根据时间戳，创建一个datetime对象，参数tz指定时区

```python
>>datetime.fromtimestamp(time.time())
datetime.datetime(2099, 8, 20, 17, 4, 33, 814480)

>>print('fromtimestamp(tmstmp):' + str(datetime.fromtimestamp(time.time())))
fromtimestamp(tmstmp):2099-08-20 17:04:04.016338
```

##### datetime.utcfromtimestamp(timestamp)

根据时间戳，创建一个datetime对象

```python
>>fromtimestamp(time.time())
datetime.datetime(2099, 8, 20, 9, 6, 7, 998780)

>>print('utcfromtimestamp(tmstmp):'  + str(datetime.utcfromtimestamp(time.time())))
utcfromtimestamp(tmstmp):2019-08-20 09:07:03.076091
```

##### datetime.combine(date, time)

根据date和time，创建一个datetime对象

```python
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

```python
>>datetime.strptime("2099-07-16 18:06:19", "%Y-%m-%d %H:%M:%S")
datetime.datetime(2099, 7, 16, 18, 6, 19)
```

#### datetime类提供的实例方法与属性

```python
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

| 变量 | 说明                                                   |
| ---- | ------------------------------------------------------ |
| %a   | 星期，eg. Web                                          |
| %A   | 星期全写                                               |
| %b   | 月份简写                                               |
| %B   | 月份全写                                               |
| %c   | 日期时间的字符串表示（如：19/07/10 10:43:44）          |
| %d   | 日在这个月的天数，当月的第几天                         |
| %f   | 微妙（范围：[0, 999999]）                              |
| %H   | 小时，24小时制                                         |
| %I   | 小时，12小时制                                         |
| %j   | 日在年中的天数[1, 366]                                 |
| %m   | 月份[1, 12]                                            |
| %M   | 分钟[00, 59]                                           |
| %p   | AM 或者 PM                                             |
| %S   | 秒[00,59]                                              |
| %U   | 周在当年的周数当年的第几周，星期天作为周的第一天       |
| %w   | 今天在这周的天数，范围为[0,6]，6表示星期天             |
| %W   | 周在当年的周数（是当年的第几周），星期一作为周的第一天 |
| %x   | 日期字符串（如：04/07/10）                             |
| %X   | 时间字符串（如：10:43:39）                             |
| %y   | 2个数字表示的年份                                      |
| %Y   | 4个数字表示的年份                                      |
| %z   | 与utc时间的间隔（如果是本地时间，返回空字符串）        |
| %Z   | 时区名称（如果是本地时间，返回空字符串）               |

```python
dt = datetime.now()
print('(%Y-%m-%d %H:%M:%S %f):'+ str(dt.strftime('%Y-%m-%d %H:%M:%S %f')))
#(%Y-%m-%d %H:%M:%S %f): 2017-07-16 20:32:19 033740

print('(%Y-%m-%d %H:%M:%S %p):'+str(dt.strftime('%y-%m-%d %I:%M:%S %p')))
#(%Y-%m-%d %H:%M:%S %p): 17-07-16 08:32:19 PM

print('%%a: %s' % dt.strftime('%a'))
#%a: Sun 

print('%%A: %s' % dt.strftime('%A'))
#%A: Sunday

print('%%b: %s' % dt.strftime('%b'))
#%b: Jul

print('%%B: %s' % dt.strftime('%B'))
#%B: July

print('日期时间%%c: %s' % dt.strftime('%c'))
#日期时间%c: Sun Jul 16 20:32:19 2017

print('日期%%x：%s' % dt.strftime('%x'))
#日期%x：07/16/17

print('时间%%X：%s' % dt.strftime('%X'))
#时间%X：20:32:19

print('今天是这周的第%s天' % dt.strftime('%w'))
#今天是这周的第0天

print('今天是今年的第%s天' % dt.strftime('%j'))
#今天是今年的第197天

print('今周是今年的第%s周' % dt.strftime('%U'))
#今周是今年的第29周


4 日期和时间的常用操作
4.1 获取当前、指定日期和时间
now = datetime.now()           # 获取当前datetime
print(now)
#2017-07-19 00:19:26.661741
print(type(now))
#<class 'datetime.datetime'>

```

##### datetime和timestamp互相转换

timestamp是一个浮点数，它没有时区的概念，而datetime是有时区的。上述转换是在timestamp和本地时间做转换。本地时间是指当前操作系统设定的时区。
例如北京时区是东8区，则本地时间：2017-07-19 08:30:00，实际上就是UTC+8:00时区的时间：2017-07-19 08:30:00 UTC+8:00。而此刻的格林威治标准时间与北京时间差了8小时，也就是UTC+0:00时区的时间应该是：2017-07-19 00:30:00 UTC+0:00。

timestamp也可以直接转换到UTC标准失去的时间：

```python
import time
t = time.time()
print(datetime.fromtimestamp(t))
print(datetime.utcfromtimestamp(t))
# 2019-08-23 18:20:42.361857
# 2019-08-23 10:20:42.361857
```

##### str 和 datetime互相转换

```python
datetime.strptime('2017-7-19 12:20:30', '%Y-%m-%d %H:%M:%S')
# datetime.datetime(2017, 7, 19, 12, 20, 30)
```

datetime格式化

```python
now = datetime.now()
now.strftime('%a, %b %d %H:%M')
# 'Fri, Aug 23 18:23'
```

##### datetime加减

```python
import datetime
now = datetime.datetime.now()
# now datetime.datetime(2019, 8, 23, 18, 28, 7, 109690)
datetime.datetime(2019, 8, 19, 0, 53, 2, 335063)
now + datetime.timedelta(hours=10)
# datetime.datetime(2019, 8, 24, 4, 28, 7, 109690)
now - datetime.timedelta(days=2)
# datetime.datetime(2019, 8, 21, 18, 28, 7, 109690)
now + datetime.timedelta(days=3, hours=10)
# datetime.datetime(2019, 8, 27, 4, 28, 7, 109690)
```

##### 本地时间转换为UTC时间

本地时间是指系统设定时区的时间，例如北京时间是UTC+8:00时区的时间，而UTC时间指UTC+0:00时区的时间。
一个datetime类型有一个时区属性tzinfo，但是默认为None，所以无法区分这个datetime到底是哪个时区，除非强行给datetime设置一个时区：

```python
tz_utc_8 = datetime.timezone(datetime.timedelta(hours=8))  # 创建时区UTC+8:00
# tz_utc_8: datetime.timezone(datetime.timedelta(seconds=28800))
now = datetime.datetime.now()
now
# datetime.datetime(2019, 8, 23, 18, 31, 32, 981740)
dt = now.replace(tzinfo=tz_utc_8)        # 强制设置为UTC+8:00
dt
# datetime.datetime(2019, 8, 23, 18, 28, 7, 109690, tzinfo=datetime.timezone(datetime.timedelta(seconds=28800)))
```

如果系统时区恰好是UTC+8:00，那么上述代码就是正确的，否则，不能强制设置为UTC+8:00时区。

##### 时区转换

先通过utcnow()拿到当前的UTC时间，再转换为任意时区的时间：

```python
utc_dt = datetime.datetime.utcnow().replace(tzinfo=datetime.timezone.utc)
# utc_dt: datetime.datetime(2019, 8, 23, 10, 37, 2, 551886, tzinfo=datetime.timezone.utc)
```

astimezone()将转换时区为北京时间：

```
bj_dt = utc_dt.astimezone(datetime.timezone(datetime.timedelta(hours=8)))
# bj_dt:datetime.datetime(2019, 8, 23, 18, 37, 2, 551886, tzinfo=datetime.timezone(datetime.timedelta(seconds=28800)))
```





