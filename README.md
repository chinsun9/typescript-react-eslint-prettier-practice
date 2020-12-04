# typescript-react-eslint-prettier-practice

- 2020.12.04 기준 최신 CRA 버전으로 다시 적용해보기


## 귀찮은 자를 위한 package.json, eslint config
```jsonc
{
  "name": "typescript-react-eslint-prettier-practice",
  "version": "0.1.0",
  "private": true,
  "dependencies": {
    "@testing-library/jest-dom": "^5.11.4",
    "@testing-library/react": "^11.1.0",
    "@testing-library/user-event": "^12.1.10",
    "@types/jest": "^26.0.15",
    "@types/node": "^12.0.0",
    "@types/react": "^16.9.53",
    "@types/react-dom": "^16.9.8",
    "react": "^17.0.1",
    "react-dom": "^17.0.1",
    "react-scripts": "4.0.1",
    "typescript": "^4.0.3",
    "web-vitals": "^0.2.4"
  },
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  },
  "eslintConfig": {
    "extends": [
      "react-app",
      "react-app/jest"
    ]
  },
  "browserslist": {
    "production": [
      ">0.2%",
      "not dead",
      "not op_mini all"
    ],
    "development": [
      "last 1 chrome version",
      "last 1 firefox version",
      "last 1 safari version"
    ]
  },
  "devDependencies": {
    "@typescript-eslint/eslint-plugin": "^4.9.0",
    "@typescript-eslint/parser": "^4.9.0",
    "eslint-config-airbnb": "18.2.1",
    "eslint-config-airbnb-typescript": "^12.0.0",
    "eslint-config-prettier": "^6.15.0",
    "eslint-plugin-import": "2.22.1",
    "eslint-plugin-jest": "^24.1.3",
    "eslint-plugin-jsx-a11y": "6.4.1",
    "eslint-plugin-prettier": "^3.2.0",
    "eslint-plugin-react": "7.21.5",
    "eslint-plugin-react-hooks": "4.0.0",
    "prettier": "^2.2.1"
  }
}
```

```jsonc
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
    "@typescript-eslint/explicit-module-boundary-types": 0,
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

> yarn

## command

```
npx create-react-app . --typescript

yarn add -D @typescript-eslint/eslint-plugin @typescript-eslint/parser eslint-config-airbnb-typescript eslint-plugin-jest prettier eslint-config-prettier eslint-plugin-prettier

npx install-peerdeps --dev eslint-config-airbnb

```

## use workspace typescript version
```jsonc 
{
  // (...)
  "typescript.tsdk": "node_modules\\typescript\\lib"
}
```

## eslint 재설치

```jsonc package.json
  "devDependencies": {
    "@typescript-eslint/eslint-plugin": "^4.9.0",
    "@typescript-eslint/parser": "^4.9.0",
    // "eslint": "7.2.0", // 삭제
    "eslint-config-airbnb": "18.2.1",
    "eslint-config-airbnb-typescript": "^12.0.0",
    "eslint-config-prettier": "^6.15.0",
    "eslint-plugin-import": "2.22.1",
    "eslint-plugin-jest": "^24.1.3",
    "eslint-plugin-jsx-a11y": "6.4.1",
    "eslint-plugin-prettier": "^3.2.0",
    "eslint-plugin-react": "7.21.5",
    "eslint-plugin-react-hooks": "4.0.0",
    "prettier": "^2.2.1"
  }
```
- _package.json_ 에서 eslint를 삭제한다.

```
rm -rf node_modules/ yarn.lock  
yarn
```
- 노드 모듈이랑 yarn.lock 을 삭제하고 다시 종속성을 설치한다.