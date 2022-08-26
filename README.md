# Unique Building Identification (UBID)

**Website:** https://buildingid.pnnl.gov/

## Documentation

### Install

To complete this guide, [npm](https://www.npmjs.com/) is required.

Install the `pnnl-buildingid` package:
```bash
npm install pnnl-buildingid
```

### Uninstall

Use [npm](https://www.npmjs.com/) to uninstall the `pnnl-buildingid` package.
```bash
npm uninstall pnnl-buildingid
```

### Content Delivery Network

The `pnnl-buildingid` package and its dependency, the `openlocationcode` package, are also distributed via [cdnjs](https://cdnjs.com/libraries/pnnl-buildingid), and can be included directly in HTML documents.

#### Not Minified

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/openlocationcode/1.0.4/openlocationcode.js" integrity="sha512-l89EkrJBS8wnnRi58zAA9oj1Ok7h0twzXeAltaax8t1viFQ6zTyom41s+YdMUSnbjP/eC0P+mQOldVzvsrBn3A==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/pnnl-buildingid/1.0.3/pnnl-buildingid.js" integrity="sha512-Lff8arMmIctm9qPOG3jwtVaiefX/JADUZqWkr7ZDu2F9tweLtPtnhj7FFeKLXDseLGGUCq4QeyWjWgWovQ/abw==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
```

#### Minified

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/openlocationcode/1.0.4/openlocationcode.min.js" integrity="sha512-nNdmCJgFefLPn6W79uEUxH2n4+qbc0kJM8uBD8f7GlmusrQN9L13hpSBRxLHdLs+6oSDurcCuDlBXVKaz/hpcA==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/pnnl-buildingid/1.0.3/pnnl-buildingid.min.js" integrity="sha512-FVPTex/yDYrMDFymOsaQH4KpUt/FxnV73vABAiyy75nWgCrTCM87hol9UMyGwY9Uo1K1PtXsqXL96xXi4gxaiw==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
```

## Usage

The `pnnl-buildingid` package supports one usage:
* Application programming interface (API)

### The API

UBID codecs are encapsulated in separate modules:
* `UniqueBuildingIdentification.v3` (format: "C-n-e-s-w")

Modules export the same API:
* `decode(string) ~> UniqueBuildingIdentification.CodeArea`
* `encode(number, number, number, number, number, number, number) ~> string`
* `encodeCodeArea(UniqueBuildingIdentification.CodeArea) ~> string`
* `isValid(string) ~> boolean`

In the following example, a UBID code is decoded and then re-encoded:

```javascript
// Use the "C-n-e-s-w" format for UBID codes.
const UniqueBuildingIdentification = require('pnnl-buildingid');

// Initialize UBID code.
const code = '849VQJH6+95J-51-58-42-50';
console.log(code);

// Decode the UBID code.
const codeArea = UniqueBuildingIdentification.v3.decode(code);
console.log(codeArea);

// Resize the resulting UBID code area.
//
// The effect of this operation is that the height and width of the UBID code
// area are reduced by half an OLC code area.
const newCodeArea = codeArea.resize();
console.log(newCodeArea);

// Encode the new UBID code area.
const newCode = UniqueBuildingIdentification.v3.encodeCodeArea(newCodeArea);
console.log(newCode);

// Test that the new UBID code matches the original.
console.log(code === newCode);
```

## License

The package is available as open source under the terms of [The 2-Clause BSD License](https://opensource.org/licenses/BSD-2-Clause).

## Contributions

Contributions are accepted on [GitHub](https://github.com/) via the fork and pull request workflow. See [here](https://help.github.com/articles/using-pull-requests/) for more information.
