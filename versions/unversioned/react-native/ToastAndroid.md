---
title: ToastAndroid
category: Facebook API
---
<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

## 

Copyright (c) 2015-present, Facebook, Inc.
All rights reserved.

This source code is licensed under the BSD-style license found in the
LICENSE file in the root directory of this source tree. An additional grant
of patent rights can be found in the PATENTS file in the same directory.

## ToastAndroid

This exposes the native ToastAndroid module as a JS module. This has a function 'show'
which takes the following parameters:

1.  String message: A string with the text to toast
2.  int duration: The duration of the toast. May be ToastAndroid.SHORT or ToastAndroid.LONG

There is also a function `showWithGravity` to specify the layout gravity. May be
ToastAndroid.TOP, ToastAndroid.BOTTOM, ToastAndroid.CENTER.

Basic usage:

```javascript
ToastAndroid.show('A pikachu appeared nearby !', ToastAndroid.SHORT);
ToastAndroid.showWithGravity('All Your Base Are Belong To Us', ToastAndroid.SHORT, ToastAndroid.CENTER);
```