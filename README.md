# @redux-utilities/reduce-reducers

[![Build Status](https://travis-ci.org/redux-utilities/reduce-reducers.svg?branch=master)](https://travis-ci.org/redux-utilities/reduce-reducers)
[![npm Version](https://img.shields.io/npm/v/@redux-utilities/reduce-reducers.svg)](https://www.npmjs.com/package/@redux-utilities/reduce-reducers)
[![npm Downloads Monthly](https://img.shields.io/npm/dm/@redux-utilities/reduce-reducers.svg)](https://www.npmjs.com/package/@redux-utilities/reduce-reducers)

> Reduce multiple reducers into a single reducer from left to right

## Install

```
npm install @redux-utilities/reduce-reducers
```

## Usage

```js
import reduceReducers from '@redux-utilities/reduce-reducers';

const reducer = reduceReducers(
  (prev, curr) => ({ ...prev, A: prev.A + curr }),
  (prev, curr) => ({ ...prev, B: prev.B * curr })
);

expect(reducer({ A: 1, B: 2 }, 3)).to.deep.equal({ A: 4, B: 6 });
expect(reducer({ A: 5, B: 8 }, 13)).to.deep.equal({ A: 18, B: 104 });
```

## Why?

Originally created to combine multiple Redux reducers that correspond to different actions (e.g. [like this](https://github.com/acdlite/redux-fsa/blob/master/src/handleActions.js#L12)). Technically works with any reducer, not just with Redux, though I don't know of any other use cases.
