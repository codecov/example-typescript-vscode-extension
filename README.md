# [Codecov][1] VSCode Extension Example

[![codecov](https://codecov.io/gh/codecov/example-typescript-vscode-extension/branch/master/graph/badge.svg)](https://codecov.io/gh/codecov/example-typescript-vscode-extension)
[![Build Status](https://travis-ci.org/codecov/example-typescript-vscode-extension.svg?branch=master)](https://travis-ci.org/codecov/example-typescript-vscode-extension)
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fcodecov%2Fexample-typescript-vscode-extension.svg?type=shield)](https://app.fossa.com/projects/git%2Bgithub.com%2Fcodecov%2Fexample-typescript-vscode-extension?ref=badge_shield)

## tl;dr
1. Clone this repo `git clone git@github.com:codecov/example-typescript-vscode-extension.git`
2. Start working on your TypeScript project (only ts-code)

## Guide
### Travis Setup
Add to your `.travis.yml` file.
```yml
language: node

before_install:
  - if [ $TRAVIS_OS_NAME == "linux" ]; then
      export CXX="g++-4.9" CC="gcc-4.9" DISPLAY=:99.0;
      sh -e /etc/init.d/xvfb start;
      sleep 3;
    fi

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

1. More documentation at https://docs.codecov.io
2. Configure codecov through the `codecov.yml`  https://docs.codecov.io/docs/codecov-yaml

We are happy to help if you have any questions. Please contact email our Support at [support@codecov.io](mailto:support@codecov.io)

[1]: https://codecov.io/


## License
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fcodecov%2Fexample-typescript-vscode-extension.svg?type=large)](https://app.fossa.com/projects/git%2Bgithub.com%2Fcodecov%2Fexample-typescript-vscode-extension?ref=badge_large)