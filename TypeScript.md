## Types

**How to add Intellisense (typings) from a npm module to legacy projects**

```typescript
// Create index.d.ts in your root
// Create a type based on import and make it globally available on Window
import * as xstate from 'xstate'

declare global {
   interface Window {
       xstate: typeof import('xstate')
   }
}

```

```typescript
// Use it on your legacy code
window as Window;
const xstateTyped = window.xstate;
```
