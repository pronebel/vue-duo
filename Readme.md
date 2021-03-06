
[![NPM version][npm-img]][npm-url]
[![Build status][travis-img]][travis-url]
[![Test coverage][coveralls-img]][coveralls-url]
[![License][license-img]][license-url]
[![Dependency status][david-img]][david-url]

### vue-duo

* You can handle complex data flow with awesome `rxjs`.
  - [vuejs/vue-rx](https://github.com/vuejs/vue-rx) is a RxJS binding for Vue.js.
* `vue-duo` provide a tiny store for simple data flow, works fine with `vue-rx`.

### Getting Started

* `app.vue`

```vue

<template>
  <div>
    <h3>{{ count }}</h3>
    <button @click="add(1)">add</button>
  </div>
</template>

<script>

import { add } from './action'
import store from './store'

export default {
  name: 'app',
  store,
  methods: {
    add
  }
}

</script>

```

* `action.js`

```js

import { createAction } from 'vue-duo'

export const add = createAction((num) => num)

```

* `store.js`

```js

import { createStore } from 'vue-duo'

import { add } from './action'

const store = createStore({
  count: 0
})

store.subscribeActions({
  [add]: (num) => ({
    count: store.state.count + num
  })
})

export default store

```

### Usage

* [example](example)

### License
MIT

[npm-img]: https://img.shields.io/npm/v/vue-duo.svg?style=flat-square
[npm-url]: https://npmjs.org/package/vue-duo
[travis-img]: https://img.shields.io/travis/haoxins/vue-duo.svg?style=flat-square
[travis-url]: https://travis-ci.org/haoxins/vue-duo
[coveralls-img]: https://img.shields.io/coveralls/haoxins/vue-duo.svg?style=flat-square
[coveralls-url]: https://coveralls.io/r/haoxins/vue-duo?branch=master
[license-img]: http://img.shields.io/badge/license-MIT-green.svg?style=flat-square
[license-url]: http://opensource.org/licenses/MIT
[david-img]: https://img.shields.io/david/haoxins/vue-duo.svg?style=flat-square
[david-url]: https://david-dm.org/haoxins/vue-duo
