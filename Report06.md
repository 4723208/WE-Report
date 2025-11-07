# 第6回 Webエンジニアリング演習 レポート
## 学籍番号(名前は書かなくてよい)
4723208
## 各エンドポイントのSwagger UIでのテスト結果
### GET /
Request:
```json
curl -X 'GET' \
  'http://127.0.0.1:8000/todos?query=%E7%89%9B%E4%B9%B3' \
  -H 'accept: application/json'
```

Response:
```json
[
  {
    "id": 1,
    "title": "牛乳とパンを買う",
    "description": "牛乳は低温殺菌じゃないとだめ",
    "completed": false
  }
]
```