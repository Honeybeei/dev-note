# 🔁 Export and Import

- [🔁 Export and Import](#-export-and-import)
  - [🔑 Key Words](#-key-words)
  - [👀 Fast Lookup](#-fast-lookup)
  - [👵🏻 Before ES6](#-before-es6)
  - [📦 Export and Import](#-export-and-import-1)
    - [Named Export and Import](#named-export-and-import)
    - [Default Export and Import](#default-export-and-import)

## 🔑 Key Words

- `export`
- `import`

## 👀 Fast Lookup

- `export`: Share code with another file.
  - **Named export**: Share multiple values or functions from a file.
  - **Default export** (`export default`): Share a single value or function from a file.
- `import`: Get code from another file.
  - Importing Named Exports: `import { name } from './file.js';`
  - Importing Default Exports: `import name from './file.js';`

## 👵🏻 Before ES6

```javascript
// file.js
module.exports = 'John';
```

```javascript
// main.js
const name = require('./file.js');
console.log(name); // John
```

## 📦 Export and Import

ES6 introduced a new syntax for exporting and importing modules.

### Named Export and Import

Named export is used when you want to export **multiple** values or functions from a file.

```javascript
// file.js
export const name = 'John';
export const age = 30;
```

You can import named exports using **curly braces**.

```javascript
// main.js
import { name, age } from './file.js';
console.log(name, age); // John 30
```

### Default Export and Import

Default export is used when you want to export a **single** value or function from a file.

```javascript
// file.js
const name = 'John';
export default name;
```

You can import a default export **without curly braces**.

```javascript
// main.js
import name from './file.js';
console.log(name); // John
```

[🔙 Back to the main page](./README.md)
