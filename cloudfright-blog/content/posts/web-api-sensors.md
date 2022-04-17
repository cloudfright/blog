---
title: "Charting mobile sensor data with JavaScript"
date: 2022-04-09T08:01:20+01:00
draft: true
summary: ""
cover: 
    image: 
    alt: ""

categories: ["coding"]
tags: []
series: []

params:
    ShowShareButtons: true
    ShowReadingTime: true

---

- Intro

As part of the work I'm doing in the [Neosensory Community Research Program](/posts/neosensory-community.md/), I wanted to explore motion sensor data from a mobile device to attempt to detect balance and gait. I wanted to chart the data in realtime so I could visualise the data  There are two ways of getting the data: 
- Write a native app, ideally cross-platform, with something like [Flutter](https://flutter.dev/multi-platform/web)
- Web-based application using JavaScript Web APIs

I chose the Web API approach for fast iteration and easy sharing with others in the team. [Web APIs](https://developer.mozilla.org/en-US/docs/Web/API) are built into modern browsers which we'll look at next.

## Web APIs

So what can you get with the Web APIs? Quite a lot it turns out! There are many APIs to access a device's hardware interfaces and filesystem, helpers to load content, store data and most interestingly, access a device's sensors.

A caveat: many of these API's are experimental and may have incomplete or differing implementations across browsers - so proceed with caution!

For accessing a mobile device's sensors, we have two options:

- [Sensor APIs](https://developer.mozilla.org/en-US/docs/Web/API/)Sensor_APIs
- [Device Motion Event](https://developer.mozilla.org/en-US/docs/Web/API/DeviceMotionEvent)

- [W3C spec](https://w3c.github.io/deviceorientation/#devicemotion)

The Sensor APIs offer access to: 
- AbsoluteOrientationSensor	
- Accelerometer	
- AmbientLightSensor	
- GravitySensor	
- Gyroscope	
- LinearAccelerationSensor
- Magnetometer
- RelativeOrientationSensor

[Browser compatibility](https://developer.mozilla.org/en-US/docs/Web/API/Sensor_APIs#browser_compatibility)

Device Motion Event offers:
- Acceleration 
- Acceleration including gravity (orientation)
- Rotation rate

[Browser compatibility](
https://developer.mozilla.org/en-US/docs/Web/API/DeviceMotionEvent#browser_compatibility)


At the time of writing, the *Device Motion Event* offers better browser compatibility, so let's explore that.

## Getting the mobile motion data

As it's an event, we can subscribe to it using an event listener. For data privacy reasons, a number of devices (notably Apple devices) require user consent before the sensors and motion events can be accessed. 


Asking permission
```
function requestPermission() {
  if (typeof DeviceMotionEvent.requestPermission === 'function') {
    // Handle iOS 13+ devices.
    DeviceMotionEvent.requestPermission()
      .then((state) => {
        if (state === 'granted') {
          window.addEventListener('devicemotion', handleMotion);
        } else {
          console.error('Request to access the orientation was rejected');
        }
      })
      .catch(console.error);
  } else {
    // Handle regular non iOS 13+ devices.
    window.addEventListener('devicemotion', handleMotion);
  }
}
```
Hat tip to [trekhleb.dev](// https://trekhleb.dev/blog/2021/gyro-web/) and [web.dev](https://web.dev/generic-sensor/) for inspiration and reference. 

## Exploring the data

So now we have requested permissions, let's explore the the data returned from the motion event.

```
function handleMotion(event) {
    ...
}
```

The DeviceMotionEvent object looks like this:

```
DeviceMotionEvent {
  isTrusted: true, 
  acceleration: {x: -0.016416461668629197, y: -0.008223821129091084, z: 0.03818447696566581},
  accelerationIncludingGravity: {x: 0.03576176159707829, y: -0.26739436074271794, z: -9.764901108551024}, 
  rotationRate: {alpha: -0.1024065136597755, beta: 0.03143359110734988, gamma: 0.0017918174194308646}, 
  interval: 0.01666666753590107
} 

```
### Acceleration

[show diagram of axes]
![something](/web-api-sensors/acceleration-sensor.jpg)

### Acceleration Including Gravity 

If we subtract the acceleration value, we're left with the orientation 

[show diagram of axes]
![something](/web-api-sensors/gravity-sensor.jpg)

### Rotation Rate

[show diagram of axes]

![something](/web-api-sensors/rotation-rate-sensors.jpg)

Interval - the relative time since the last measurement.



## Charting the data

 Now we have device motion data, how can we chart it in real time?

I came across a great library called [smoothie.js](http://smoothiecharts.org/). It's simple to set up and is easy to configure / customise.

I needed three real time charts with each axis plotted in a different colour 
- Rotation rate 
- Acceleration 
- Device orientation 


Initialising the charts
```
var rotationRateSeries1 = new TimeSeries();
var rotationRateSeries2 = new TimeSeries();
var rotationRateSeries3 = new TimeSeries();

var accelerationSeries1 = new TimeSeries();
var accelerationSeries2 = new TimeSeries();
var accelerationSeries3 = new TimeSeries();

var orientationSeries1 = new TimeSeries();
var orientationSeries2 = new TimeSeries();
var orientationSeries3 = new TimeSeries();

function createTimeline() {

  var rotationRateChart = new SmoothieChart({ responsive: true, scrollBackwards: false });
  rotationRateChart.addTimeSeries(rotationRateSeries1, { strokeStyle: 'rgba(255, 0, 0, 1)', fillStyle: 'rgba(255, 0, 0, 0.2)', lineWidth: 3 });
  rotationRateChart.addTimeSeries(rotationRateSeries2, { strokeStyle: 'rgba(0, 255, 0, 1)', fillStyle: 'rgba(0, 255, 0, 0.2)', lineWidth: 3 });
  rotationRateChart.addTimeSeries(rotationRateSeries3, { strokeStyle: 'rgba(0, 0, 255, 1)', fillStyle: 'rgba(0, 0, 255, 0.2)', lineWidth: 3 });
  rotationRateChart.streamTo(document.getElementById("rotation-rate-chart"), 500);

  var accelerationChart = new SmoothieChart({ responsive: true, scrollBackwards: false });
  accelerationChart.addTimeSeries(accelerationSeries1, { strokeStyle: 'rgba(255, 0, 0, 1)', fillStyle: 'rgba(255, 0, 0, 0.2)', lineWidth: 3 });
  accelerationChart.addTimeSeries(accelerationSeries2, { strokeStyle: 'rgba(0, 255, 0, 1)', fillStyle: 'rgba(0, 255, 0, 0.2)', lineWidth: 3 });
  accelerationChart.addTimeSeries(accelerationSeries3, { strokeStyle: 'rgba(0, 0, 255, 1)', fillStyle: 'rgba(0, 0, 255, 0.2)', lineWidth: 3 });
  accelerationChart.streamTo(document.getElementById("acceleration-chart"), 500);

  var orientationChart = new SmoothieChart({ responsive: true, scrollBackwards: false });
  orientationChart.addTimeSeries(orientationSeries1, { strokeStyle: 'rgba(255, 0, 0, 1)', fillStyle: 'rgba(255, 0, 0, 0.2)', lineWidth: 3 });
  orientationChart.addTimeSeries(orientationSeries2, { strokeStyle: 'rgba(0, 255, 0, 1)', fillStyle: 'rgba(0, 255, 0, 0.2)', lineWidth: 3 });
  orientationChart.addTimeSeries(orientationSeries3, { strokeStyle: 'rgba(0, 0, 255, 1)', fillStyle: 'rgba(0, 0, 255, 0.2)', lineWidth: 3 });
  orientationChart.streamTo(document.getElementById("orientation-chart"), 500);

}

```

Displaying data

```
function handleMotion(event) {

  let now = Date.now();
  rotationRateSeries1.append(now, event.rotationRate.alpha);
  rotationRateSeries2.append(now, event.rotationRate.beta);
  rotationRateSeries3.append(now, event.rotationRate.gamma);

  accelerationSeries1.append(now, event.acceleration.x);
  accelerationSeries2.append(now, event.acceleration.y);
  accelerationSeries3.append(now, event.acceleration.z);

  orientationSeries1.append(now, event.accelerationIncludingGravity.x - event.acceleration.x);
  orientationSeries2.append(now, event.accelerationIncludingGravity.y - event.acceleration.y);
  orientationSeries3.append(now, event.accelerationIncludingGravity.z - event.acceleration.z);

  updateState(event);

}

```

You can see the completed project [here](https://github.com/cloudfright/motion-sensor-chart).


## Next steps

Offline analysis 
Posting data to Azure storage 
Machine Learning RNN








