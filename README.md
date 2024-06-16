# typescript basic
- tsを使う利用その１、ブラウザの対応がjsのアップデートに追いついてないため、jsの新機能をブラウザが解析できなくなることがある。というわけでtsコンパイラが昔のjsの書き方にコンパイルすることによってjsの新しい機能などをブラウザで解読できるようになる。

## section1

### install ts

- npm install -g typescript
- -g: この folder だけではなく、すべての folder に適用させる

### complie ts

- tsc index.ts
- 上のコマンドを叩くことでコンパイルされてindex.jsファイルが出来上がる

### run js

- node index.js