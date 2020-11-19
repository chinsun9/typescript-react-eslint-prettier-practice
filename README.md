# typescript-react-eslint-prettier-practice

- typescript react 에 eslint, prettier, airbnb style guide 적용해보기

## CRA로 typescript-react 시작

```cmd terminal
npx create-react-app . --typescript

yarn add redux react-redux @types/react-redux

yarn add typesafe-actions
```

## eslint, prettier 설치

```
yarn add -D @typescript-eslint/eslint-plugin @typescript-eslint/parser eslint-config-airbnb-typescript eslint-plugin-jest

npx install-peerdeps --dev eslint-config-airbnb    <-- 물음에 y로 답해 yarn으로 설치 진행

yarn add -D prettier eslint-config-prettier eslint-plugin-prettier
```

## .eslintrc 생성

```json .eslintrc
{
  "extends": [
    "airbnb-typescript",
    "airbnb/hooks",
    "plugin:@typescript-eslint/recommended",
    "plugin:jest/recommended",
    "prettier",
    "prettier/react",
    "prettier/@typescript-eslint",
    "plugin:prettier/recommended"
  ],
  "plugins": ["react", "@typescript-eslint", "jest"],
  "env": {
    "browser": true,
    "es6": true,
    "jest": true
  },
  "globals": {
    "Atomics": "readonly",
    "SharedArrayBuffer": "readonly"
  },
  "parser": "@typescript-eslint/parser",
  "parserOptions": {
    "project": "./tsconfig.json"
  },
  "rules": {
    "linebreak-style": "off",
    "prettier/prettier": [
      "error",
      {
        "endOfLine": "auto",
        "singleQuote": true,
        "tabWidth": 2
      }
    ]
  }
}
```

- json 방식으로 생성한다.
- js 방식으로 했는데 `Parsing error: "parserOptions.project" has been set for @typescript-eslint/parser. ...` 오류가 나왔었다.

* 여기까지하고 src 및에 App.tsx나 index.tsx에 들어가서 빨간 밑줄이 생겻는지 확인한다.
* 반응이 없다면 vscode를 재시작한다.
* 그래도 반응이 없다면 .eslintrc > rule > prettier/prettier 에 tabWidth를 4, 3 등으로 조정하고 확인해 본다.
* 그래도 반응이 없다면 output > eslint 에 들어가서 에러가 발생했는지 확인한다.

## (선택사항) package.json 에 script 추가

```json package.json
"scripts": {
    // ...
  "format": "prettier --write src/**/*.ts{,x}",
  "lint": "tsc --noEmit && eslint src/**/*.ts{,x}"
}
```

## 참고

- https://medium.com/@brygrill/create-react-app-with-typescript-eslint-prettier-and-github-actions-f3ce6a571c97
