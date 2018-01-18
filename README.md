# [Codecov][1] VSCode Extension Example

[![codecov](https://codecov.io/gh/codecov/example-typescript-vscode-extension/branch/master/graph/badge.svg)](https://codecov.io/gh/codecov/example-typescript-vscode-extension)
[![Build Status](https://travis-ci.org/codecov/example-typescript-vscode-extension.svg?branch=master)](https://travis-ci.org/codecov/example-typescript-vscode-extension)

## Guide
### Travis Setup
Add to your `.travis.yml` file.
```yml
language: node

script:
  - npm run vscode:prepublish
  - npm test

after_success:
- bash <(curl -s https://codecov.io/bash)
```
### Producing Coverage Reports
Make sure you build your extension. In this case via `tsc -p ./` or simply `npm run vscode:prepublish`

Add to `coverconfig.json`:
```json
{
    "enabled": true,
    "relativeSourcePath": "../src",
    "relativeCoverageDir": "../../coverage",
    "ignorePatterns": ["**/node_modules/**"],
    "includePid": false,
    "reports": ["json", "html", "lcov"],
    "verbose": false
}
```
Run `npm test` which runs `node ./node_modules/vscode/bin/test`

## Differences to standard `yo code` generated example

* Modified `test/index.ts` - the main testrunner rewritten completely
* Changes in `stripts` and `devDependencies` section in `package.json`
* `coverconfig.json` added - small config file to change coverage settings localy.

## Caveats
### Private Repos

Add to your `.travis.yml` file.

```yml
after_success:
  - bash <(curl -s https://codecov.io/bash) -t uuid-repo-token
```

## Support

### Contact
- Intercom (in-app messanger)
- Email: [support@codecov.io](mailto:support@codecov.io)
- Slack: [slack.codecov.io](https://slack.codecov.io)
- [gh/codecov/support](https://github.com/codecov/support)

1. More documentation at https://docs.codecov.io
2. Configure codecov through the `codecov.yml`  https://docs.codecov.io/docs/codecov-yaml

[1]: https://codecov.io/
