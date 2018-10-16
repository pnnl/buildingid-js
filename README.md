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

BSD 3-clause "New" or "Revised" license.

## Contributions

Contributions are accepted on [GitHub](https://github.com/) via the fork and pull request workflow. See [here](https://help.github.com/articles/using-pull-requests/) for more information.
