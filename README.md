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
- [get](#get)
- [delete](#delete)
- [entries](#entries)
- [keys](#keys)
- [values](#values)
- [clear](#clear)
- [flush](#flush)

### set
```javascript
storage.set(key, value);
```
- Requires 0.1~
- key
    - `String` or `Number`
- value
    - `String`, `Number`, `Object`, `Array`, or `Blob`

### get
```javascript
let value = await storage.get(key);
```
- Requires 0.1~

### delete
```javascript
await storage.delete(key);
```
- Requires 0.1~

### entries
```javascript
let entries = await storage.entires();
```
- Requires 0.1~
- entries
    - `Array`

### keys
```javascript
let keys = await storage.keys();
```
- Requires 0.1~
- keys
    - `Array`

### values
```javascript
let values = await storage.values();
```
- Requires 0.1~
- values
    - `Array`

### clear
```javascript
await storage.clear();
```
- Requires 0.1~

### flush
```javascript
await storage.flush();
```
- Requires 0.1~

## Code Sample
```javascript
let db = new Storage('example', 'test');
console.log(await db.set('aaa', 'bbb')); // 'bbb';
console.log(await db.set('ccc', 'ddd')); // 'ddd';
console.log(await db.set('aaa', 'eee')); // 'eee';
console.log(await db.get('eee')); // undefined;
console.log(await db.keys()); // ['aaa', 'ccc'];
console.log(await db.values()); // ['eee', 'ddd'];
console.log(await db.delete('aaa')); // true;
console.log(await db.entries()); // [ {key: 'bbb', value: 'ddd'} ];
console.log(await db.clear()); // true;
console.log(await db.entries()); // [];
console.log(await db.purge()); // true;
console.log(await indexedDB.databases()); // [];
```
