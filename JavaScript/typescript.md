# Node.js typescript

1. Init the app
```bash
yarn init
```

2. Install requirements
```
yarn add typescript ts-node @types/node && mkdir src && touch src/app.ts 
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
5. Run the app with the following command:
 ```
 node --experimental-specifier-resolution=node --loader ts-node/esm ./src/app.ts
 ```
Or 
```
yarn global add ts-node
```
And Run:
```
ts-node --esm ./src/app.ts
```
