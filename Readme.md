# Realm prevents exit

This repo demonstrates an issue with Realm.

It seems like requiring the Realm module starts some async task that never finishes. This prevents (eg.) jest tests from exiting.

See `index.test.js`:

```javascript
require('realm')

describe("a test", function() {
  test("testing", function(){

  })
})
```

To execute the test run `yarn && yarn jest index.test.js`.

I'm running on Node `v8.9.1`, npm `5.6.0` and yarn `1.3.2`.
Realm is at `2.1.1`.


## Workaround

Run jest with the `--forceExit` flag.
