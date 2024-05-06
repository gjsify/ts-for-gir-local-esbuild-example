# ts-for-gir-local-example

This example shows how `ts-for-gir` v4 can be used to generate and use the TypeScript types.

![Hello World GJS Gtk/Adwaita application](https://github.com/gjsify/ts-for-gir-local-tsc-example/assets/1073989/af49b7b8-48e3-4bb2-b051-03a000caf2ca)


## How to use

1. Install the dependencies using `npm install`
2. Run `npm run generate` to generate the TypeScript types
3. Run `npm run build` to build the TypeScript code using esbuild
4. Run `npm run start` to start the code with GJS (alternatively run `gjs -m main.js`)

## How it works

The `tsconfig.json` file is configured to use the `ESNext` target and `lib` setting, which allows for the use of ES module syntax and `async/await`. The `types` array is set to `["@girs/gjs", "@girs/gio-2.0", "@girs/adw-1", "@girs/gtk-4.0"]` to include the generated types.

The `main.ts` file uses the generated types to create a simple Hello World GJS Gtk/Adwaita application.

The `esbuild.js` file is a simple script that uses `esbuild` to build the TypeScript code instead of using `tsc`.

The `package.json` file is configured to add the generated types to the workspace, So that the types can be found by the TypeScript compiler:

```json
  "workspaces": [
    "@types/*"
  ]
```

In addition, 3 NPM scripts are included:

* `generate`: This script runs `ts-for-gir` CLI to generate the types for the `Adw-1` package.
* `build`: This script runs `esbuild.js` to build the TypeScript code.
* `start`: This script runs `gjs` to start the code with GJS.

## Other examples

* [ts-for-gir-local-tsc-example](https://github.com/gjsify/ts-for-gir-local-tsc-example) - Almost identical example, but uses tsc to build the TypeScript code

