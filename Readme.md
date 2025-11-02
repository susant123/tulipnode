[![Build Status](https://travis-ci.com/TulipCharts/tulipnode.svg?branch=master)](https://travis-ci.com/TulipCharts/tulipnode)
[![Build Status](https://ci.appveyor.com/api/projects/status/ps9l8w7fxi81v2q5/branch/master?svg=true)](https://ci.appveyor.com/project/codeplea/tulipnode)
[![npm](https://img.shields.io/npm/dw/tulind-maintained.svg)](https://www.npmjs.com/package/tulind-maintained)

# Tulind Maintained

> **📢 Important Notice:** This is a maintained fork of the original [tulipnode](https://github.com/TulipCharts/tulipnode) 
> project by Lewis Van Winkle. The original project appears to be unmaintained with pending PRs not being merged. 
> This fork provides compatibility with modern Node.js versions and ongoing maintenance.

## Why This Fork?

- ✅ **Modern Node.js Support**: Works with Node.js 16, 18, 20, and 22 (LTS versions)
- ✅ **Updated Dependencies**: All dependencies updated to latest versions
- ✅ **Active Maintenance**: Bugs are fixed and PRs are reviewed
- ✅ **Community Driven**: Welcoming contributions from the community
- ✅ **Same Great API**: Drop-in replacement for the original `tulind` package

**All credit for the original implementation and design goes to Lewis Van Winkle and the Tulip Indicators project.**

---

## About Tulip Indicators

Tulip Node is the official node.js wrapper for [Tulip
Indicators](https://tulipindicators.org). It provides 100+
technical analysis indicator functions, such as:
simple moving average, Bollinger Bands, MACD, Parabolic SAR, Stochastic
Oscillator, and many more.

## Installation

Installation should just be:

```js
npm install tulind-maintained
```

**Or if migrating from the original package:**
```js
npm uninstall tulind
npm install tulind-maintained
```

Then update your imports:
```js
// Old
// const tulind = require("tulind");

// New
const tulind = require("tulind-maintained");
```

It should work on Windows, Os X, and Linux. Node version 16, 18, 20, and 22 (LTS)
are tested and supported on each platform.

Note that pre-compiled binaries are available for Windows. For other platforms
you will need a C++ build environment installed. On Linux based distributions
this can be achieved by installing `build-essential` package.

You can force building from source with:

```js
npm install tulind-maintained --build-from-source
```

If you run into problems, let me know. I want this to be easy for everyone to
use.

## Usage

Tulip Node is very easy to use.

```js
var tulind = require("tulind-maintained");
console.log("Tulip Indicators version is:");
console.log(tulind.version);
```

In these examples, we assume you already have price data loaded such as:

```js
//Examples assume you have some price data like this:
//Data order is from oldest to newset (index 0 is the oldest)
var open = [4, 5, 5, 5, 4, 4, 4, 6, 6, 6];
var high = [9, 7, 8, 7, 8, 8, 7, 7, 8, 7];
var low = [1, 2, 3, 3, 2, 1, 2, 2, 2, 3];
var close = [4, 5, 6, 6, 6, 5, 5, 5, 6, 4];
var volume = [123, 232, 212, 232, 111, 232, 212, 321, 232, 321];
```

Calculating a simple moving average is as easy as:

```js
//Do a simple moving average on close prices with period of 3.
tulind.indicators.sma.indicator([close], [3], function (err, results) {
  console.log("Result of sma is:");
  console.log(results[0]);
});
```

Example of calculating the Stochastic Oscillator:

```js
//Functions that take multiple inputs, options, or outputs use arrays.
//Call Stochastic Oscillator, taking 3 inputs, 3 options, and 2 outputs.
tulind.indicators.stoch.indicator(
  [high, low, close],
  [5, 3, 3],
  function (err, results) {
    console.log("Result of stochastic oscillator is:");
    console.log(results[0]);
    console.log(results[1]);
  }
);
```

It's also easy to discover argument types at run-time:

```js
//Discover argument types at run-time:
console.log(tulind.indicators.stoch);

//Produces:
{ name: 'stoch',
  full_name: 'Stochastic Oscillator',
  type: 'indicator',
  inputs: 3,
  options: 3,
  outputs: 2,
  input_names: [ 'high', 'low', 'close' ],
  option_names: [ '%k period', '%k slowing period', '%d period' ],
  output_names: [ 'stoch_k', 'stoch_d' ],
  indicator: [Function],
  start: [Function] }
```

Many (most) indicators return an output array length smaller than the input length.
You can get the difference like this:

```js
console.log(
  "Given these options, the output arrays will be this much shorter than the input arrays:"
);
console.log(tulind.indicators.stoch.start([5, 3, 3]));
```

Hopefully it's obvious, but you can see all the available indicators by doing:

```js
console.log(tulind.indicators);
```

You can also see a full list of the available indicators on the [Tulip
Indicators website here](https://tulipindicators.org/list).

## Contributing

Contributions are welcome! This is a community-maintained fork, and we're happy to review PRs.

Please:
- Open an issue first for major changes
- Follow the existing code style
- Add tests for new features
- Update documentation as needed

## Original Project

This is a maintained fork of [tulipnode](https://github.com/TulipCharts/tulipnode) by Lewis Van Winkle.

The original project provided an excellent foundation for technical analysis in Node.js. This fork exists to ensure the project remains compatible with modern Node.js versions and receives ongoing maintenance.

## License

This project maintains the original **LGPL-3.0** license. See the [LICENSE](LICENSE) file for details.

Original work Copyright (C) Lewis Van Winkle  
Modifications Copyright (C) 2025 Susant and contributors

## Links

- **NPM Package**: [tulind-maintained](https://www.npmjs.com/package/tulind-maintained)
- **Original Project**: [TulipCharts/tulipnode](https://github.com/TulipCharts/tulipnode)
- **Tulip Indicators**: [tulipindicators.org](https://tulipindicators.org)
- **Report Issues**: [GitHub Issues](https://github.com/susant123/tulipnode/issues)

