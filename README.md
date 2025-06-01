# storage.js

### Download
[Latest](//jc3213.github.io/storage.js/storage.js)

### HTML
```HTML
<script src="https://jc3213.github.io/storage.js/storage.js"></script>
```

### TamperMonkey
```javascript
// @require https://jc3213.github.io/storage.js/storage.js
```

## Syntax
```javascript
let storage = new Storage(dbName, storeName);
```
- dbName
    - `String`
    - The name of the database of `indexedDB`
- storeName
    - `String`
    - The name of the object store in database of `indexedDB`

## Method
- [set](#set)
- [has](#has)
- [get](#get)
- [delete](#delete)
- [entries](#entries)
- [keys](#keys)
- [values](#values)
- [forEach](#foreach)
- [clear](#clear)
- [flush](#flush)

### set
```javascript
storage.set(key, value);
```
- key
    - `string` or `number`
- value
    - `string`, `number`, `object`, `array`, or `blob`

### has
```javascript
let result = await storage.has(key);
```
- result
    - `boolean`

### get
```javascript
let value = await storage.get(key);
```

### delete
```javascript
await storage.delete(key);
```

### entries
```javascript
let entries = await storage.entires();
```
- entries
    - `array`

### keys
```javascript
let keys = await storage.keys();
```
- keys
    - `array`

### values
```javascript
let values = await storage.values();
```
- values
    - `array`

### forEach
```javascript
await storage.forEach(
    callback: function
);
```
- callback
    - `function`
    - ( entry: { key, value } ) => void

### clear
```javascript
await storage.clear();
```

### flush
```javascript
await storage.flush();
```

## Code Sample
```javascript
let db = new Storage('sample', 'test');
console.log(await db.set('aaa', 'bbb')); // 'aaa';
console.log(await db.set('ccc', 'ddd')); // 'ccc';
console.log(await db.has('bbb')); // false;
console.log(await db.keys()); // ['aaa', 'ccc'];
console.log(await db.set('aaa', 'eee')); // 'aaa'; overwrite 'aaa' => 'eee';
console.log(await db.values()); // ['eee', 'ddd'];
console.log(await db.delete('aaa')); // undefined; removed 'aaa' => 'eee';
console.log(await db.entries()); // [ {key: 'bbb', value: 'ddd'} ];
console.log(await db.clear()); // undefined; clear all items under database 'sample' -> object store 'test'
console.log(await db.entries()); // [];
console.log(await db.flush()); // true;
console.log(await indexedDB.databases()); // [];
```
