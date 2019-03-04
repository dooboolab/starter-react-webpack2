# React Typescript Boilerplate
[![codecov](https://codecov.io/gh/dooboolab/dooboo-frontend-ts/branch/master/graph/badge.svg)](https://codecov.io/gh/dooboolab/dooboo-frontend-ts)
[![CircleCI](https://circleci.com/gh/dooboolab/dooboo-frontend-ts.svg?style=svg)](https://circleci.com/gh/dooboolab/dooboo-frontend-ts)

> Specification
* styled-component
* typescript
* react-router-dom v4
* ts-jest
* global state management with `context-api`
* react-hook
* localization

> We decided to remove `mobx` from the boilerplate from `dooboo-cli@1.4.0` completely. The reason to remove `mobx` is that we thought this isn't suitable with what `react` brought up as a design pattern today. `Functional programming` has been powered by `react-hook` so we chose to remove work on `object-oriented programming` which was more suitable with `mobx`. We hope you enjoy what we've brought up today.

# Gain points
```
1. Typescript support. No need to run tsc because webpack is doing it for you with ts-loader.
2. Sample of react-router-dom v4.
3. Able to learn how to structure react app with typescript.
4. Testing code with `ts-jest`.
5. Linting code with `tslint`.
6. Learn how to localize your project.
```

# INSTALL
```
1. npm install
2. npm start
```

# Structures
```text
app/
├─ assets
│  └─ icons // app icons
│  └─ images // app images like background images
├─ docs // explanation for dev stack we used. (Sorry for Korean)
├─ node_modules/
├─ src/
│  └─ apis
│  └─ components
│     └─ navigation
│     └─ screen
│     └─ shared
│  └─ utils
│  └─ ui
│  └─ contexts
│  └─ providers
│  └─ index.js
│  └─ theme.js // global variables for theming in `styled-components`
├─ test/
├─ .gitignore
├─ babel.config.js
├─ jest.config.js
├─ package.json
├─ postcss.config.js
├─ README.md
├─ STRINGS.js
├─ tsconfig.json
├─ tslint.json
├─ typings.d.ts
└─ webpack.config.js
```

# Running the project
Running the project is as simple as running
```sh
npm run start
```

This runs the `start` script specified in our `package.json`, and will spawn off a server which reloads the page as we save our files.
Typically the server runs at `http://localhost:8080`, but should be automatically opened for you.

# Testing the project
Testing is also just a command away:
```sh
npm test
 PASS  src/components/shared/__tests__/Button.test.tsx
 PASS  src/components/screen/__tests__/Intro.test.tsx

Test Suites: 2 passed, 2 total
Tests:       4 passed, 4 total
Snapshots:   2 passed, 2 total
Time:        2.145s, estimated 3s
```

# Adding component
> Copy sourcecode in /src/components/screen/Temp.tsx
> Create new tsx file with compnent name you will create

# Adding mobx store
> Include as many stores as you want in src/stores directory.
```
// class in src/stores/appStore.ts
class Store {
  @observable public user: User;
  @observable private locale: Localization;

  constructor() {
    this.user = new User();
    this.locale = new Localization();
  }

  public setLocale(param: Localization) {
    this.locale = param;
  }

  public getString = (param: string) => {
    return this.locale.getString(param);
  }
}
```

# Writing tests with Jest
We've created test examples with jest-ts in `src/components/screen/__tests__` and `src/components/shared/__tests__`. Since react is component oriented, we've designed to focus on writing test in same level of directory with component. You can simply run `npm test` to test if it succeeds and look more closer opening the source.

# Localization
We've defined Localization class in `src/models/Localization.ts`. This model class is used in mobx store which is `src/stores/appStore.ts`. Localization model imports `STRINGS.ts` which handles localized strings.
```
const STRINGS = {
  en: { // English
    SIGNUP: 'SIGN UP',
    LOGIN: 'LOGIN',
    LOGOUT: 'LOGOUT',
    GOOGLE_LOGIN: 'LOGIN WITH GOOGLE',
    FACEBOOK_LOGIN: 'LOGIN WITH FACEBOOK',
    EMAIL: 'EMAIL',
    PASSWORD: 'PASSWORD',
    COMPLETE: 'DONE',
  },
  ko: { // Korean
    SIGNUP: '회원가입',
    LOGIN: '로그인',
    LOGOUT: '로그아웃',
    GOOGLE_LOGIN: '구글 로그인',
    FACEBOOK_LOGIN: '페이스북 로그인',
    EMAIL: '이메일',
    PASSWORD: '패스워드',
    COMPLETE: '완료',
  },
  ...
```
In `App.tsx` when app starts it search for navigator's locale and set mobx state.
```
  const userLang: string = navigator.language;
  const localization = new Localization();
  localization.setLocale(userLang);
  store.setLocale(localization);
  ...
```

# React version
16.8

# React-router-dom version
4

# Typescript
3
