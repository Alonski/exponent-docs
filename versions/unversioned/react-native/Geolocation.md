---
title: Geolocation
category: Facebook API
---
<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

## 

Copyright (c) 2015-present, Facebook, Inc.
All rights reserved.

This source code is licensed under the BSD-style license found in the
LICENSE file in the root directory of this source tree. An additional grant
of patent rights can be found in the PATENTS file in the same directory.

## Geolocation

The Geolocation API extends the web spec:
<https://developer.mozilla.org/en-US/docs/Web/API/Geolocation>

As a browser polyfill, this API is available through the `navigator.geolocation`
global - you do not need to `import` it.

### Configuration and Permissions

<div class="banner-crna-ejected">
  <h3>Projects with Native Code Only</h3>
  <p>
    This section only applies to projects made with <code>react-native init</code>
    or to those made with Create React Native App which have since ejected. For
    more information about ejecting, please see
    the <a href="https://github.com/react-community/create-react-native-app/blob/master/EJECTING.md" target="_blank">guide</a> on
    the Create React Native App repository.
  </p>
</div>

#### iOS

You need to include the `NSLocationWhenInUseUsageDescription` key
in Info.plist to enable geolocation when using the app. Geolocation is
enabled by default when you create a project with `react-native init`.

In order to enable geolocation in the background, you need to include the
'NSLocationAlwaysUsageDescription' key in Info.plist and add location as
a background mode in the 'Capabilities' tab in Xcode.

#### Android

To request access to location, you need to add the following line to your
app's `AndroidManifest.xml`:

`<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />`

Android API >= 18 Positions will also contain a `mocked` boolean to indicate if position
was created from a mock provider.