summary: React 18 ハンズオン
id: react-18
categories: JS
status: Published
authors: yutaroyoshikawa
Feedback Link: https://github.com/yutaroyoshikawa/react-18

# React 18 ハンズオン

## お品書き

- 追加された hooks
- Suspence
- Conccurent Rendering
- useTransition
- useSyncExternalStore
- React Server Components

## 追加された hooks

### useId

- SSR 時と CSR 時に共通した UUID を生成してくれる hook

```tsx
const Component = () => {
  const id = useId();

  return (

  );
}
```

### use
