

# react-native-updated-proximity


This project is based on the react-native-proximity library. So unfortunately the react-native-proximity library wasn't updated for a long time and the methods, versions were deprecated. The react-native-updated-proximity library has all fixes and you can easily use it in you react-native applications.

## A React Native wrapper that provides access to the state of the proximity sensor for iOS and Android and has been fixed for iOS > 13 and react Native > 0.60.x versions :)

![](https://github.com/williambout/react-native-proximity/raw/master/demo.gif)

*Usage of react-native-proximity and scrollview.*

## Getting Started

- Install the library 
```shell
npm install --save react-native-updated-proximity
```

## Usage

First import the library

```javascript
import Proximity from 'react-native-updated-proximity';
```

### addListener(callback)
### removeListener(callback)

The callback function returns an object with *proximity* and *distance* properties. If *proximity* is true, it means the device is close to an physical object. *distance* is only supported in Android.


Use this way:

```javascript
import {useEffect, useState} from 'react';

const [isNear, setIsNear] = useState(false);

const callback = ({ proximity }) => setIsNear(!!proximity);

useEffect(() => {
  Proximity.addListener(proximityListener);
  return  () => removeListener(calback)
}, []);
```

Or if you're writing in TypeScript first you have to create a file for Proximity types:

```javascript
// create this file wherewhere you want in your application
// name the files as react-native-updated-proximity.d.ts
// add this code in your file and then you can use that in your component

declare module 'react-native-proximity' {
    const proximity: {
        addListener(callback: (data: { Proximity: boolean }) => void): void;
        removeListener(callback: (data: { Proximity: boolean }) => void): void;
    };
    export default proximity;
}
```
