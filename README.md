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
- js 방식으로 했는데 `Parsing error: "parserOptions.project" has been set for @typescript-eslint/parser. (...)` 오류가 나왔었다.

* 여기까지하고 src 및에 App.tsx나 index.tsx에 들어가서 빨간 밑줄이 생겻는지 확인한다.
* 반응이 없다면 vscode를 재시작한다.
* 그래도 반응이 없다면 .eslintrc > rule > prettier/prettier 에 tabWidth를 4, 3 등으로 조정하고 확인해 본다.
* 그래도 반응이 없다면 output > eslint 에 들어가서 에러가 발생했는지 확인한다.

## tsconfig.json 오류 확인하기

```jsonc
"jsx": "react-jsx" // <- 오류나서 아래로 고침

"jsx": "react"
```

- 자동생성된 tsconfig.json에 들어가 오류가 있나 확인한다.
- tsconfig.json 에 오류가없어야지 린트가 정상동작한다.

## (선택사항) package.json 에 script 추가

```jsonc package.json
"scripts": {
    // ...
  "format": "prettier --write src/**/*.ts{,x}",
  "lint": "tsc --noEmit && eslint src/**/*.ts{,x}"
}
```

## 저장할 때 자동으로 포맷팅하도록 설정하기

```json .vscode/setting.json
{
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "editor.formatOnSave": false
}
```

- setting.json을 열고 위처럼 만들어준다.
- workspace용 setting.json을 만들고 그대로 복사 붙여넣기 해도 된다.

* 이전부터 vscode 확장도구로 prettier를 사용하고 있는 사람들은 formatOnSave와 같은 설정을 켜놨을 수도있다.
* _source.fixAll.eslint_ 설정을 통해서 eslint에서 포맷팅을 하도록 할 수 있다.
* 둘다 켜두면 포맷팅이 두번일어나는 일이 벌어진다.

- .eslintrc 에서 prettier/prettier 에 원하는 설정을 해두면
- 별도의 .prettierrc 없이 prettier/prettier의 설정을 읽어 포맷팅이 동작한다.

## 참고

- [Create-React-App with TypeScript, ESLint, Prettier, and Github Actions | by Bryan Grill | Medium](https://medium.com/@brygrill/create-react-app-with-typescript-eslint-prettier-and-github-actions-f3ce6a571c97)
- 내 블로그 글 [react typescirpt eslint prettier airbnb style guide 적용하기](https://chinsun9.github.io/2020/11/18/react-typescirpt-eslint-prettier-airbnb-style-guide-적용하기/)
