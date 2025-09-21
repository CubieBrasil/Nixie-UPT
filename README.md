# ⚠️ Nixie UPT SDK – (API NOT PUBLIC)

Official SDK for **NixieUPT API** integrations.  
This library provides utilities for user management, system monitoring, and connection handling.

---

## 📦 Installation

```bash
npm install nixie-upt
````

---

## 🚀 Client Initialization

```js
const { createClient } = require("nixie-upt");

// Create client with minimal config
const Nixie = createClient({
  host: "localhost",
  port: 6920,
  authToken: "YOUR_TOKEN_HERE",
  protocol: "http",
  timeout: 3000
});
```

⚠️ **Only `http` is supported**

---

## ⚙️ Configuration Options

| Field       | Type   | Required | Default       | Description                 |
| ----------- | ------ | -------- | ------------- | --------------------------- |
| `host`      | string | no       | `"localhost"` | Server host                 |
| `port`      | number | no       | `6920`        | Server port                 |
| `protocol`  | string | yes      | `"http"`     | Only `"http"` is supported |
| `timeout`   | number | no       | `3000`        | Timeout in ms               |
| `authToken` | string | ✅        | —             | Authentication token        |

---

## 👤 User Management

```js
// Access a specific user
const user = Nixie.user("user123");

// Check if user exists
const exists = await Nixie.userExists("user123");

// Create user
await Nixie.createUser("user456");

// General user operations
const users = Nixie.users();
await users.create({ id: "user789" });
```

---

## 🖥️ System Operations

```js
// Check connection
const isConnected = await Nixie.isConnected();

// Test connection + authentication
const test = await Nixie.testConnection();
console.log(test);

// Detailed connection info
const info = await Nixie.getConnectionInfo();
console.log(info);

// System overview
const overview = await Nixie.getOverview();
console.log(overview);
```

---

## 🔑 Authentication

```js
// Validate token
const valid = await Nixie.validateAuth();

// Update token
Nixie.updateAuthToken("NEW_TOKEN");

// Update connection
Nixie.updateConnection({ host: "localhost", port: 6920 });
```

---

## 🛠️ Utilities

```js
const { utils } = require("nixie-upt");

// Validate URL
console.log(utils.isValidUrl("http://localhost:6920")); // true

// Parse server URL
console.log(utils.parseServerUrl("http://localhost:6920"));
/*
{ protocol: "http", host: "localhost", port: 6920 }
*/

// Build server URL
console.log(utils.buildServerUrl("http", "localhost", 6920));
// http://localhost:6920
```

## 🐞 Debug Mode

```js
Nixie.enableDebug();
Nixie.log("Debug message");
Nixie.disableDebug();
```

## 📚 Exports

```js
const {
  NixieClient,
  createClient,
  createSimpleClient,
  validateConfig,
  HttpClient,
  UserManager,
  UrlManager,
  SystemManager,
  constants,
  utils
} = require("nixie-upt");

## 📌 Default Constants

* `DEFAULT_HOST = "localhost"`
* `DEFAULT_PORT = 6920`
* `DEFAULT_PROTOCOL = "http"`
* `DEFAULT_TIMEOUT = 3000`
