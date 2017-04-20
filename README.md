# npmtest-publish-latest

#### basic test coverage for  [publish-latest (v1.1.2)](https://github.com/kentcdodds/publish-latest#readme)  [![npm package](https://img.shields.io/npm/v/npmtest-publish-latest.svg?style=flat-square)](https://www.npmjs.org/package/npmtest-publish-latest) [![travis-ci.org build-status](https://api.travis-ci.org/npmtest/node-npmtest-publish-latest.svg)](https://travis-ci.org/npmtest/node-npmtest-publish-latest)

#### Script to publish generated files to a `latest` branch

[![NPM](https://nodei.co/npm/publish-latest.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/publish-latest)

| git-branch : | [alpha](https://github.com/npmtest/node-npmtest-publish-latest/tree/alpha)|
|--:|:--|
| coverage : | [![istanbul-coverage](https://npmtest.github.io/node-npmtest-publish-latest/build/coverage.badge.svg)](https://npmtest.github.io/node-npmtest-publish-latest/build/coverage.html/index.html)|
| test-report : | [![test-report](https://npmtest.github.io/node-npmtest-publish-latest/build/test-report.badge.svg)](https://npmtest.github.io/node-npmtest-publish-latest/build/test-report.html)|
| build-artifacts : | [![build-artifacts](https://npmtest.github.io/node-npmtest-publish-latest/glyphicons_144_folder_open.png)](https://github.com/npmtest/node-npmtest-publish-latest/tree/gh-pages/build)|

- [https://npmtest.github.io/node-npmtest-publish-latest/build/coverage.html/index.html](https://npmtest.github.io/node-npmtest-publish-latest/build/coverage.html/index.html)

[![istanbul-coverage](https://npmtest.github.io/node-npmtest-publish-latest/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fcoverage.lib.html.png)](https://npmtest.github.io/node-npmtest-publish-latest/build/coverage.html/index.html)

- [https://npmtest.github.io/node-npmtest-publish-latest/build/test-report.html](https://npmtest.github.io/node-npmtest-publish-latest/build/test-report.html)

[![test-report](https://npmtest.github.io/node-npmtest-publish-latest/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Ftest-report.html.png)](https://npmtest.github.io/node-npmtest-publish-latest/build/test-report.html)

- [https://npmdoc.github.io/node-npmdoc-publish-latest/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-publish-latest/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-publish-latest/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-publish-latest/build/apidoc.html)

![npmPackageListing](https://npmtest.github.io/node-npmtest-publish-latest/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmtest.github.io/node-npmtest-publish-latest/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "name": "publish-latest",
    "description": "Script to publish generated files to a 'latest' branch",
    "version": "1.1.2",
    "main": "dist/index.js",
    "scripts": {
        "start": "npm run test:watch",
        "prebuild": "rm -rf dist && mkdir dist",
        "build": "cd src && babel index.js -d ../dist && cd ..",
        "commit": "git-cz",
        "eslint": "eslint src/ -c other/src.eslintrc --ignore-path other/src.eslintignore && eslint src/*.test.js",
        "check-coverage": "istanbul check-coverage --statements 80 --branches 58 --functions 90 --lines 80",
        "report-coverage": "cat ./coverage/lcov.info | codecov",
        "test:watch": "mocha src/*.test.js -w --compilers js:babel/register",
        "test": "istanbul cover -x *.test.js _mocha -- -R spec src/index.test.js --compilers js:babel/register",
        "prepublish": "npm run build",
        "postpublish": "bin/publish-latest",
        "semantic-release": "semantic-release pre && npm publish && semantic-release post"
    },
    "repository": {
        "type": "git",
        "url": "https://github.com/kentcdodds/publish-latest.git"
    },
    "keywords": [
        "git",
        "ci",
        "release",
        "publish"
    ],
    "author": "Kent C. Dodds <kent@doddsfamily.us> (http://kentcdodds.com/)",
    "license": "MIT",
    "bugs": {
        "url": "https://github.com/kentcdodds/publish-latest/issues"
    },
    "bin": {
        "publish-latest": "bin/publish-latest"
    },
    "homepage": "https://github.com/kentcdodds/publish-latest#readme",
    "devDependencies": {
        "babel": "5.8.23",
        "chai": "3.2.0",
        "chai-string": "1.1.2",
        "codecov.io": "0.1.6",
        "commitizen": "1.0.4",
        "cz-conventional-changelog": "1.1.0",
        "eslint": "1.4.1",
        "eslint-config-kentcdodds": "4.0.0",
        "eslint-plugin-mocha": "0.5.1",
        "ghooks": "0.3.2",
        "istanbul": "0.3.19",
        "lodash": "3.10.1",
        "mocha": "2.3.2",
        "semantic-release": "^4.3.4",
        "validate-commit-msg": "1.0.0"
    },
    "config": {
        "ghooks": {
            "commit-msg": "./node_modules/.bin/validate-commit-msg && npm run eslint && npm t && npm run check-coverage && echo 'pre-commit checks good 👍'"
        }
    },
    "czConfig": {
        "path": "node_modules/cz-conventional-changelog/"
    },
    "dependencies": {
        "commander": "^2.8.1",
        "parse-author": "0.2.0",
        "path-here": "^1.1.0",
        "repo-path-parse": "1.0.1"
    }
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
