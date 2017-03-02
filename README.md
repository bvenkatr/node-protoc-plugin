# node-protoc-plugin

Create protoc code-generation plugins easily in nodejs


## installation

`npm i -S protoc-plugin`


## usage

You can checkout the code in the `example/` dir, but here is a quick example:

```js
const protocPlugin = require('protoc-plugin')

protocPlugin(protos => {
  // do stuff here with protos
  // return array like [{name: 'filename', content: 'CONTENTS'}]
})
```

Make sure not to output anything to `stdout` (for example with `console.log`) because protoc uses `stdout`. I use `console.error` to output stuff to the user.

Since it's a promise, you can `throw` or just return `Promise.reject('reason')`, and you can do async stuff with promises.

Once you have made your plugin, save it as `protoc-gen-NAME`, give it executable permissions, then run it like this:

```
protoc --plugin=protoc-gen-NAME --NAME_out=generated yourfile.proto
```

If you put it in your path, you don't need the `--plugin=protoc-gen-NAME` part.

# advanced usage

If you need more from the incoming stdin `CodeGeneratorRequest` have a look at `example/protoc-gen-extendedlogger`.
