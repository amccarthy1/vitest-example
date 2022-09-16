# Issue with `yarn bin` resolution

## To reproduce: 
1) clone this repo.
2) run `yarn`
3) Change directory to `parent` and run `yarn bin vitest`

Step 3 will yield different results depending on which commit is checked out.
- If the child package is named `subpackage`, the version you get is `vitest-example/parent/subpackage/node_modules/vitest/vitest.mjs`.
- If the child package is named `child`, the version you get is `vitest-example/parent/node_modules/vitest/vitest.mjs`

## Expected outcome
Under both versions, the correct version to use is `parent/node_modules/vitest/vitest.mjs`

Ideally, yarn should not produce different results for the location of a binary installed by package `A` based on the existence of a package whose name is alphabetically greater than `node_modules`
