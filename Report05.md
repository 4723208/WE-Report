# 第5回 Webエンジニアリング演習 レポート
## 学籍番号(名前は書かなくてよい)
4723208
## 各エンドポイントのSwagger UIでのテスト結果
### GET /
Request:
```json
curl -X 'GET' \
  'http://127.0.0.1:8000/items/-1?q=test' \
  -H 'accept: application/json'
```

Response:
```json
{
  "detail": "Item ID must be positive"
}
```