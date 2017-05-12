---
title: Picker
category: Facebook Component
---
<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

## 

Copyright (c) 2015-present, Facebook, Inc.
All rights reserved.

This source code is licensed under the BSD-style license found in the
LICENSE file in the root directory of this source tree. An additional grant
of patent rights can be found in the PATENTS file in the same directory.

## PickerItem

**Extends React.Component**

Individual selectable item in a Picker.

## label

Text to display for this item.

## value

The value to be passed to picker's `onValueChange` callback when
this item is selected. Can be a string or an integer.

## color

Color of this item's text.

## testID

Used to locate the item in end-to-end tests.

## testID

Used to locate this view in end-to-end tests.

## Picker

**Extends React.Component**

Renders the native picker component on iOS and Android. Example:

    <Picker
      selectedValue={this.state.language}
      onValueChange={(itemValue, itemIndex) => this.setState({language: itemValue})}>
      <Picker.Item label="Java" value="java" />
      <Picker.Item label="JavaScript" value="js" />
    </Picker>

### MODE_DIALOG

On Android, display the options in a dialog.

### MODE_DROPDOWN

On Android, display the options in a dropdown (this is the default).

## selectedValue

Value matching value of one of the items. Can be a string or an integer.

## onValueChange

Callback for when an item is selected. This is called with the following parameters:

-   `itemValue`: the `value` prop of the item that was selected
-   `itemPosition`: the index of the selected item in this picker

## enabled

If set to false, the picker will be disabled, i.e. the user will not be able to make a
selection.

## mode

On Android, specifies how to display the selection items when the user taps on the picker:

-   'dialog': Show a modal dialog. This is the default.
-   'dropdown': Shows a dropdown anchored to the picker view

## itemStyle

Style to apply to each of the item labels.

## prompt

Prompt string for this picker, used on Android in dialog mode as the title of the dialog.