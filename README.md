# Stale Closure in useCallback with Nested Functions in React Native

This repository demonstrates a common issue when using the `useCallback` hook in React Native with nested functions that access state variables.  The problem arises because the nested function's closure is created at the time of `useCallback` execution, and it doesn't update correctly even when the state variable changes.

The `bug.js` file shows how this can result in stale closures, and the `bugSolution.js` shows the correct approach to address this issue.

## Setup

1. Clone the repository
2. `npm install` or `yarn install`
3. Run the app (instructions might vary depending on your setup)

## Problem and Solution Explained

The core problem lies in how closures work in JavaScript.  The nested function retains a reference to the state variable's value *at the time the closure is created*, not at the time the nested function is called.  `useCallback` memoizes the function, preventing unnecessary re-renders, but it doesn't magically update the closure's reference.

The solution typically involves refactoring the code to eliminate the unnecessary closure or updating the dependency array of `useCallback` correctly.  Sometimes, using a different state management solution might also solve the problem.  Check the `bugSolution.js` file for a possible solution.