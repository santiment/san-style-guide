# Santiment JavaScript Style Guide

## Table of Contents

  1. [Variables](#variables)
  2. [Destructuring](#destructuring)
  3. [Basic React Rules](#basic-react-rules)

## Variables

  <a name="variables"></a><a name="1"></a> [1](#variables)
  Use const for all of your references; avoid using var. eslint: prefer-const, no-const-assign

  If you must reassign references, use let instead of var. eslint: no-var

  Note that both let and const are block-scoped.

## Destructuring

  <a name="destructuring--object"></a><a name="2.1"></a>
  - [2.1](#destructuring--object) Use object destructuring when accessing and using multiple properties of an object. eslint: [`prefer-destructuring`](https://eslint.org/docs/rules/prefer-destructuring)

    > Why? Destructuring saves you from creating temporary references for those properties.

    ```javascript
    // bad
    const getFullName = user => {
      const firstName = user.firstName
      const lastName = user.lastName

      return `${firstName} ${lastName}`
    }

    // good
    const getFullName = user => {
      const { firstName, lastName } = user
      return `${firstName} ${lastName}`
    }

    // best
    const getFullName = ({ firstName, lastName }) => {
      return `${firstName} ${lastName}`
    }
    ```

    ```javascript
    // bad
    const value = type.value
    // good
    const { value } = type
    ```

<a name="destructuring--array"></a><a name="2.2"></a>
  - [2.2](#destructuring--array) Use array destructuring. eslint: [`prefer-destructuring`](https://eslint.org/docs/rules/prefer-destructuring)

    ```javascript
    const arr = [1, 2, 3, 4]

    // bad
    const first = arr[0]
    const second = arr[1]

    // good
    const [first, second] = arr
    ```

  <a name="destructuring--object-over-array"></a><a name="2.3"></a>
  - [2.3](#destructuring--object-over-array) Use object destructuring for multiple return values, not array destructuring.

    > Why? You can add new properties over time or change the order of things without breaking call sites.

    ```javascript
    // bad
    const processInput = input => [left, right, top, bottom]

    // the caller needs to think about the order of return data
    const [left, __, top] = processInput(input)

    // good
    const processInput = input => {
      // then a miracle occurs
      return { left, right, top, bottom }
    }

    // the caller selects only the data they need
    const { left, top } = processInput(input)
    ```

**[⬆ back to top](#table-of-contents)**

## Basic React Rules

  <a name="basic-react-rules"></a><a name="3"></a> [3](#variables)

  - Only include one React component per file.
    - However, multiple [Stateless, or Pure, Components](https://facebook.github.io/react/docs/reusable-components.html#stateless-functions) are allowed per file. eslint: [`react/no-multi-comp`](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/no-multi-comp.md#ignorestateless).
  - Always use JSX syntax.
  - Organize imports. First libraries, then our components, then styles
       ```jsx
    // bad
    import React, { Fragment } from 'react'
    import styles from './SignalCard.module.scss'
    import { Link } from 'react-router-dom'
    import cx from 'classnames'
    import StatusLabel from './../../components/StatusLabel'
    import { Panel, Icon, Toggle } from '@santiment-network/ui'

    // good
    import React, { Fragment } from 'react'
    import { Link } from 'react-router-dom'
    import { Panel, Icon, Toggle } from '@santiment-network/ui'
    import cx from 'classnames'
    import StatusLabel from './../../components/StatusLabel'
    import styles from './SignalCard.module.scss'
    ```

**[⬆ back to top](#table-of-contents)**
