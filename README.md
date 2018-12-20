# cheatsheets

Things I keep for utility and quick reference, mostly commands

I currently use Windows 10, Visual Studio Code and npm.

- [Create a new React app](#create-a-new-React-app)
- [Npm start using different browsers](#npm-start-using-different-browsers)
- [React + boostrap](#react-bootstrap)
- [React + redux](#react-redux)
- [Fontawesome + react](#fontawesome-react)
- [Debugging in Chrome](#debugging-in-chrome)
- [Jasmine](#jasmine)
- [React modal](#react-modal)
- [Github deploy while using React](#github-deploy-while-using-react)
- [jquery](#jquery)
- [Bootstrap](#bootstrap)
- [ESLINT](#ESLINT)
- [ESLINT-REACT](#ESLINT-REACT)
- [In case of messed up dependencies](#in-case-of-messed-up-dependencies)
- [Jest](#jest)
- [JEST + REACT](#jest-react)

## [Create a new React app](https://code.visualstudio.com/docs/nodejs/reactjs-tutorial)

npm install -g create-react-app: install react globally

create-react-app appName

open /go to new dir appName with VSC

debug: create launch.json and change the port of the url from 8080 to 3000

npm start: run the app in the browser locally

### Npm start using different browsers:

create and set value of EXPORT env, e.g.: SET BROWSER=firefox

npm start

to reset it: SET BROWSER=opera

See list of all env variables: SET

## React + boostrap

Install react

npm install --save react-bootstrap bootstrap@3

remove package-lock.json

npm install

add to index.js:

```
import 'bootstrap/dist/css/bootstrap.css';
import 'bootstrap/dist/css/bootstrap-theme.css';
// Put any other imports below so that CSS from your
// components takes precedence over default styles.
```

## React + redux

Install react

npm install --save redux

npm install --save react-redux

npm install --save-dev redux-devtools

Add this to App.js:

`import { Provider, connect } from 'react-redux'`

npm install

[Basic React-Redux setup](https://gist.github.com/luismartinezs/3fa20100ae88efeb62714531bbdecdf5)

## Fontawesome + react

npm i --save @fortawesome/fontawesome-svg-core

npm i --save @fortawesome/free-solid-svg-icons

npm i --save @fortawesome/react-fontawesome

add this to App.js:

```
import { library } from '@fortawesome/fontawesome-svg-core'
import { FontAwesomeIcon } from '@fortawesome/react-fontawesome'
import { faPlay } from '@fortawesome/free-solid-svg-icons'
library.add(faPlay) // adds an icon to lib
<FontAwesomeIcon icon={faPlay} />
```

## Debugging in Chrome

f12: open developer tools

Esc: Toggle console

Click line number: set breakpoint

Right click line number: set conditional breakpoint

debugger; > pause code

During debugging, right click line: continue here

## Jasmine

### Local install:

npm install --save-dev jasmine

node node_modules/jasmine/bin/jasmine init

package.json: `"scripts": { "test": "jasmine" }`

npm test

### Global install:

npm install -g jasmine

jasmine init

jasmine examples: useful to have a reference to create the tests

jasmine (run tests)

### Basic test

```
describe('Suite to do X', function() {

it("Should do Y", function() {
        expect(actual).toEqual(expected);
    });

});
```

## React modal

npm install react-modal

If it fails, do npm install and try again

## Github deploy while using React:

If you follow these steps it should work

1. Create new repo in github
2. Create react app project, and initiatie git local repo: git init, git add ., git commit -m "first commit"
3. Set github repo as your remote repo: git remote origin https://github.com/user/repository.git
4. Make changes to the local repo
5. npm run build
6. Paste `"homepage": "http://username.github.io/myapp"` in package.json, after "private" (change the url)
7. Add this to package.json after eject key
```
"predeploy": "npm run build",
"deploy": "gh-pages -d build"
```
8. Run: npm install --save-dev gh-pages
9. Run: npm run deploy
10. In git-hub > repo > settings, selectsource gh-pages branch, save
11. Try the link provided, if it doesn't work, select another branch, save, select again gh-pages, save. Reload page. It may take a few seconds/minutes for the web to show up.

## jquery

Google CDN: `<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>`

## Bootstrap:
### head
```
<meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css" integrity="sha384-MCw98/SFnGE8fJT3GXwEOngsV7Zt27NXFoaoApmYm81iuXoPkFOJwJ8ERdknLPMO" crossorigin="anonymous">
```

### end of body
```
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.3/umd/popper.min.js" integrity="sha384-ZMP7rVo3mIykV+2+9J3UJ46jBk0WLaUAdn689aCwoqbBJiSnjAK/l8WvCWPIPm49" crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/js/bootstrap.min.js" integrity="sha384-ChfqqxuZUCnJSK3+MXmPNIyE6ZbWh2IMqE241rYiqJxyMiZ6OW/JmZQ5stwEULTy" crossorigin="anonymous"></script>
```

## ESLINT

Readme: https://eslint.org/docs/user-guide/configuring

npm install --save-dev eslint

eslint --init

eslint filename.js

## ESLINT-REACT

follow this: https://github.com/yannickcr/eslint-plugin-react

npm install eslint --save-dev

## In case of messed up dependencies:

Delete node_modules and package-lock.json

npm install

[Source](https://npm.community/t/cannot-read-property-match-of-undefined/203/3)

## [JEST](https://jestjs.io/docs/en/getting-started)
### Setup:
- npm install --save-dev jest
- Given a file filename.js to test, create a filename.test.js
- npm test filename.test.js
- Add to package.json:
```
{
  "scripts": {
    "test": "jest"
  }
}
```
- remove package-lock.json and do again `npm install` if something does't work
### Use:
- In the file to test, export the required objects: `module.exports = testMe;`
- In a file fileName.test.js:
        - Import objects to test: `const testMe = require('./filename');`
        - Create a test suite, e.g:
```
describe('test suite', () => {

    test('testMe', () => {
        expect(true).toBe(true);
    })

})
```

## JEST + REACT

create-react-app already includes jest

npm i react-test-renderer

Sample test:
```
// Link.react.js
import React from "react";

const STATUS = {
  HOVERED: "hovered",
  NORMAL: "normal"
};

export default class Links extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      class: STATUS.NORMAL
    };
    this._onMouseEnter = this._onMouseEnter.bind(this);
    this._onMouseLeave = this._onMouseLeave.bind(this);
  }

  _onMouseEnter() {
    this.setState({ class: STATUS.HOVERED });
  }

  _onMouseLeave() {
    this.setState({ class: STATUS.NORMAL });
  }

  render() {
    return (
      <a
        className={this.state.class}
        href={this.props.page || "#"}
        onMouseEnter={this._onMouseEnter}
        onMouseLeave={this._onMouseLeave}
      >
        {this.props.children}
      </a>
    );
  }
}

// Link.react.test.js
import React from "react";
import Link from "../Link.react";
import renderer from "react-test-renderer";

test("Link changes the class when hovered", () => {
  const component = renderer.create(
    <Link page="http://www.facebook.com">Facebook</Link>
  );
  let tree = component.toJSON();
  expect(tree).toMatchSnapshot();

  // manually trigger the callback
  tree.props.onMouseEnter();
  // re-rendering
  tree = component.toJSON();
  expect(tree).toMatchSnapshot();

  // manually trigger the callback
  tree.props.onMouseLeave();
  // re-rendering
  tree = component.toJSON();
  expect(tree).toMatchSnapshot();
});
```
