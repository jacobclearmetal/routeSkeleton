# Repo Proposal

A skeletal structure inspired by [View](https://survivejs.com/react/advanced-techniques/structuring-react-projects/#directory-per-view), [Ducks](https://medium.freecodecamp.org/scaling-your-redux-app-with-ducks-6115955638be), and [Fractal](https://hackernoon.com/fractal-a-react-app-structure-for-infinite-scale-4dab943092af).

## Contents:

- [React](https://github.com/jacobclearmetal/routeSkeleton#react)
  - [Fractal](https://github.com/jacobclearmetal/routeSkeleton#fractal-folders)
    - [How To](https://github.com/jacobclearmetal/routeSkeleton#how-to-fractal)
    - [Parents & Children](https://github.com/jacobclearmetal/routeSkeleton#children-and-parents)
    - [Siblings](https://github.com/jacobclearmetal/routeSkeleton#siblings-together-under-parents)
    - [Example: Deep Nesting](https://github.com/jacobclearmetal/routeSkeleton#family-forever)
    - [Container/Presentation Components](https://github.com/jacobclearmetal/routeSkeleton#container--indexjs)
  - [Higher Level Organization](https://github.com/jacobclearmetal/routeSkeleton#high-level-organization)
    - [Example: Routes](https://github.com/jacobclearmetal/routeSkeleton#organize-by-routes)
    - [Example: Functionality](https://github.com/jacobclearmetal/routeSkeleton#organize-by-functionality--business-logic)
- [Redux]()
- [Sources]()

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

## Sources

- [Scaling React.js](https://vimeo.com/168648012) - Older but good
- Fractal:
  - [Fractal Project Structure](https://github.com/davezuko/react-redux-starter-kit/wiki/Fractal-Project-Structure)
  - [fractal a react app structure for infinite scale](https://hackernoon.com/fractal-a-react-app-structure-for-infinite-scale-4dab943092af)
- [Pascal](https://blog.bitsrc.io/structuring-a-react-project-a-definitive-guide-ac9a754df5eb)
- [Ducks](https://medium.freecodecamp.org/scaling-your-redux-app-with-ducks-6115955638be)
- Higher Level Organization:
  - [Directory per Concept](https://survivejs.com/react/advanced-techniques/structuring-react-projects/#directory-per-concept)
  - [Directory per Component](https://survivejs.com/react/advanced-techniques/structuring-react-projects/#directory-per-component)
  - [Directory per View](https://survivejs.com/react/advanced-techniques/structuring-react-projects/#directory-per-view)
- [My journey toward a maintainable project structure for React/Redux](https://hackernoon.com/my-journey-toward-a-maintainable-project-structure-for-react-redux-b05dfd999b5)
