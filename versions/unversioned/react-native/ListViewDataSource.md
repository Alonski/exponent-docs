---
title: ListViewDataSource
category: Facebook API
---
<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

## 

Copyright (c) 2015-present, Facebook, Inc.
All rights reserved.

This source code is licensed under the BSD-style license found in the
LICENSE file in the root directory of this source tree. An additional grant
of patent rights can be found in the PATENTS file in the same directory.

## ListViewDataSource

Provides efficient data processing and access to the
`ListView` component.  A `ListViewDataSource` is created with functions for
extracting data from the input blob, and comparing elements (with default
implementations for convenience).  The input blob can be as simple as an
array of strings, or an object with rows nested inside section objects.

To update the data in the datasource, use `cloneWithRows` (or
`cloneWithRowsAndSections` if you care about sections).  The data in the
data source is immutable, so you can't modify it directly.  The clone methods
suck in the new data and compute a diff for each row so ListView knows
whether to re-render it or not.

In this example, a component receives data in chunks, handled by
`_onDataArrived`, which concats the new data onto the old data and updates the
data source.  We use `concat` to create a new array - mutating `this._data`,
e.g. with `this._data.push(newRowData)`, would be an error. `_rowHasChanged`
understands the shape of the row data and knows how to efficiently compare
it.

    getInitialState: function() {
      var ds = new ListViewDataSource({rowHasChanged: this._rowHasChanged});
      return {ds};
    },
    _onDataArrived(newData) {
      this._data = this._data.concat(newData);
      this.setState({
        ds: this.state.ds.cloneWithRows(this._data)
      });
    }

**Parameters**

-   `params` **ParamType** 

### constructor

You can provide custom extraction and `hasChanged` functions for section
headers and rows.  If absent, data will be extracted with the
`defaultGetRowData` and `defaultGetSectionHeaderData` functions.

The default extractor expects data of one of the following forms:

     { sectionID_1: { rowID_1: <rowData1>, ... }, ... }

   or

     { sectionID_1: [ <rowData1>, <rowData2>, ... ], ... }

   or

     [ [ <rowData1>, <rowData2>, ... ], ... ]

The constructor takes in a params argument that can contain any of the
following:

-   getRowData(dataBlob, sectionID, rowID);
-   getSectionHeaderData(dataBlob, sectionID);
-   rowHasChanged(prevRowData, nextRowData);
-   sectionHeaderHasChanged(prevSectionData, nextSectionData);

**Parameters**

-   `params` **ParamType** 

### cloneWithRows

Clones this `ListViewDataSource` with the specified `dataBlob` and
`rowIdentities`. The `dataBlob` is just an arbitrary blob of data. At
construction an extractor to get the interesting information was defined
(or the default was used).

The `rowIdentities` is a 2D array of identifiers for rows.
ie. \[['a1', 'a2'], ['b1', 'b2', 'b3'], ...].  If not provided, it's
assumed that the keys of the section data are the row identities.

Note: This function does NOT clone the data in this data source. It simply
passes the functions defined at construction to a new data source with
the data specified. If you wish to maintain the existing data you must
handle merging of old and new data separately and then pass that into
this function as the `dataBlob`.

**Parameters**

-   `dataBlob` **($ReadOnlyArray&lt;any> | {})** 
-   `rowIdentities` **$ReadOnlyArray&lt;[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)>?** 

Returns **[ListViewDataSource](#listviewdatasource)** 

### cloneWithRowsAndSections

This performs the same function as the `cloneWithRows` function but here
you also specify what your `sectionIdentities` are. If you don't care
about sections you should safely be able to use `cloneWithRows`.

`sectionIdentities` is an array of identifiers for  sections.
ie. ['s1', 's2', ...].  If not provided, it's assumed that the
keys of dataBlob are the section identities.

Note: this returns a new object!

**Parameters**

-   `dataBlob` **any** 
-   `sectionIdentities` **[Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)>?** 
-   `rowIdentities` **[Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;[Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)>>?** 

Returns **[ListViewDataSource](#listviewdatasource)** 

### rowShouldUpdate

Returns if the row is dirtied and needs to be rerendered

**Parameters**

-   `sectionIndex` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** 
-   `rowIndex` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** 

Returns **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** 

### getRowData

Gets the data required to render the row.

**Parameters**

-   `sectionIndex` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** 
-   `rowIndex` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** 

Returns **any** 

### getRowIDForFlatIndex

Gets the rowID at index provided if the dataSource arrays were flattened,
or null of out of range indexes.

**Parameters**

-   `index` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** 

Returns **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?** 

### getSectionIDForFlatIndex

Gets the sectionID at index provided if the dataSource arrays were flattened,
or null for out of range indexes.

**Parameters**

-   `index` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** 

Returns **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)?** 

### getSectionLengths

Returns an array containing the number of rows in each section

Returns **[Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)>** 

### sectionHeaderShouldUpdate

Returns if the section header is dirtied and needs to be rerendered

**Parameters**

-   `sectionIndex` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** 

Returns **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** 

### getSectionHeaderData

Gets the data required to render the section header

**Parameters**

-   `sectionIndex` **[number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)** 

Returns **any** 

### \_getRowData

Private members and methods.

Type: any