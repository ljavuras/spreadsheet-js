# spreadsheet-js

A web-based JavaScript spreadsheet.

spreadsheet-js is forked from [x-spreadsheet](https://github.com/myliang/x-spreadsheet).

## NPM

```shell
npm install ljavuras/spreadsheet-js
```

```html
<div id="spreadsheet-js-demo"></div>
```

```javascript
import Spreadsheet from "spreadsheet-js";
// If you need to override the default options, you can set the override
// const options = {};
// new Spreadsheet('#spreadsheet-js-demo', options);
const s = new Spreadsheet("#spreadsheet-js-demo")
  .loadData({}) // load data
  .change(data => {
    // save data to db
  });

// data validation
s.validate()
```

```javascript
// default options
{
  mode: 'edit', // edit | read
  showToolbar: true,
  showGrid: true,
  showContextmenu: true,
  view: {
    height: () => document.documentElement.clientHeight,
    width: () => document.documentElement.clientWidth,
  },
  row: {
    len: 100,
    height: 25,
  },
  col: {
    len: 26,
    width: 100,
    indexWidth: 60,
    minWidth: 60,
  },
  style: {
    bgcolor: '#ffffff',
    align: 'left',
    valign: 'middle',
    textwrap: false,
    strike: false,
    underline: false,
    color: '#0a0a0a',
    font: {
      name: 'Helvetica',
      size: 10,
      bold: false,
      italic: false,
    },
  },
}
```

## Bind events

```javascript
const s = new Spreadsheet("#spreadsheet-js-demo")
// event of click on cell
s.on('cell-selected', (cell, ri, ci) => {});
s.on('cells-selected', (cell, { sri, sci, eri, eci }) => {});
// edited on cell
s.on('cell-edited', (text, ri, ci) => {});
```

## update cell-text

```javascript
const s = new Spreadsheet("#spreadsheet-js-demo")
// cellText(ri, ci, text, sheetIndex = 0)
s.cellText(5, 5, 'xxxx').cellText(6, 5, 'yyy').reRender();
```

## get cell and cell-style

```javascript
const s = new Spreadsheet("#spreadsheet-js-demo")
// cell(ri, ci, sheetIndex = 0)
s.cell(ri, ci);
// cellStyle(ri, ci, sheetIndex = 0)
s.cellStyle(ri, ci);
```

## Internationalization

```javascript
// npm 
import Spreadsheet from 'spreadsheet-js';
import zhCN from 'spreadsheet-js/dist/locale/zh-cn';

Spreadsheet.locale('zh-cn', zhCN);
new Spreadsheet(document.getElementById('xss-demo'));
```

## Development

```shell
git clone https://github.com/ljavuras/spreadsheet-js.git
cd spreadsheet-js
npm install
npm run dev
```

Open your browser and visit http://localhost:8080.

## LICENSE

MIT
