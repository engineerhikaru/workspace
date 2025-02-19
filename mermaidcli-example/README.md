# MermaidCLI example

## System requirements

- macOS Sonoma 14.0 or later. (Have not try other versions)
- Node 20.11.0 or later. (Have not try other versions)
- npm 10.2.4 or later. (Have not try other versions)
- VSCode 1.97.2 or later. (Have not try other versions)

## Installation

```bash
$ npm install
```

## Compile the project

```bash
$ npm run compile
```

## Custom icon

available icons ↓

- [icones.js](https://icones.js.org/)

change code by yourself in `node_modules/@mermaid-cli/src/index.js` ↓

```javascript
await mermaid.registerExternalDiagrams([zenuml]);

// add ↓
mermaid.registerIconPacks([
  {
    name: 'logos',
    loader: () => fetch('https://unpkg.com/@iconify-json/logos@1/icons.json').then((res) => res.json()),
  },
  {
    name: 'material-symbols',
    loader: () => fetch('https://unpkg.com/@iconify-json/material-symbols/icons.json').then((res) => res.json()),
  },
]);
```

usage ↓

```plaintext
architecture-beta
  group api(logos:aws-lambda)[API]

  service db(logos:aws-aurora)[Database] in api
  service disk1(logos:aws-glacier)[Storage] in api
  service disk2(logos:aws-s3)[Storage] in api
  service server(logos:aws-ec2)[Server] in api

  db:L -- R:server
  disk1:T -- B:server
  disk2:T -- B:db
```
