# Fix compatibility with @iobroker/adapter-react@1.4.5

`@iobroker/adapter-react` has switched to default-importing `React`, which causes our `* as React` imports to break the type declarations.
By enabling `esModuleInterop` and dropping the `*` import (TypeScript only), we can fix it.

Migration guide:

-   Remove the line `"jsx": "react"` from `tsconfig.json` in the project root.
-   Add `"esModuleInterop": true` and `"jsx": "react"` to `admin/tsconfig.json` (inside `compilerOptions`)
-   TypeScript only: Replace `import * as React from "react"` with `import React from "react"`
-   TypeScript only: Replace `import * as ReactDOM from "react-dom"` with `import ReactDOM from "react-dom"`
