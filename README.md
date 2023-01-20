# learning-mongodb

🦎🦎🦎 ドキュメント指向データベース、MongoDBを学ぶ。  

## 実行方法

```shell
docker compose up mongo -d
docker compose up mongo-express -d
```

<http://localhost:8080/>へアクセス。  
管理者画面(mongo-express)が表示される。  

---

コンテナのシェルから直接操作することも可能。  

```shell
# コンテナに入る
docker-compose exec mongo bash

# MongoDBプロンプトに入る(password)
mongosh admin -u root -p

# データベースの作成(切り替え)
use <データベース名>

# データの追加
db.<コレクション名>.insertOne({ name: "hogehoge", property1: "foofoo", property2: "foofoo", property3: "foofoo" })
db.<コレクション名>.insertMany([{ name: "hoge1" }, { name: "hoge2" }, { name: "hoge3" }])

# データの参照
db.<コレクション名>.find({name: "hogehoge"})

# データの削除
db.<コレクション名>.deleteOne({name: "hogehoge"})
db.<コレクション名>.deleteMany({name: "hogehoge"})

# データの更新
db.<コレクション名>.update(
  { name: "hoge" }, # 条件
  { $set: { property1: "foofoo", property2: "foofoo", property3: "foofoo" } } # セットする値
)
db.<コレクション名>.update(
  { name: "hoge" }, # 条件
  { $push: { ary: "foofoo" } } # プッシュする値(配列用)
)
db.<コレクション名>.update( # 年齢が30未満のhogeさんに、年齢に1を加算する
  { name: "hoge", age: { $lt: 30 } },
  { $inc: { age: 1 } }
)
```
