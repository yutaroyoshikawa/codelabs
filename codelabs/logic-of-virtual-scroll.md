summary: 仮想スクロールの仕組み
id: logic-of-virtual-scroll
categories: JS
status: Published
authors: yutaroyoshikawa
Feedback Link: https://github.com/yutaroyoshikawa/web-tutorial

# 仮想スクロールの仕組み

## お品書き

- 仮想スクロールとは？
- react-window
- 仮想スクロールの仕組み
- 可変幅の対応

## 仮想スクロールとは？

- スクロール要素のマウント状態を管理することで、非常に要素数の多いリストの表示もパフォーマンスを劣化させずに表示する方法
- １ページには DOM の数を 1500 以下に抑えることが推奨されている。
- [web.dev](https://web.dev/dom-size/)

## react-window

- react で仮想スクロールを実現するためのライブラリ
- 無限スクロールを実装することも可能。
- [demo](https://react-window.vercel.app/#/examples/list/fixed-size)
## 仮想スクロールの仕組み

- スクロール方向の要素幅を取得する。
- 要素数とスクロール方向の要素幅からリスト全体の幅を算出する。
- リストのスクロールイベントが発火した時にスクロール量から表示すべき要素をマウントする。
- マウントするリスト要素に `position: absolute` を設定し、表示すべき位置を管理することでスクロールしているように見える。

## 可変幅の対応

- 仮想スクロール要素を resizeObserber で監視することで、サイズが変わった時に仮想スクロールに要素幅を渡すことができる。
- バブリングが発生し、処理が重たいので、`matchMedia()` などでブレークポイントを設定するのもあり。
