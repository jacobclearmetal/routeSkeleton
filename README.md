# Repo Proposal

A skeletal structure inspired by [View](https://survivejs.com/react/advanced-techniques/structuring-react-projects/#directory-per-view), [Ducks](https://medium.freecodecamp.org/scaling-your-redux-app-with-ducks-6115955638be), and [Fractal](https://hackernoon.com/fractal-a-react-app-structure-for-infinite-scale-4dab943092af).

## React

### Fractal Folders

> Why wrap a component in a folder?

It allows a singular component to be cleaned up, tested, accessible styles, and _componentized_:

```
src
 └── Foo
    ├── index.js
    ├── utils.js
    ├── Foo.spec.js
    ├── constants.js
    └── styles.js
```

##### How to Fractal:

```
components
└── Foo
    └ index.js
```

##### Children components live with their parents:

```
components
└── Foo
    ├ index.js
    │
    └── FooNav
        └ index.js
```

##### Siblings, together, under parents:

```
components
└── Foo
    ├ index.js
    │
    ├── FooNav
    │   └ index.js
    └── FooFooter
        └ index.js
```

##### Family. Forever.

```
components
└── Foo
    ├ index.js
    ├── FooNav
    │   └ index.js
    │
    └── FooFooter
        ├ index.js
        │
        ├── FooFooterButtn
        │   └ index.js
        └── FooFooter
            ├ index.js
            └── Header
                └ index.js
```

##### Component Re-use?

```
components
├── Foo
│   ├ index.js
│   │
│   ├── FooNav // DUPLICATE USE CASE
│   │   └ index.js
│   └── FooFooter
│        └ index.js
│
└── Bar
    ├ index.js
    │
    └── FooNav // DUPLICATE USE CASE
      └ index.js

```

Move/Rename 'till it makes sense:

```
components
├── Nav // Was FooNav
│   └ index.js
│
├── Foo
│   ├ index.js
│   │
│   └── FooFooter
│        └ index.js
│
└── Bar
    └ index.js
```

#### Container === index.js

If you want to seperate `Foo` component into a presentational and container:

1. create a secondary file named `Foo.js` under the `Foo` folder
1. stuff container logic into `index.js`

```
components
└── Foo
    ├ index.js // 'container'
    └ Foo.js // 'presentational'
```

### Useage

```
www.clearmetal.com/home

src
 ├── components
 └── routes
    ├── index.js
    └── Home
        ├ index.js
        ├ style.js
        ├ home.spec.js
        └ Home.js
```

```
src
 ├── components
 │
 ├── routes
 │  ├── index.js // react-router
 │  ├── Home
 │  │   ├ index.js // container component
 │  │   ├ style.js
 │  │   └ Home.js // optional stateless component
 │  ├── Login
 │  │   ├ index.js // container component
 │  │   ├ style.js
 │  │   └ Login.js // optional stateless component
 └── product
    ├── container.js
    ├── actions.js
    ├── reducers.js
    ├── types.js
    ├── sagas.js
    └── selectors.js
```

## Redux Useage

## TODO:

- [ ] Handle Design Imports: custom Icons, Images, etc.
