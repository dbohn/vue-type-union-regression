# Vue 3.5.19 regression reproduction

This repository reproduces a regression, we noticed with Vue 3.5.19.
The reproduction was constructed by starting with a fresh project created using create-vite.

Within the `HelloWorld.vue` component, a `placement` prop was added with a default value of `right-end`. In the type definition, Floating UI's placement type was referenced.

Whereas Vue 3.5.18 was perfectly capable of handling the placement prop type in the `HelloWorld.vue` component,
Vue 3.5.19 fails with the following error message:

```
[vite:vue] [@vue/compiler-sfc] Default value of prop "placement" does not match declared type.
```

This message is displayed, although `right-end` is a valid type option.

The error can be reproduced by running:

```
npm install
npm run build
```

When lowering the version of the vue package to `3.5.18`, everything compiles as expected.

Please note, that this error persists up to the latest version 3.5.21.