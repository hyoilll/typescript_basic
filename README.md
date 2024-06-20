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

## section2

### 型検査
- ts -> (tsc) -> js -> (js engine) -> 機械語
- tsc: 静的型付け
- js engine: 動的型付け

### number型について
- tsでは他の言語とは違って、`float`型の値も`number`型として扱う

### 型注釈 vs 型推論
- 型注釈: `const a: string`のように明示的に型定義するタイプ
- 型推論: `const a = 'test'`のように`'test'`を代入することにより、vscodeに組み込まれているtsコンパイラが肩を推論してくれるタイプ
- 基本的には`型推論`を使うことにして、`型推論`が使えない時には`型注釈`を使う
- 関数のパラメータには`型注釈`を使えばよい。`function testFunc(a: number, b: number)`

### object型
- 以下のようにobjectの型を定義することにより、`obj.`にすると`name`と`age`属性がeditor上に出てくるようになって（補完）使いやすくなる利点がある。
```ts
interface TypeObj = {
  name: string,
  age: number,
}
const obj: TypeObj = {
  name: 'Jack',
  age: 21,
}
```
- 以下のように`object`型が存在はしているが、それは文字のまま`object`であることを示しているだけで、どの属性をもっているかまでには定義されていないので、属性にアクセスしようとするとエラーが出る。
```ts
const obj: object = {
  name: 'Jack',
  age: 21,
}
console.log(obj.name) // error
```

### array型
- 指定した型以外の型は入れれなくなる。
```ts
const arr: string[] = ['1', '2'] // OK
const arr: string[] = ['1', 2] // NG
```

### tuble型
- 色んな型を許容し、決まったタイプのみOK
```ts
const book: [string, number, boolean] = ['hello', 1200, true] // OK
const book: [string, number, boolean] = ['hello', 1200, true, false] // NG
```

### enum（列挙型）
- 特定のまとまった型のみ受け入れる
- enumのkeyは全て大文字にする
- object使うバージョン
```ts
const CoffeeSize = {
  SHORT: 'SHORT',
  TALL: 'TALL',
}
const coffee = {
  hot: true,
  size: CoffeeSize.SHORT // string型
}
coffee.size = 'temp' // coffee.sizeはstring型なのでエラーにならない
```
- enum使うバージョン
```ts
enum CoffeeSize {
  SHORT = 'SHORT',
  TALL = 'TALL'
}
const coffee = {
  hot: true,
  size: CoffeeSize.SHORT // CoffeeSize型
}
coffee.size = 'temp' // coffee.sizeはCoffeeSize型型なのでエラーになる
```