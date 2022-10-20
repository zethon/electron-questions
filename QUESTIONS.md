<a name="ctx_bridge"></a>
## How do you use `contextBridge` with Typescript?

I have added a call to `contextBridge.exposeInMainWorld` in `preload.ts`, and stored a test value:

#### **`preload.ts`**
```typescript
const { contextBridge } = require('electron');

contextBridge.exposeInMainWorld('api', { xyzvalue: 'xyz' });
```

Neither attempt of printing this value in `renderer.ts` work as expected:

#### **`renderer.ts`**
```typescript
console.log("value: " + api.xyzvalue);
// console.log("value: " + window.api.xyzvalue);
```

Both give similar errors. For example, 

```bash
src/renderer.ts:8:25 - error TS2304: Cannot find name 'api'.

8 console.log("value: " + api.xyzvalue);
```

and 
```bash
src/renderer.ts:9:32 - error TS2339: Property 'api' does not exist on type 'Window & typeof globalThis'.

9 console.log("value: " + window.api.xyzvalue);
```

