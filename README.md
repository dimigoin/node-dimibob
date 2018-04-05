# node-dimibob
[![CircleCI](https://img.shields.io/circleci/project/github/dimigoin/node-dimibob.svg?style=flat-square)](https://circleci.com/gh/dimigoin/node-dimibob)
![npm version](https://img.shields.io/npm/v/dimibob.svg?style=flat-square)
![npm license](https://img.shields.io/npm/l/dimibob.svg?style=flat-square)
![npm downloads](https://img.shields.io/npm/dt/dimibob.svg?style=flat-square)
[![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg?style=flat-square)](https://standardjs.com)

한국디지털미디어고등학교 급식 조회 프로그램<br>
Lookup meals information for [Korea Digital Media Highshcool](https://www.dimigo.hs.kr/).

## Install
```
$ npm install dimibob
```

## Usage
```js
import dimibob from 'dimibob'
dimibob.daily().then(console.log)
```

```js
{ breakfast: '우거지해장국/쌀밥/생선커틀렛/비엔나볶음/참나물무침/포기김치/그레놀라씨리얼/우유',
  lunch: '참치마요덮밥/들깨무채국/야채떡볶이/찰순대/깍두기/요구르트',
  dinner: '바베큐장각구이/볶음밥/가츠오장국/샐러드우동/영콘맛살볶음/무말랭이/포기김치/오렌지/매실쥬스',
  snack: '생크림모카번/덴마크요구르트',
  date: '2018-04-05' }
```

## API

### `dimibob()`
Fetches meal data of specific date.
```js
import dimibob from 'dimibob'

async function example () {
  const { dinner } = await dimibob(new Date(2018, 3, 1))
  console.log(`Special dinner for April Fools' day is ${dinner}`)
}
```

#### Syntax
```js
async function dimibob(date: Date?): Meal
```

#### Parameters
##### date (optional)
The [date] on which you want to fetch meal data. If `date` is omitted, `new Date()` is used instead.

#### Return value
[Meal object] containing the meal data.

### `dimibob.daily()`
Just an alias of `dimibob()`.

### `dimibob.monthly()`
```js
import { monthly } from 'dimibob'

async function example () {
  const list = await monthly(new Date(2018, 2, 17)) // day is irrelevant
  console.log(`March 14th: White day, and macaroons! ${list[13].lunch}`)
}
```

#### Syntax
```js
async function monthly(date: Date?): Meal[]
```

#### Parameters
##### date (optional)
The [date] on which you want to fetch meal data. If `date` is omitted, `new Date()` is used instead.

#### Return value
An array of [meal object] containing *monthly* meal data.

[date]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date
[meal object]: #meal-model
