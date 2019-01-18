> As a developer, it's common to spend more time figuring out what code does, rather than actually writing code.

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

It encourages component clean-up, testing, accessible styling, and faster re-[composition](https://reactjs.org/docs/composition-vs-inheritance.html):

```
components
 └ Foo
    ├ index.js
    ├ utils.js
    ├ Foo.spec.js
    ├ constants.js
    └ styles.js
```

##### How to Fractal

We start with `Foo`

```
components
 └ Foo
    └ index.js
```

##### Children and Parents

```
components
 └ Foo       <-- Parent
    ├ index.js
    └ FooNav <-- Child
        └ index.js
```

##### Siblings, together, under parents

```
components
 └ Foo          <-- Parent
    ├ index.js
    ├ FooNav    <-- Child / Sibling
    │   └ index.js
    └ FooFooter <-- Child / Sibling
        └ index.js
```

##### Family. Forever.

```
components
 └ Foo
    ├ index.js
    ├ FooNav
    │   └ index.js
    └ FooFooter
        ├ index.js
        ├ FooFooterButton
        │ ├ index.js
        │ └ Bar
        │   └ index.js
        ├ FooFooterButton
        │   └ index.js
        └ ListOfBars
            ├ index.js
            └ Bar
                └ index.js
```

##### Component Re-use?

```
components
 └ Foo
    ├ index.js
    ├ FooNav
    │   └ index.js
    └ FooFooter
        ├ index.js
        ├ FooFooterButton
        │ ├ index.js
        │ └ Bar         <-- Duplication!
        │   └ index.js
        ├ FooFooterButton
        │   └ index.js
        └ ListOfBars
            ├ index.js
            └ Bar       <-- Duplication!
                └ index.js
```

Move/Rename 'till it makes sense to you:

```
components
 ├ Bar                  <-- Boom.
 │  └ index.js
 └ Foo
    ├ index.js
    ├ FooNav
    │   └ index.js
    └ FooFooter
        ├ index.js
        ├ FooFooterButton
        │   └ index.js
        ├ FooFooterButton
        │   └ index.js
        └ ListOfBars
            └ index.js
```

#### Container === index.js

If you want to separate `Foo` component into a presentational and container:

1. create a secondary file named `Foo.js` under the `Foo` folder
1. stuff container logic into `index.js`

```
components
 └ Foo
    ├ index.js  <-- container AKA stateful component
    └ Foo.js    <-- presentational AKA stateless component
```

### High-Level Organization

Fractal a granular pattern, pair it with a broad organizational approach:

#### Organize by Routes

```
www.clearmetal.com/home

src
 ├ components  <-- "shared" components live here
 │  └ Nav
 │      └ index.js
 └ routes
    ├ index.js
    └ Home
        ├ index.js
        ├ style.js
        ├ home.spec.js
        └ Home.js
```

#### Organize by Functionality / Business Logic

```
src
 ├ components
 │   ├ Home
 │   │   ├ index.js
 │   │   ├ style.js
 │   │   └ Home.js
 │   └ Login
 │       ├ index.js
 │       ├ style.js
 │       └ Login.js
 └ routes
     └ index.js

```

## Assets

Every good project has icons, images, etc. A designer should control what is being used. Long term, we should have a seperate repo to pull icons, images, styles, etc.

```
src
 ├ components
 ├ routes
 └ assets
    ├ images
    ├ ...
    └ icons
```

## Redux

### Basic Structure

This can be sliced and diced, I recommend the following:

```
ReduxFoo
 ├ index.js     <-- Contains Reducer and Selectors, could contain Actions
 ├ Foo.spec.js
 ├ actions.js
 ├ types.js
 ├ utils.js
 └ sagas
    ├ index.js
    ├ utils.js
    └ sagas.spec.js
```

### Where to put them

From a repo stand point, we can either add redux files (depending on how we break them up).

#### With Components

With the previous structure, this can get messy, you could nest redux stuff within a state folder, or top level with the component files.

```
src
 ├ assets
 ├ routes
 └ components
    └ Foo
        ├ index.js
        ├ reducer.js <-- Contains Reducer and Selectors, could contain Actions
        ├ actions.js
        ├ types.js
        └ styles.js
```

#### Mirrored in State

I prefer this method as it allows easier reducer composition, organic grow, and patterned file naming (e.g. `utils` vs. `fooStateUtils.js`)

```
src
 ├ assets
 ├ routes
 ├ components
 │  └ Foo
 └ state
    └ Foo
        ├ index.js
        ├ Foo.spec.js
        ├ actions.js
        ├ types.js
        ├ utils.js
        └ sagas
```

There's also the discussion on building out the Redux state, [which can be cut several ways](https://redux.js.org/faq/organizing-state#how-do-i-organize-nested-or-duplicate-data-in-my-state). All of which are outside of the scope for this project.

## Services

Not everything can be a component. Independent modules can encapsulate business logic and be consumed throughout the app.

```
src
 ├ components
 ├ routes
 ├ store
 └ utils
    ├ intercom
    └ user
        └ sessions
            └ index.js
```

## Everything Else

Move it till is makes sense.

## Sources

- [Scaling React.js](https://vimeo.com/168648012) - Older but good
- Fractal:
  - [Fractal Project Structure](https://github.com/davezuko/react-redux-starter-kit/wiki/Fractal-Project-Structure)
  - [fractal a react app structure for infinite scale](https://hackernoon.com/fractal-a-react-app-structure-for-infinite-scale-4dab943092af)
- [Pascal](https://blog.bitsrc.io/structuring-a-react-project-a-definitive-guide-ac9a754df5eb)
- [Ducks](https://medium.freecodecamp.org/scaling-your-redux-app-with-ducks-6115955638be)
- [View](https://survivejs.com/react/advanced-techniques/structuring-react-projects/#directory-per-view)
- Higher Level Organization:
  - [Directory per Concept](https://survivejs.com/react/advanced-techniques/structuring-react-projects/#directory-per-concept)
  - [Directory per Component](https://survivejs.com/react/advanced-techniques/structuring-react-projects/#directory-per-component)
  - [Directory per View](https://survivejs.com/react/advanced-techniques/structuring-react-projects/#directory-per-view)
- [My journey toward a maintainable project structure for React/Redux](https://hackernoon.com/my-journey-toward-a-maintainable-project-structure-for-react-redux-b05dfd999b5)
