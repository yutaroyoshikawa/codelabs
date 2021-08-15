summary: Shallow equal と Deep equal の違い
id: shallow-equal-vs-deep-equal
categories: JS
status: Published
authors: yutaroyoshikawa
Feedback Link: https://github.com/yutaroyoshikawa/web-tutorial

# Shallow equal と Deep equal の違い

## お品書き

- Deep equal is 何
- Flux
- Shallow equal

## Deep equal is 何

- 厳密等価のこと（===）
- JS ではオブジェクト型では参照渡しが基本なので値渡しするには一工夫必要
- オブジェクト型での厳密等価ではポインタが同じかどうかをチェックしている。
- JS においての null はオブジェクト判定されるが実体はプリミティブなので例外(そもそも typeof null === "object" なのはバグ)
- ちなみにプリミティブ型での厳密等価では変数の値を比較している。

## Flux

- JS が関数型言語としての使い方がされるようになってきた。
- 状態と振る舞いを切り離して、副作用を起こさないようにするためには、オブジェクトの参照渡しは不都合があった。
- Flux という MVVM のようなアーキテクチャが登場して、データの流れを一方向にする動きが主流になった。
- web では、パフォーマンスチューニング手法の一つとして差分レンダリングというものがある。
- web においての宣言的 UI は、一方向のデータの流れで管理されている状態変数によって管理されている。
- その状態変数が変更されたことを検知したら、DOM を変更掛けるようにして、更新回数や更新箇所を最小限に抑えている。
- Flux アーキテクチャや仮想 DOM は、一つの大きなオブジェクトで状態を管理しているので、Deep equal(厳密等価)では差分検知をすることができない。
- それで必要になるのが Shallow Equal である。

## Shallow equal

- Shallow Equal とは、Object のプロパティ値が全て一致しているかどうかをチェックして、参照先が違うオブジェクトを等価チェックする方法。

[shallo equal の実装例](https://codesandbox.io/s/youthful-wildflower-brd1j?file=/src/shallowEqual.ts)

- 多段ネストしているオブジェクトでは、参照先が一致していれば `true` が返る
- useReducer においての shallow equal は、store 全体を shallow equal しているのではなく、必要なプロパティを取り出して shallow equal している。
