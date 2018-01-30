# SharedStreets (Node.js & Javascript)

Node.js & Javascript implementation of [SharedStreets Reference System](https://github.com/sharedstreets/sharedstreets-ref-system).

## Install

**In Node.js**

```bash
$ npm install sharedstreets
```

**CommonJS**

```js
const sharedstreets = require('sharedstreets');
```

**Typescript**

```js
import * as sharedstreets from 'sharedstreets';
```

## In Browser

Download the latest [sharedstreets.js](https://unpkg.com/sharedstreets@latest) UMD file or use the link directly and include it in a script tag.

This will expose a global variable named **sharedstreets**.

**external url**

```html
<script src="https://unpkg.com/sharedstreets@latest" charset="utf-8"></script>
```

**local file**

```html
<script src="sharedstreets.js" charset="utf-8"></script>
```

## API

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

#### Table of Contents

-   [geometryId](#geometryid)
-   [intersectionId](#intersectionid)
-   [referenceId](#referenceid)
-   [lonlatsToCoords](#lonlatstocoords)
-   [generateHash](#generatehash)
-   [getRoadClassString](#getroadclassstring)
-   [getRoadClassNumber](#getroadclassnumber)
-   [getFormOfWayString](#getformofwaystring)
-   [getFormOfWayNumber](#getformofwaynumber)

### geometryId

Geometry Id

**Parameters**

-   `line` **(Feature&lt;LineString> | [Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)>>)** Line Geometry as a GeoJSON LineString or an Array of Positions Array&lt;&lt;longitude, latitude>>.

**Examples**

```javascript
const id = sharedstreets.geometryId([[110, 45], [115, 50], [120, 55]]);
id // => 'ce9c0ec1472c0a8bab3190ab075e9b21'
```

Returns **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** SharedStreets Geometry Id

### intersectionId

Intersection Id

**Parameters**

-   `pt` **(Feature&lt;Point> | [Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)>)** Point location reference as a GeoJSON Point or an Array of numbers &lt;longitude, latitude>.

**Examples**

```javascript
const id = sharedstreets.intersectionId([110, 45]);
id // => '71f34691f182a467137b3d37265cb3b6'
```

Returns **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** SharedStreets Intersection Id

### referenceId

Reference Id

**Parameters**

-   `locationReferences` **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;LocationReference>** An Array of Location References.
-   `formOfWay` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Form Of Way

**Examples**

```javascript
const locationReferences = [
  sharedstreets.locationReference([-74.0048213, 40.7416415], {outboundBearing: 208, distanceToNextRef: 9279}),
  sharedstreets.locationReference([-74.0051265, 40.7408505], {inboundBearing: 188})
];
const formOfWay = 2; // => 'MultipleCarriageway'

const id = sharedstreets.referenceId(locationReferences, formOfWay);
id // => '???'
```

Returns **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** SharedStreets Reference Id

### lonlatsToCoords

Converts lonlats to GeoJSON LineString Coords

**Parameters**

-   `lonlats` **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)>** Single Array of paired latitude & longitudes

**Examples**

```javascript
const coords = lonlatsToCoords([110, 45, 120, 55]);
coords // => [[110, 45], [120, 55]]
```

Returns **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)>>** GeoJSON coordinate format

### generateHash

Generates Base16 Hash

**Parameters**

-   `message` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Message to hash

**Examples**

```javascript
const message = 'Intersection -74.00482177734375 40.741641998291016';
const hash = sharedstreets.generateHash(message);
hash // => '69f13f881649cb21ee3b359730790bb9'
```

Returns **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** SharedStreets Reference ID

### getRoadClassString

Get RoadClass from a Number to a String

**Parameters**

-   `value` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** Number value [between 0-8]

**Examples**

```javascript
sharedstreets.getRoadClassString(0); // => 'Motorway'
sharedstreets.getRoadClassString(5); // => 'Residential'
```

Returns **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Road Class

### getRoadClassNumber

Get RoadClass from a String to a Number

**Parameters**

-   `value` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** String value ['Motorway', 'Trunk', 'Primary', etc...]

**Examples**

```javascript
sharedstreets.getRoadClassNumber('Motorway'); // => 0
sharedstreets.getRoadClassNumber('Residential'); // => 5
```

Returns **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Road Class

### getFormOfWayString

Get FormOfWay from a Number to a String

**Parameters**

-   `value` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** Number value [between 0-7]

**Examples**

```javascript
sharedstreets.getFormOfWayString(0); // => 'Undefined'
sharedstreets.getFormOfWayString(5); // => 'TrafficSquare'
```

Returns **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Form of Way

### getFormOfWayNumber

Get FormOfWay from a String to a Number

**Parameters**

-   `value` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** String value [ex: 'Undefined', 'Motorway', etc...]

**Examples**

```javascript
sharedstreets.getFormOfWayNumber('Undefined'); // => 0
sharedstreets.getFormOfWayNumber('TrafficSquare'); // => 5
```

Returns **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** Form of Way
