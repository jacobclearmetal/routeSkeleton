# Repo Proposal

A skeletal structure inspired by [View](https://survivejs.com/react/advanced-techniques/structuring-react-projects/#directory-per-view), [Ducks](https://medium.freecodecamp.org/scaling-your-redux-app-with-ducks-6115955638be), and [Fractal](https://hackernoon.com/fractal-a-react-app-structure-for-infinite-scale-4dab943092af).

## Contents:

- [React](https://github.com/jacobclearmetal/routeSkeleton#react)
  - [Fractal](https://github.com/jacobclearmetal/routeSkeleton##fractal-folders)
    - [How To](https://github.com/jacobclearmetal/routeSkeleton#how-to-fractal)
    - [Parents & Children](https://github.com/jacobclearmetal/routeSkeleton#children-and-parents)
    - [Siblings]()
    - [Example: Deep Nesting]()
  - [Higher Level Organization]()
    - [Routes]()
    - [Functionality]()
- [Redux]()

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

##### How to Fractal

We start with `Foo`

```
components
 └── Foo
     └ index.js
```

##### Children and Parents

```
components
 └── Foo        <-- Parent
     ├ index.js
     │
     └── FooNav <-- Child
         └ index.js
```

##### Siblings, together, under parents

```
components
 └── Foo           <-- Parent
     ├ index.js
     │
     ├── FooNav    <-- Child / Sibling
     │   └ index.js
     └── FooFooter <-- Child / Sibling
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
         ├── FooFooterButton
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
 │   ├── FooNav // DUPLICATE USE
 │   │   └ index.js
 │   └── FooFooter
 │       └ index.js
 │
 └── Bar
     ├ index.js
     │
     └── FooNav // DUPLICATE USE
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

### High Level Organization

Fractal a granular method of organizing, apply it how ever you'd like:

#### Organize by Routes

```
www.clearmetal.com/home

src
 ├── components // 'shared' components live here
 │   └── Nav
 │       └ index.js
 └── routes
    ├── index.js
    └── Home
        ├ index.js
        ├ style.js
        ├ home.spec.js
        └ Home.js
```

#### Organize by Functionality / Business Logic

```
src
 ├── components
 │   ├── Home
 │   │   ├ index.js
 │   │   ├ style.js
 │   │   └ Home.js
 │   └── Login
 │       ├ index.js
 │       ├ style.js
 │       └ Login.js
 │
 └── routes
     └── index.js

```

## Redux Useage
