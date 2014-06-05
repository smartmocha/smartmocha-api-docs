---
title: Smart Mocha API Reference

language_tabs:
  - curl

toc_footers:
  - <a href='https://account.smartmocha.com'>Sign Up for a Developer Key</a>

includes:
  - errors

---

# Introduction

Welcome to the Smart Mocha API. Here you can get access to all of your devices, data, and notifications.

The Smart Mocha API is built around REST / JSON. We use the same API to power our dashboards and other services. We hope to see you build innovative applications around your devices and data.

All requests must be to our secure endpoint and we're currently at v0 of our API.

e.g. https://api.smartmocha.com/v0/:endpoint


# Authentication

Authenication is handled via API tokens and basic auth. You can manage your API tokens in your <a href='https://account.smartmocha.com'>account</a>.

In your terminal, you pass your credentials as such:

```shell
curl -u your-api-token: https://api.smartmocha.com/v0/:endpoint
```

# Devices

## Get All Devices

This endpoint retrieves all devices for your account.

### HTTP Request

`GET https://api.smartmocha.com/v0/devices`

```shell
curl -u your-api-token: https://api.smartmocha.com/v0/devices
```

> The above command returns JSON structured like this:

```json
{
  "count": 1,
  "data": [
    {
      "attached_devices": [
        "A6B2E93A15267DBF",
        "3AD97529EE51A8A4",
        "CCE29492A7044737"
      ],
      "created_at": "2014-05-02T18:54:09",
      "deployed": false,
      "description": null,
      "firmware_version": "1.0.0",
      "id": "D0A0D862CC766B7A",
      "last_seen": "2014-05-05T20:35:30",
      "location": null,
      "metrics": [
        {
          "id": "3a853a54-e0fc-4aa9-b1a8-82cfa6dbb783",
          "last_seen": "2014-05-05T13:35:30",
          "last_val": "8.61819792521705",
          "name": "Battery Voltage"
        },
        {
          "id": "115d1dae-ffc0-40cf-ade0-18e9da3b654a",
          "last_seen": "2014-05-05T13:35:30",
          "last_val": "12.285120019427794",
          "name": "External Voltage"
        }
      ],
      "name": null,
      "status": "online",
      "type": "SmartMocha Base Station",
      "updated_at": "2014-05-02T18:54:39"
    }
  ],
  "object": "list",
  "url": "/v0/devices"
}
```

## Get Device

This endpoint retrieves info about a specific device.

### HTTP Request

`GET https://api.smartmocha.com/v0/device/:device_id`

```shell
curl -u your-api-token: https://api.smartmocha.com/v0/device/D0A0D862CC766B7A
```

> The above command returns JSON structured like this:

```json
{
  "attached_devices": [
    "A6B2E93A15267DBF",
    "3AD97529EE51A8A4",
    "CCE29492A7044737"
  ],
  "created_at": "2014-05-02T18:54:09",
  "deployed": false,
  "description": null,
  "firmware_version": "1.0.0",
  "id": "D0A0D862CC766B7A",
  "last_seen": "2014-05-05T20:35:34",
  "location": null,
  "metrics": [
    {
      "id": "3a853a54-e0fc-4aa9-b1a8-82cfa6dbb783",
      "last_seen": "2014-05-05T13:35:34",
      "last_val": "4.941293067865106",
      "name": "Battery Voltage"
    },
    {
      "id": "115d1dae-ffc0-40cf-ade0-18e9da3b654a",
      "last_seen": "2014-05-05T13:35:34",
      "last_val": "12.487047065296252",
      "name": "External Voltage"
    }
  ],
  "name": null,
  "status": "online",
  "type": "SmartMocha Base Station",
  "updated_at": "2014-05-02T18:54:39"
}
```

## Update Device

This endpoint updates info about a specific device.

### HTTP Request

`PUT https://api.smartmocha.com/v0/device/:device_id`

```shell
curl -u your-api-token: -H "Content-Type: application/json" -XPUT -d @update-device.json https://api.smartmocha.com/v0/device/D0A0D862CC766B7A
```

> Where `update-device.json` is structured like this:

```json
{
  "name": "awesome basestation",
  "description": "Pacific Building 5th Floor",
  "location": "520 SW Yamhill St, Portland, OR 97204"
}
```

> The above command returns JSON structured like this:

