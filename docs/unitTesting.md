# Unit Testing

Unit tests are fast and focused tests that verify the behavior of individual functions or components in isolation. 
Unlike End-to-End (E2E) tests, which validate complete user flows, unit tests ensure that the building blocks of your codebase work as expected.

## Purpose of Unit Testing

- Validates small, isolated units of logic (e.g., functions like `sort` and `filter`).
- Catches bugs early in the development cycle, before integration or deployment.
- Increases code quality and makes refactoring safer.
- Provides fast feedback during development.

## Example: `utils.js`

In this example, we are testing two utility functions: `sort` and `filter`. These are used to sort and filter arrays of objects. The tests are written using **Jest**.

```js
import { sort, filter } from '../utils.js';

const arr = [
  { name: 'Charlie' },
  { name: 'Alice' },
  { name: 'Bob' },
];
```

## sort function
### What’s being tested:

- Sorting an array in ascending and descending order based on a key (e.g., name)..
- Ensures the original array remains unchanged by working on a copy.
```js
  describe('sort', () => {
    it('sorts array ascending by key', () => {
      const result = sort([...arr], 'name', 'asc');
      expect(result.map(x => x.name)).toEqual(['Charlie', 'Bob', 'Alice']);
    });

    it('sorts array descending by key', () => {
      const result = sort([...arr], 'name', 'desc');
      expect(result.map(x => x.name)).toEqual(['Alice', 'Bob', 'Charlie']);
    });
  });
```
Note: The expected output in the test might seem counterintuitive — “ascending” returns ['Charlie', 'Bob', 'Alice']. This could be a logic bug or a naming mismatch in the actual implementation.

## filter function
### What’s being tested:

- Case-insensitive filtering based on a string match within a specific key.
- Returns the original array if the search term is empty or null.
- Returns an empty array if there are no matches.

```js
  describe('filter', () => {
    it('filters array by key and term (case-insensitive)', () => {
      expect(filter(arr, 'name', 'ali')).toEqual([{ name: 'Alice' }]);
      expect(filter(arr, 'name', 'BO')).toEqual([{ name: 'Bob' }]);
    });

    it('returns original array if term is empty', () => {
      expect(filter(arr, 'name', '')).toEqual(arr);
      expect(filter(arr, 'name', null)).toEqual(arr);
    });

    it('returns empty array if no match', () => {
      expect(filter(arr, 'name', 'zzz')).toEqual([]);
    });
  });

```
## How to Run Unit Tests
You can run all unit tests using this command:

```bash
npm run test
```
To run a specific test file (e.g., utils.test.js):
```bash
npm run test -- utils.test.js

```
you can also use watch mode to run test automatic, when saving files
```bash
npm run test -- --watch

```
## Summary

- Unit tests are great for fast and focused feedback.
- They work best for logic-heavy parts of your code (pure functions, helpers).
- Pair them with integration and E2E tests for full confidence.

