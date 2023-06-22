# Node.js typescript

1. Init the app
```bash
yarn init
```

2. Install requirements

```
yarn global add ts-node
```
```
yarn add typescript @types/node
```
3. Add `"type": "module"` to `package.json`

4. `tsconfig.json` should have the following options:
```json
{
  "compilerOptions": {
    "module": "ESNext",
    "target": "ESNext",
    "moduleResolution": "Node"
  }
}
```
