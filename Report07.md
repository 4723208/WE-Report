# 第7回 Webエンジニアリング演習 レポート
## 学籍番号(名前は書かなくてよい)
4723208
## PUTリクエスト検証用のモデルとAPI部分のコード
Request:
```json
{
  "title": "GFPのレポート作成",
  "description": "次の時間にやる",
  "completed": false
}

curl -X 'POST' \
  'http://localhost:8000/todos/5' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "title": "GFPのレポート作成",
  "description": "次の時間にやる",
  "completed": false
}'
```

Swagger UIでのPUTエンドポイントテスト結果

正常系：存在するタスクの更新
```json
{
  "id": 2,
  "title": "string",
  "description": "string",
  "completed": true
}

```
異常系：存在しないタスクIDでのエラー確認
```json
{
  "detail": "TODOが見つからない"
}
```