# md

# Node.js `fs` (File System) Cheat Sheet

## 📌 Importing `fs` Module
```js
const fs = require('fs');  // Callback-based API
const fsPromises = require('fs').promises;  // Promise-based API
const { readFile, writeFile } = require('fs').promises; // Destructuring for cleaner code
```

---

## **1️⃣ Reading Files**

### 📌 Synchronous Read (Blocking)
```js
const data = fs.readFileSync('file.txt', 'utf8');
console.log(data); // Reads file content synchronously
```

### 📌 Asynchronous Read (Non-Blocking)
```js
fs.readFile('file.txt', 'utf8', (err, data) => {
  if (err) throw err;
  console.log(data); // Reads file content asynchronously
});
```

### 📌 Promise-based Read (Async/Await)
```js
async function readFileAsync() {
  try {
    const data = await fsPromises.readFile('file.txt', 'utf8');
    console.log(data); // Reads file content using promises
  } catch (err) {
    console.error(err);
  }
}
readFileAsync();
```

---

## **2️⃣ Writing Files**

### 📌 Synchronous Write
```js
fs.writeFileSync('file.txt', 'Hello, World!'); // Writes data synchronously
```

### 📌 Asynchronous Write
```js
fs.writeFile('file.txt', 'Hello, Async!', (err) => {
  if (err) throw err;
  console.log('File written successfully'); // Writes data asynchronously
});
```

### 📌 Promise-based Write
```js
async function writeFileAsync() {
  try {
    await fsPromises.writeFile('file.txt', 'Hello, Async/Await!');
    console.log('File written successfully');
  } catch (err) {
    console.error(err);
  }
}
writeFileAsync();
```

---

## **3️⃣ Appending to a File**

### 📌 Synchronous Append
```js
fs.appendFileSync('file.txt', '\nAppended text!'); // Appends text synchronously
```

### 📌 Asynchronous Append
```js
fs.appendFile('file.txt', '\nAppended text!', (err) => {
  if (err) throw err;
  console.log('Appended successfully'); // Appends text asynchronously
});
```

### 📌 Promise-based Append
```js
async function appendFileAsync() {
  try {
    await fsPromises.appendFile('file.txt', '\nAppended Async!');
    console.log('Appended successfully');
  } catch (err) {
    console.error(err);
  }
}
appendFileAsync();
```

---

## **4️⃣ Deleting Files**

### 📌 Synchronous Delete
```js
fs.unlinkSync('file.txt'); // Deletes file synchronously
```

### 📌 Asynchronous Delete
```js
fs.unlink('file.txt', (err) => {
  if (err) throw err;
  console.log('File deleted'); // Deletes file asynchronously
});
```

### 📌 Promise-based Delete
```js
async function deleteFileAsync() {
  try {
    await fsPromises.unlink('file.txt');
    console.log('File deleted');
  } catch (err) {
    console.error(err);
  }
}
deleteFileAsync();
```

---

## **5️⃣ Checking File/Directory Existence**
```js
if (fs.existsSync('file.txt')) {
  console.log('File exists'); // Checks if file exists
} else {
  console.log('File does not exist');
}
```

---

## **6️⃣ Creating Directories**

### 📌 Synchronous
```js
fs.mkdirSync('newDir'); // Creates directory synchronously
```

### 📌 Asynchronous
```js
fs.mkdir('newDir', (err) => {
  if (err) throw err;
  console.log('Directory created');
});
```

### 📌 Promise-based
```js
async function createDir() {
  try {
    await fsPromises.mkdir('newDir');
    console.log('Directory created');
  } catch (err) {
    console.error(err);
  }
}
createDir();
```

---

## **7️⃣ Removing Directories**
```js
fs.rmdirSync('newDir'); // Removes directory synchronously
fs.rmdir('newDir', (err) => {
  if (err) throw err;
  console.log('Directory removed');
});
```

---

## **8️⃣ Reading Directory Contents**
```js
const files = fs.readdirSync('./');
console.log(files); // Reads directory contents synchronously

fs.readdir('./', (err, files) => {
  if (err) throw err;
  console.log(files); // Reads directory contents asynchronously
});
```

---

## **9️⃣ Renaming Files**
```js
fs.renameSync('old.txt', 'new.txt'); // Renames file synchronously
fs.rename('old.txt', 'new.txt', (err) => {
  if (err) throw err;
  console.log('File renamed');
});
```

---

## **🔟 Getting File Info (Stats)**
```js
const stats = fs.statSync('file.txt');
console.log(stats); // Gets file stats synchronously
```

---

## **🔹 Watching a File for Changes**
```js
fs.watch('file.txt', (event, filename) => {
  console.log(`${filename} file changed due to ${event}`); // Watches file changes
});
```

---

## **🎯 Summary of Common Methods**
| Method | Description |
|--------|------------|
| `fs.readFile()` | Read file (async) |
| `fs.readFileSync()` | Read file (sync) |
| `fs.writeFile()` | Write file (async) |
| `fs.writeFileSync()` | Write file (sync) |
| `fs.appendFile()` | Append to file (async) |
| `fs.unlink()` | Delete file |
| `fs.rename()` | Rename file |
| `fs.mkdir()` | Create directory |
| `fs.rmdir()` | Remove directory |
| `fs.readdir()` | Read directory contents |
| `fs.stat()` | Get file info |
| `fs.watch()` | Watch file for changes |

---

🚀 **Now you have a complete cheat sheet for the `fs` module!** 🎯
