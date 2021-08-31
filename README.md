# Print.js
forked from https://github.com/crabbly/Print.js  
The original print-js does not work with SSR (Next.js), there's an [open PR](https://github.com/crabbly/Print.js/pull/543) to fix that
that has a long time just waiting to be merged. So in the meantime we made this fork that has that small change and made our own 
[npm package](https://www.npmjs.com/package/@strive-labs/print-js). If the PR gets merged, please get rid of this repo and npm package and use the original print-js

## Testing on landing-gear
- Change dependency on landing-gear's package.json (don't forget to revert the change before doing a commit)
  ```diff
  -     "@strive-labs/print-js": "^1.6.0",
  +     "@strive-labs/print-js": "file:./relative/path/to/local/Print.js",
  ```
- `npm install`

Note: You may need to manually delete the dependency from node_modules to return back to the npm's registry package,
it works by creating a symlink to the local print-js directory, and `npm install` sometimes has problem reverting the symlink

## Publishing
```
npm install
npm run production
npm publish
```