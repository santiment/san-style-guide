# Santiment JavaScript Style Guide

## Table of Contents

  1. [Variables](#variables)
  2. [Basic React Rules](#basic-react-rules)

## Variables

  <a name="variables"></a><a name="1"></a> [1](#variables)
  Use const for all of your references; avoid using var. eslint: prefer-const, no-const-assign

  If you must reassign references, use let instead of var. eslint: no-var

  Note that both let and const are block-scoped.
  ```

**[⬆ back to top](#table-of-contents)**

## Basic React Rules

  <a name="basic-react-rules"></a><a name="2"></a> [2](#variables)

  - Only include one React component per file.
    - However, multiple [Stateless, or Pure, Components](https://facebook.github.io/react/docs/reusable-components.html#stateless-functions) are allowed per file. eslint: [`react/no-multi-comp`](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/no-multi-comp.md#ignorestateless).
  - Always use JSX syntax.
  - Organize imports. First libraries, then our components, then styles

**[⬆ back to top](#table-of-contents)**
