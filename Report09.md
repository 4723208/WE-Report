# 第9回 Webエンジニアリング演習 レポート
## 学籍番号(名前は書かなくてよい)
4723208
## frontend/calculator.tsのプログラム

```ts
export function add(number1: number, number2: number): number{
    return number1 + number2;
}

export function multiply(number1: number, number2: number): number{
    return number1 * number2;
}
```



## 動作確認結果
```
@4723208 ➜ /workspaces/WE-TypeScript/frontend (main) $ npx tsc main.ts
@4723208 ➜ /workspaces/WE-TypeScript/frontend (main) $ node main.js
5 + 3 = 8
5 * 3 = 15
```
