---
title: ページ読み込み時間
slug: Glossary/Page_load_time
tags:
  - Glossary
  - Timings
  - Web Performance
  - metrics
  - page load time
translation_of: Glossary/Page_load_time
---
**ページ読み込み時間**とはページの読み込みにかかる時間のことであり、[ナビゲーション開始時](/ja/docs/Web/API/PerformanceTiming/navigationStart)から[ロードイベント開始時](/ja/docs/Web/API/PerformanceTiming/loadEventStart)までをもって測定されます。

```js
let time = performance.timing;

let pageloadtime = time.loadEventStart - time.navigationStart;
```

ページ読み込み時間は完璧なウェブパフォーマンス測定基準に聞こえますが、そうではありません。読み込み時間はユーザーのデバイス性能やネットワーク状態、そして程度は低いもののサーバーからの距離によって大きく変化します。ページ読み込み時間が測定される開発環境は最適化された環境である場合が多くユーザーの実態体験を反映しません。さらにウェブパフォーマンスはロードイベント発生時間だけではありません。それは[体感速度](/ja/docs/Glossary/Perceived_performance)、応答性、[ジャンク（Jank)](/ja/docs/Glossary/Jank)、そしてジッター(Jitter)でもあります。

## See also

- [Navigation and resource timing](/ja/docs/Web/Performance/Navigation_and_resource_timings)
- {{domxref("PerformanceNavigationTiming")}}
- {{domxref("PerformanceResourceTiming")}},
