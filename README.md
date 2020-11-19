# typescript-react-eslint-prettier-practice

- typescript react 에 eslint, prettier, airbnb style guide 적용해보기

## CRA로 typescript-react 시작

```cmd terminal
npx create-react-app . --typescript

yarn add redux react-redux @types/react-redux

yarn add typesafe-actions
```

## eslint 설치

```
yarn add -D @typescript-eslint/eslint-plugin @typescript-eslint/parser eslint-config-airbnb-typescript eslint-plugin-jest

npx install-peerdeps --dev eslint-config-airbnb    <-- 물음에 y로 답해 yarn으로 설치 진행
```

## 참고

- https://medium.com/@brygrill/create-react-app-with-typescript-eslint-prettier-and-github-actions-f3ce6a571c97
