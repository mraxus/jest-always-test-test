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
