CSVJSON csv2json() function
===========================

Single function `csv2json` to reliably convert CSV to JSON. Self contained without dependencies. Used to power CSVJSON the online tool found at [www.csvjson.com/csv2json](https://www.csvjson.com/csv2json). Used by thousands everyday.

[npm package here](https://www.npmjs.com/package/csvjson-csv2json)

# Usage
Simply call `csv2json` passing a string to obtain JSON. The string may be CSV (comma separated values), TSV (tab separated values) or semi-colon separated values (typically used in French Excel). It will auto-detect the separator although you may override or force it via the `separator` option.

## Node example

```
const csv2json = require('./csv2json.js');
const csv = `album, year, US_peak_chart_post
The White Stripes, 1999, -
De Stijl, 2000, -
White Blood Cells, 2001, 61
Elephant, 2003, 6
Get Behind Me Satan, 2005, 3
Icky Thump, 2007, 2
Under Great White Northern Lights, 2010, 11
Live in Mississippi, 2011, -
Live at the Gold Dollar, 2012, -
Nine Miles from the White City, 2013, -`;

const json = csv2json(csv, {parseNumbers: true});
console.log(json);

```

## Browser example

Note: In the browser, global namespace `CSVJSON` is created. It contains the `csv2json` function.

```
<script type="text/javascript" src="csv2json.js"></script>
<script>
    const csv = `album, year, US_peak_chart_post
The White Stripes, 1999, -
De Stijl, 2000, -
White Blood Cells, 2001, 61
Elephant, 2003, 6
Get Behind Me Satan, 2005, 3
Icky Thump, 2007, 2
Under Great White Northern Lights, 2010, 11
Live in Mississippi, 2011, -
Live at the Gold Dollar, 2012, -
Nine Miles from the White City, 2013, -`;

    const json = CSVJSON.csv2json(csv, {parseNumbers: true});
    console.log(json);
</script>
```

In both cases, you would get this in the console:
```
[
  {
    "album": "The White Stripes",
    "year": 1999,
    "US_peak_chart_post": "-"
  },
  {
    "album": "De Stijl",
    "year": 2000,
    "US_peak_chart_post": "-"
  },
  {
    "album": "White Blood Cells",
    "year": 2001,
    "US_peak_chart_post": 61
  },
  {
    "album": "Elephant",
    "year": 2003,
    "US_peak_chart_post": 6
  },
  {
    "album": "Get Behind Me Satan",
    "year": 2005,
    "US_peak_chart_post": 3
  },
  {
    "album": "Icky Thump",
    "year": 2007,
    "US_peak_chart_post": 2
  },
  {
    "album": "Under Great White Northern Lights",
    "year": 2010,
    "US_peak_chart_post": 11
  },
  {
    "album": "Live in Mississippi",
    "year": 2011,
    "US_peak_chart_post": "-"
  },
  {
    "album": "Live at the Gold Dollar",
    "year": 2012,
    "US_peak_chart_post": "-"
  },
  {
    "album": "Nine Miles from the White City",
    "year": 2013,
    "US_peak_chart_post": "-"
  }
]
```

## Documentation
`csv2json` supports a number of options passed as an optional hash:
- `separator`: Character which acts as separator. If omitted, will attempt to detect comma `,`, semi-colon `;` or tab `\t`.
- `parseNumbers`: If set to `true` will attempt to convert a value to a number, if possible.
- `parseJSON`: If set to `true` will attempt to convert a value to a valid JSON value if possible. Detects numbers, `null`, `false`, `true`, `[]` and `{}`.
- `transpose`: If set to `true` will pivot the table. The first column becomes the header.
- `hash`: If set to `true` will use the first column as a key and return a hash instead of an array of objects.

You can of course test all of these options online on [www.csvjson.com/csv2json](https://www.csvjson.com/csv2json).

## Tests
Run the tests in your browser by opening `test-browser.html`.

Run the tests through node:
```
node test-node.js
```

# Companion functions

[json2csv](https://github.com/martindrapeau/csvjson-csv2json) to convert JSON to CSV. [npm package here](https://www.npmjs.com/package/csvjson-json2csv).

[json_beautifier](https://github.com/martindrapeau/csvjson-json_beautifier) to beautify and format your JSON. [npm package here](https://www.npmjs.com/package/csvjson-json_beautifier).

[JSON2_mod](https://github.com/martindrapeau/json2-mod) a replacement of `JSON` with more options to format your JSON. [npm package here](https://www.npmjs.com/package/json2-mod).