---
title: ProgressBarAndroid
category: Facebook Component
---
<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

## 

Copyright (c) 2015-present, Facebook, Inc.
All rights reserved.

This source code is licensed under the BSD-style license found in the
LICENSE file in the root directory of this source tree. An additional grant
of patent rights can be found in the PATENTS file in the same directory.

## ProgressBarAndroid

React component that wraps the Android-only `ProgressBar`. This component is used to indicate
that the app is loading or there is some activity in the app.

Example:

    render: function() {
      var progressBar =
        <View style={styles.container}>
          <ProgressBar styleAttr="Inverse" />
        </View>;

      return (
        <MyLoadingComponent
          componentView={componentView}
          loadingView={progressBar}
          style={styles.loadingComponent}
        />
      );
    },

## styleAttr

Style of the ProgressBar. One of:

-   Horizontal
-   Normal (default)
-   Small
-   Large
-   Inverse
-   SmallInverse
-   LargeInverse

## indeterminate

If the progress bar will show indeterminate progress. Note that this
can only be false if styleAttr is Horizontal.

## progress

The progress value (between 0 and 1).

## color

Color of the progress bar.

## testID

Used to locate this view in end-to-end tests.