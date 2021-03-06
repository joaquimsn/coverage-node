# coverage-node changelog

## 4.0.0

### Major

- The updated [`kleur`](https://npm.im/kleur) dependency causes subtle differences in which environments get colored console output.

### Minor

- Added runtime argument type checks for various private and public functions.
- Improved console output for `coverage-node` CLI errors.

### Patch

- Updated dependencies.
- Also test Node.js v15 in GitHub Actions CI.
- Simplified the GitHub Actions CI config with the [`npm install-test`](https://docs.npmjs.com/cli/v7/commands/npm-install-test) command.
- Removed `npm-debug.log` from the `.gitignore` file as npm [v4.2.0](https://github.com/npm/npm/releases/tag/v4.2.0)+ doesn’t create it in the current working directory.
- Removed an extra space character from the `coverage-node` CLI error message when coverage is enabled.
- Use the `FORCE_COLOR` environment variable in tests to ensure output is colorized.
- Use a new [`snapshot-assertion`](https://npm.im/snapshot-assertion) dev dependency to snapshot test CLI output.
- Replaced the `stripStackTraces` test helper with a smarter `replaceStackTraces` helper that allows tests to detect a missing stack trace.
- Use `spawnSync` from the Node.js `child_process` API instead of the `execFilePromise` helper in tests.
- Added more `coverage-node` CLI tests.
- Improved internal JSDoc.
- Updated SLOC and install size related documentation.

## 3.0.0

### Major

- Updated supported Node.js versions to `^10.17.0 || ^12.0.0 || >= 13.7.0`.
- Updated dependencies, some of which require newer Node.js versions than were previously supported.
- Added a [package `exports` field](https://nodejs.org/api/esm.html#esm_package_entry_points) with [conditional exports](https://nodejs.org/api/esm.html#esm_conditional_exports) to support native ESM in Node.js and keep internal code private, [whilst avoiding the dual package hazard](https://nodejs.org/api/esm.html#esm_approach_1_use_an_es_module_wrapper). Published files have been reorganized, so previously undocumented deep imports will need to be rewritten according to the newly documented paths.

### Patch

- Updated Prettier config and scripts.
- Added ESM related keywords to the package `keywords` field.
- Updated ESLint config to match the new Node.js version support.
- Moved reading `process.argv` into the `coverageNode` function scope.
- Improved a JSDoc return type.
- Ensure GitHub Actions run on pull request.
- Test with Node.js v14 instead of v13.
- Updated EditorConfig.

## 2.0.3

### Patch

- Updated dev dependencies.
- Added a new [`hard-rejection`](https://npm.im/hard-rejection) dev dependency to ensure unhandled rejections in tests exit the process with an error.
- Destructured `assert` imports.
- Moved the `execFilePromise` helper from the `/lib` directory to `/test`, reducing the install size.

## 2.0.2

### Patch

- Allow a line to contain both code and a coverage ignore next line comment.
- Simplified `test/index.js`.

## 2.0.1

### Patch

- Updated dev dependencies.
- Added a new [`disposable-directory`](https://npm.im/disposable-directory) dependency to simplify the implementation and tests.
- Moved JSDoc comments above module exports code.
- Updated the compared [`c8` install size](https://packagephobia.com/result?p=c8@7.0.0), fixing [#1](https://github.com/jaydenseric/coverage-node/issues/1).

## 2.0.0

### Major

- The `coverage-node` CLI now skips code coverage when Node.js < v13.3 and displays an explanatory message in place of a code coverage report.
- Removed the `nodeWithCoverage` function.

### Minor

- New `coverageSupported` and `coverageSupportedMinNodeVersion` constants are exported.

### Patch

- Additionally test Node.js v10 and v12 in CI.
- Updated the comparison install size in the readme for [`nyc@15.0.0`](https://packagephobia.com/result?p=nyc@15.0.0).

## 1.1.0

### Minor

- Added a new `filesCount` field to the code coverage analysis resolved by the `analyseCoverage` function.

### Patch

- Fixed the total number of files in the report summary sometimes being too big.

## 1.0.1

### Patch

- Updated the [`eslint-config-env`](https://npm.im/eslint-config-env) dev dependency.
- Only test Node.js v13 in CI as earlier versions produce flawed coverage data.
- Updated the support documentation to recommend Node.js v13.3+.
- Corrected the temporary directory paths created by the `createTempDir` function.
- The `tempDirOperation` function now checks the temporary directory path was created before attempting to remove it in the cleanup phase.
- `fsPathRemove` function improvements:
  - Reject with an error if the provided path is not a string.
  - Use `rm -rf` instead of `rm -r` so that it doesn’t error when the path doesn’t exist.
- Tweaked test fixture formatting.

## 1.0.0

Initial release.
