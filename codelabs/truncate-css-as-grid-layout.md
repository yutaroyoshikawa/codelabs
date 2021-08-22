summary: Shallow equal と Deep equal の違い
id: truncate-css-as-grid-layout
categories: JS
status: Published
authors: yutaroyoshikawa
Feedback Link: https://github.com/yutaroyoshikawa/web-tutorial

# レスポンシブデザインの truncate css

## お品書き

- truncate とは？
- grid layout とは？
- レスポンシブデザインへの適用

## truncate とは？

- 文字列を三点リーダーで省略するやつ。
- 必要なプロパティ
- IE のことは考えない。

```css
white-space: nowrap;
overflow: hidden;
text-overflow: ellipsis;
```

### white-space

- 文字列をどのように改行するかを指定するやつ
- `nowrap` を指定すると、改行しなくなる。

### overflow

- はみ出た分のコンテンツを非表示にするか、スクロール領域にするかを指定できる。
- `hidden` を指定すると、非表示

### text-overflow

- `overflow: hidden;` ではみ出た分の文字をどう表示するかを指定できる。
- `ellipsis` を指定すると、三点リーダーで表示される。

## レスポンシブに対応させたい

```css
width: 300px;
white-space: nowrap;
overflow: hidden;
text-overflow: ellipsis;
```

- 要素幅が可変長だと、省略されない問題。
  - `width: 100%` だけでは省略されない。

### 最小サイズを指定する

- flex も grid も、特に最小サイズを指定しなければデフォルト最小幅値（ `min-width: auto;` ）は、要素幅のサイズになる。
- つまり、`min-width: auto;` は `width: 100%;` とほぼ同じ。

## レスポンシブデザインへの適用

- 基本的には、 `min-width: 0;` のような最小値を明示的に書けばいい。

```css
min-width: 0;
white-space: nowrap;
overflow: hidden;
text-overflow: ellipsis;
```

### flex layout

```css
flex: 1;
min-width: 0;
white-space: nowrap;
overflow: hidden;
text-overflow: ellipsis;
```

### grid layout

```css
grid-template-columns: minmax(0, auto);
white-space: nowrap;
overflow: hidden;
text-overflow: ellipsis;
```

## 複数行の対応

- `line-clamp` を使うと複数行での省略ができる。

```css
display: -webkit-box;
overflow: hidden;
-webkit-box-orient: vertical;  
-webkit-line-clamp: 3;
```