```json
{
  "attached_devices": [
    "A6B2E93A15267DBF",
    "3AD97529EE51A8A4",
    "CCE29492A7044737"
  ],
  "created_at": "2014-05-02T18:54:09",
  "deployed": false,
  "description": "Pacific Building 5th Floor",
  "firmware_version": "1.0.0",
  "id": "D0A0D862CC766B7A",
  "last_seen": "2014-05-06T15:30:24",
  "location": "520 SW Yamhill St, Portland, OR 97204",
  "metrics": [
    {
      "id": "3a853a54-e0fc-4aa9-b1a8-82cfa6dbb783",
      "last_seen": "2014-05-06T08:30:24",
      "last_val": "7.923217610472991",
      "name": "Battery Voltage"
    },
    {
      "id": "115d1dae-ffc0-40cf-ade0-18e9da3b654a",
      "last_seen": "2014-05-06T08:30:24",
      "last_val": "49.934818435763376",
      "name": "External Voltage"
    }
  ],
  "name": "awesome basestation",
  "status": "offline",
  "type": "SmartMocha Base Station",
  "updated_at": "2014-05-06T20:22:29"
}
```

# Sensor Data

At the moment, all sensor data is attached to the device. Soon you will be able to query sensor data across devices.

### HTTP Request

`GET https://api.smartmocha.com/v0/device/:device_id/data`

## Get sensor data

```shell
curl -u your-api-token: 'https://api.smartmocha.com/v0/device/D0A0D862CC766B7A/data?start=2014-05-01&rollup=1h-avg'
```

> The above command returns JSON structured like this:

```json
{
  "end": "2014-05-06T20:36:27",
  "object": "query",
  "results": [
    {
      "data": {
        "1399322129": 26.650172630945843
      },
      "device": "D0A0D862CC766B7A",
      "metric": "Battery Voltage",
      "name": "awesome basestation",
      "ts": "115d1dae-ffc0-40cf-ade0-18e9da3b654a"
    },
    {
      "data": {
        "1399322129": 28.36407470703125
      },
      "device": "D0A0D862CC766B7A",
      "metric": "External Voltage",
      "name": "awesome basestation",
      "ts": "115d1dae-ffc0-40cf-ade0-18e9da3b654a"
    }
  ],
  "rollup": "1h-avg",
  "start": "2014-05-01T00:00:00"
}
```

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
rollup | none/required | see options below for rollup
start | none/required | query start time is required, see options below for date/time formats
end | now | see options below for data/time formats
arrays | none | if &arrays, data will be returned as JSON arrays versus objects
metric_id | none | a semicolon delimited list of metric ids specific to this device

### Rollup Examples

Example | Description
------- | -----------
1h-min | downsampled to 1 hour/min
1d-max | downsampled to 1 day/max
10m-avg | downstampled to 10 minute/average

### Rollup Operations

Operation | Description
--------- | -----------
min | returns the smallest value
max | returns the largest value
sum | returns the sum of all values
avg | returns the average value
dev | returns the standard deviation
rate | returns the rate of change between pairs of data points

### Date Formats

Dates are returned in ISO8601 format, though we gladly accept many other formats in the start and end fields,
including unix timestamps and relative times.

### Relative Times
You can use relative times for your start and end query parameters.

Example | Description
------- | -----------
1h-ago | one hour ago
2n-ago | two months ago
3y-ago | three years ago

### Time units

Time unit | Description
--------- | -----------
ms | milliseconds
s | seconds
m | minutes
h | hours
d | days
w | weeks
n | months
y | years

# Streaming Data

We're using <a href="http://en.wikipedia.org/wiki/Server-sent_events">server-sent events</a> for some of our
realtime streaming features. Please do not use this directly in javascript loaded in your browser, as
you will leak your API key.

### HTTP Request

`GET https://api.smartmocha.com/v0/device/:device_id/stream`

## Connect to device stream

```shell
curl -u your-api-token: http://api.smartmocha.dev:5000/v0/device/D0A0D862CC766B7A/stream
```

> The above command will return text/event-stream structured like this:

```json
data: {"device": "D0A0D862CC766B7A", "data": [[1399588748000, 78.40191068442397]], "metric": "Battery Voltage", "type": "data"}

data: {"device": "D0A0D862CC766B7A", "data": [[1399588748000, 73.46231559449963]], "metric": "External Voltage", "type": "data"}

data: {"device": "D0A0D862CC766B7A", "data": [[1399588749000, 63.86665544710024]], "metric": "Battery Voltage", "type": "data"}

data: {"device": "D0A0D862CC766B7A", "data": [[1399588749000, 35.487668612821295]], "metric": "External Voltage", "type": "data"
```

