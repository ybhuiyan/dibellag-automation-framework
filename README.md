# dibellag-automation-framework
A protractor cucumber automation framework built using the latest
versions of each. The goal is to display an automation framework with working
examples of how to use these latest packages. 

## Dependencies

NOTE: This framework maybe usable on lower versions of node and npm. 
However, these are the versions this project was built and test with.

```
npm  ->  5.3.0
node ->  v8.4.0
```

## Try it now

NOTES: This will run a set of example scenarios that are setup to outline the latest features of cucumber and how to work it.

```
npm install
npm test
```

## Linters

### Resources
[JSDOC](https://eslint.org/docs/rules/valid-jsdoc)
[ESLint](https://eslint.org/docs/rules/)
[Google](https://github.com/google/eslint-config-google)

Lint rules have been setup based on eslint and google recommendations,
along with gherkin and protractor lint rules. 

The following lint tasks are available:

```json
"lint": "(npm run lint:gherkin; npm run lint:es)",
"lint:fix": "eslint test/** --fix",
"lint:gherkin": "gherkin-lint",
"lint:es": "eslint test/**"
```    

These are the protractor lint rules that will be turned on.
Investigating why it throws error when there isnt a case for it.

TODO: Try adding back: "plugin:protractor/recommended" in the extends, and find out why each rule needs protractor/ in front of it to work. 

Settings for protractor rules: 
```
2 - error
1 - warning
0 - off
```

## How to use protractor's elementExplorer

1. Run the below command in one terminal tab
```
npm run webdriver-manager:setup
```
This will update webdriver-manager and start it

2. Run the below command in a second terminal tab
```
npm run test:elementExplorer
``` 
3. Testing selectors
```
You can now navigate to any url and run protractor 
commands to test your selectors and functions.
```

## Bash cli differences

1. How to run a task one after the other regardless if the first one passes
```
npm run test:scripts:ignore-failure
```

2. How to run tasks synchronously
```
npm run test:scripts:synchronous
```

3. How to run tasks in parallel
```
npm run test:scripts:parallel
```
See example of parallel execution in ./test/scripts/parallel.sh

## Add a script to the scripts directory

After adding a script to the scripts directory you needs to run
the following command to make it executable:

```
chmod +x fileName
```

## TODOs

1. Mock setup
2. Travis ci/headless chrome cucumber tests
3. Fuctions for executing requests
4. Custom reporter
5. Parallel testing
	5.1 shardTestFiles: true adds PID to results file name
	5.2 if a task returns no results a json file is created with [] which is invalid and doesnt allow to give report on other scenarios
	5.3 restartBrowserBetweenTests seems to partially work, meaning soon as it hits github example scenarios it fails waiting for angular even though browser.waitForAngularEnabled(false) is being set.
6. Add more test examples
7. Semantic commits / changelog
8. Cross browser support

## FAQ

### The world instance isn't available in my hooks or step definitions.

This has frequently been caused by the use of ES6 arrow functions. You cannot use ES6 arrow functions for step definitions or hooks because they bind this to the current context which prevents the world instance from being injected.

### Why do my definition patterns need to be globally unique instead of unique only within Given, When, Then?

To encourage a ubiquitous, non-ambiguous domain language. Using the same language to mean different things is basically the definition of ambiguous. If you have similar Given and Then patterns, try adding the work "should" to your Then pattern


