# Description

An easy template for Vite with WASM.
reference to: https://juejin.cn/post/7146143545433260045

## How to modify the configuration of Vite

- `./wasm_test/package.json`:

You should add your pkg as a dependency

```json
"dependencies": {
    "test_wasm": "file:../pkg"
  },
```

- `./wasm_test/vite.config.js`:

You should add the pkg for vite config to ignore the package when they build.

```js
optimizeDeps: {
    exclude: ['test_wasm'],
}
```

Then you can use it with async, like `./wasm_test/src/App.vue`:

```js
import init,{test} from "test_wasm"

onMounted(()=>{
  init().then(()=>{console.log(test())});
})
```

## steps to run dev

### step 1 

run `wasm-pack build -t web`

to build the web assembly package

### step 2

`cd wasm_test`
and 
`pnpm install`

### step 3

`pnpm dev`

and then you can see the log from the WASM and return a array from WASM module.