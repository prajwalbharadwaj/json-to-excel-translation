# JSON to Excel Converter

Demo: [Json to Excel ](https://jtet.bharadwajlabz.com/)

## Overview

JSON to Excel Converter is a simple application designed to take JSON input in the form of an object and export it to an Excel file. The output format is an array of objects, where each entry has a key-value pair representation.

## Features

- Input: Accepts JSON in object format.
- Output: Exports data to an Excel file as an array of objects with key and value pairs.
- Ease of Use: Intuitive process for converting JSON to Excel.
- Flexibility: Supports dynamic JSON structures without predefined schemas.

---

## Input Format

The input JSON must be an object, as shown in the example below:

```
{
  "name": "John Doe",
  "age": 30,
  "city": "New York"
}
```

## Output Format

The exported Excel file will have the following format, with each row as an object containing key and value pairs:

| Key  | Value    |
| ---- | -------- |
| name | John Doe |
| age  | 30       |
| city | New York |

The corresponding JSON representation of the exported data would look like:

```
[
  { "key": "name", "value": "John Doe" },
  { "key": "age", "value": 30 },
  { "key": "city", "value": "New York" }
]
```
