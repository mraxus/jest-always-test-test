# `Jest 22.4` includes `test/` when configured not to

Problem with jest and not testing in `/test` folder.

## Expected behaviour

Run: `npm run test`

Having `jest.config.js` with:

```
module.exports = {
	testEnvironment: 'node',
    testRegex: 'test/unit/.*\\.test\\.js$',
};
```

everything works as expected


## Unexpected behaviour

Run: `npm run fail`

Having `jest.config.js` with:

```
module.exports = {
	testEnvironment: 'node',
    testRegex: 'src/.*\\.test\\.js$',
};
```

the test suite includes tests in `test/` even though it's not configured to


## Update 2018-04-13

Turns out `testRegex` is matching file for absolute paths, not relative. This caused the problem as I had the absolute path like `/Users/me/src/js/jest-always-test-test`, where the folder `src` was interfering and accepting any directory to be a valid test location.

Issue https://github.com/facebook/jest/issues/5974 has been submitted and updated. See more details regarding this issue there.
