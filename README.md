# rollup-plugin-copy2

[Rollup](https://github.com/rollup/rollup) plugin to copy additional assets
to the build directory.

This plugin actually does not copy assets but adds them to the resulting bundle
so they could be accessed by other plugins (for example by the
[rollup-plugin-zip](https://github.com/mentaljam/rollup-plugin-zip)).

The actual copying is made by the Rollup itself.

## Install

```sh
npm i -D rollup-plugin-copy2
```

## Usage

```js
// rollup.config.js

import {copy} from 'rollup-plugin-copy2'

export default {
  input: 'index.js',
  output: {
    dir: 'dist',
    format: 'es',
  },
  plugins: [
    copy({
      assets: [
        'README.md',
        ['data.txt', 'assets/data.txt'],
      ]
    }),
  ],
}
```

## Options

### assets

#### Type

```js
(string | [string, string])[]
```

An array of assets to copy. Each entry can be a `string` that contains a relative
path to the source file, or a pair of strings `[string, string]` that contains
relative paths to the source and destination files.

If an entry is a single string then the destination file path will be equal to it
(relative to the output directory).

## License

[MIT](LICENSE) © [Petr Tsymbarovich](mailto:petr@tsymbarovich.ru)
