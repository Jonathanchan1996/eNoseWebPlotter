# eNoseWebPlotter
### Author: Jonathan
### Date: 2025-07-16


System Architecture
```
Backend -> mqtt broker -> Frontend 
```

Host:Plot 
```
mqtt-dashboard.com:8884
```


Topic
```
hkust/ece/enose/{uid}
```


ChatGPT chat
```
I would like to build a realtime sensor plotter tools. The sensor is a 3x3 matrix in 1Hz. There is the structure `Backend -> mqtt broker -> Frontend`. mqtt broken use `mqtt-dashboard.com:8884`. But for this stage, lets start from simulating random data. First, use `html` and `js` to make a Backend simulator to generate 9 random sensor data (`0-4095`) as the sensor is 3x3. the web GUI has 5 buttons, each of them will control the generated data differently. And it will send the data timestamp and sensor data via mqtt broker. The propsed mqtt message is `{"ts": 1752658312, 
    "sensor": {
        "data":[0,10,20,30,40,50,60,70,80]
    },}`
 the topic is `hkust/ece/enose/{uid}` where default `{uid}` is `1`. Secondly, as for the Frontend, The GUI has: company logo, raw data (3x3 color scale matrix), time series of that 9 data.

In short, all the app there are `html`. 
```

Topic approach 

```
{path} = hkust/ece/enose/{uid}
```

| Topic | Type | Description |
| --- | --- | --- |
| {path}/timestamp | int | timestamp of each data |
| {path}/sensor/px | array of int | pixel of the sensor |
| {path}/sensor/range | array of int | range of the sensor |
| {path}/sensor/rawdata | array of int | raw data of the sensor |
| {path}/classify/method | string | classification method |
| {path}/classify/dimension | int | classification dimension |
| {path}/classify/point | array of int | classification point |