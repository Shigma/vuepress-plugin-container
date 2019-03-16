# [vuepress-plugin-container](https://vuepress-contrib.github.io/vuepress-plugin-container/)

[![Build Status](https://travis-ci.org/vuepress-contrib/vuepress-plugin-container.svg?branch=master)](https://travis-ci.org/vuepress-contrib/vuepress-plugin-container)
[![npm](https://img.shields.io/npm/v/vuepress-plugin-container.svg)](https://www.npmjs.com/package/vuepress-plugin-container)

A [VuePress](https://vuepress.vuejs.org/) plugin that registers markdown containers.

## Usage

```bash
npm install vuepress-plugin-container
# OR
yarn add vuepress-plugin-container
```

```js
// config.js
module.exports = {
  plugins: [
    // you can use it multiple times
    // so babel-style may be a better choice
    ['container', {
      type: 'right',
      defaultTitle: '',
    }],
    ['container', {
      type: 'theorem',
      before: info => `<div class="theorem"><p class="title">${info}</p>`,
      after: '</div>',
    }],
  ]
}
```

```stylus
// index.styl
.theorem
  margin 1rem 0
  padding .1rem 1.5rem
  border-radius 0.4rem
  background-color #f0f4f8
  .title
    font-weight bold

.custom-block
  &.right
    color transparentify($textColor, 0.4)
    font-size 0.9rem
    text-align right
```

## Options

### type

- **type:** `string`
- **required:** `true`

The type for the container. For example, if `type` is set to `foo`, only the following syntax will be parsed as a container:

```md
::: foo bar
write something here ~
:::
```

### defaultTitle

- **type:** `string`
- **default:** the upper case of `type`

The default title for the container. If no title is provided, `defaultTitle` will be shown as the title of the container.

### localeTitle

- **type:** `object`
- **default:** `{}`

The locale titles for the container. They will override `defaultTitle` when using the corresponding language.

### before

- **type:** `string | Function`
- **default:** `undefined`

String to be placed before the block. If specified as a function, an argument `info` will be passed to it. (In the example above, `info` will be `bar`.) If specified, it will override `defaultTitle` and `localeTitle`.

### after

- **type:** `string | Function`
- **default:** `undefined`

String to be placed after the block. If specified as a function, an argument `info` will be passed to it. (In the example above, `info` will be `bar`.) If specified, it will override `defaultTitle` and `localeTitle`.

### validate

- **type:** `Function`
- **default:** `undefined`

A function to validate tail after opening marker, should return `true` on success.

### render

- **type:** `Function`
- **default:** `undefined`

The renderer function for opening/closing tokens. If specified, it will override `before`, `after`, `defaultTitle` and `localeTitle`.

### marker

- **type:** `string`
- **default:** `':'`

The character to use as a delimiter.

## Contribution

Contribution Welcome!
