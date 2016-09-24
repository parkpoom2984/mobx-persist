# Mobx Persist

```
$ npm install mobx-persist --save
```

## Usage

``` typescript
import { observable, asMap } from 'mobx'
import { create, persist } from 'mobx-resist'

class SomeItem {
    @persist @observable name = 'some'
    @persist @observable count = 0
}

class SomeStore {
    @persist('object') @observable obj = { a: 1, b: 2 }
    @persist('map') @observable stringMap = asMap<string>({})
    @persist('list') @observable numList = [1,2,3,4]
    @persist('object', SomeItem) @observable s = new SomeItem
    @persist('map', SomeItem) @observable m = asMap<SomeItem>({})
    @persist('list', SomeItem) @observable l = []
}

const createStore = create({
    storage: AsyncStorage // default localStorage
})

export const someStore = createStore('some', SomeStore)

```

## Dependency

- [Serializr](https://github.com/mobxjs/serializr)
