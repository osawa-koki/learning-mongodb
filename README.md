# learning-mongodb

ð¦ð¦ð¦ ãã­ã¥ã¡ã³ãæåãã¼ã¿ãã¼ã¹ãMongoDBãå­¦ã¶ã  

## å®è¡æ¹æ³

```shell
docker compose up mongo -d
docker compose up mongo-express -d
```

<http://localhost:8080/>ã¸ã¢ã¯ã»ã¹ã  
ç®¡çèç»é¢(mongo-express)ãè¡¨ç¤ºãããã  

---

ã³ã³ããã®ã·ã§ã«ããç´æ¥æä½ãããã¨ãå¯è½ã  

```shell
# ã³ã³ããã«å¥ã
docker-compose exec mongo bash

# MongoDBãã­ã³ããã«å¥ã(password)
mongosh admin -u root -p

# ãã¼ã¿ãã¼ã¹ã®ä½æ(åãæ¿ã)
use <ãã¼ã¿ãã¼ã¹å>

# ãã¼ã¿ã®è¿½å 
db.<ã³ã¬ã¯ã·ã§ã³å>.insertOne({ name: "hogehoge", property1: "foofoo", property2: "foofoo", property3: "foofoo" })
db.<ã³ã¬ã¯ã·ã§ã³å>.insertMany([{ name: "hoge1" }, { name: "hoge2" }, { name: "hoge3" }])

# ãã¼ã¿ã®åç§
db.<ã³ã¬ã¯ã·ã§ã³å>.find({name: "hogehoge"})

# ãã¼ã¿ã®åé¤
db.<ã³ã¬ã¯ã·ã§ã³å>.deleteOne({name: "hogehoge"})
db.<ã³ã¬ã¯ã·ã§ã³å>.deleteMany({name: "hogehoge"})

# ãã¼ã¿ã®æ´æ°
db.<ã³ã¬ã¯ã·ã§ã³å>.update(
  { name: "hoge" }, # æ¡ä»¶
  { $set: { property1: "foofoo", property2: "foofoo", property3: "foofoo" } } # ã»ããããå¤
)
db.<ã³ã¬ã¯ã·ã§ã³å>.update(
  { name: "hoge" }, # æ¡ä»¶
  { $push: { ary: "foofoo" } } # ããã·ã¥ããå¤(éåç¨)
)
db.<ã³ã¬ã¯ã·ã§ã³å>.update( # å¹´é½¢ã30æªæºã®hogeããã«ãå¹´é½¢ã«1ãå ç®ãã
  { name: "hoge", age: { $lt: 30 } },
  { $inc: { age: 1 } }
)
```
