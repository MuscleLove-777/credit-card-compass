# クレカコンパス - スケジュールエージェントガイド

毎日JST 09:55起動、クレジットカードの最新キャンペーン・改定情報を3記事生成。

## 1日のタスク
1. WebSearchで「クレカ ランキング 2026」「楽天カード キャンペーン」「JCB CARD W 入会特典」「dカード GOLD 改定」「アメックス 比較」等から3トピック、既存articles/と重複なし
2. Unsplash画像3枚 (`site:unsplash.com credit card`, `wallet`, `shopping payment` 等、`?w=1600&h=900&fit=crop`)
3. 記事3本 `articles/YYYY-MM-DD-<slug>.html` 1200-1800字、h2 2-3個
4. index.htmlのblog-grid最新6件、stat-articles更新、blog-empty削除
5. sitemap.xmlに新3本追記
6. IndexNow通知 (indexnow-key.txt → POST)
7. git push `[auto] Add daily articles YYYY-MM-DD`

## 執筆ルール
- 日本語、家計改善・経済圏ユーザー目線で実用的に
- タイトル28-40字、年会費・還元率・特典を含める
- 末尾に「キャンペーン条件・年会費・還元率は変動するため公式サイト確認推奨」必須
- 「絶対お得」「100%還元」等の誇張NG
- 個人の信用状況・与信判断について断定的表現NG（資金需要法/景表法配慮）
- 実在人物画像NG、Unsplashのみ
- フッターのMuscleLove広告+7部作リンクは全ページ必須

## 外部リンク張る時は必ず到達確認（最重要）
記事内で公式サイト・サービスへの外部リンクを張る時、URL を書く前に必ず `curl -sI -m 10 -L "<URL>" -A "Mozilla/5.0" | head -1` で HTTP 200/301/302 を確認すること。
- 採用OK: 200/301/302
- 採用NG: 404/410/0(DNS失敗)/5xx
- NGなら公式トップURLに格上げ、それも無理なら掲載しない
- 推測でURLを書くな（「ブランド名から想像して例えば https://brand.com/foo/」みたいな組み立て厳禁）
- 必ず公式サイトトップ or 公式の検索結果上位から採取

## 記事HTMLテンプレート
```html
<!DOCTYPE html><html lang="ja"><head>
<meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>{{タイトル}} | クレカコンパス</title>
<meta name="description" content="{{150字以内}}">
<link rel="canonical" href="https://musclelove-777.github.io/credit-card-compass/articles/{{slug}}.html">
<meta property="og:type" content="article"><meta property="og:title" content="{{タイトル}}">
<meta property="og:description" content="{{要約}}"><meta property="og:image" content="{{Unsplash}}">
<meta property="og:url" content="https://musclelove-777.github.io/credit-card-compass/articles/{{slug}}.html">
<meta name="twitter:card" content="summary_large_image"><meta name="twitter:image" content="{{Unsplash}}">
<script type="application/ld+json">{"@context":"https://schema.org","@type":"Article","headline":"{{タイトル}}","image":"{{Unsplash}}","datePublished":"{{YYYY-MM-DD}}","author":{"@type":"Organization","name":"クレカコンパス"}}</script>
<link rel="stylesheet" href="../assets/style.css"></head><body>
<nav class="filter-nav"><a href="../index.html" class="filter-btn">← トップに戻る</a></nav>
<main class="article-body">
<img class="article-hero-img" src="{{Unsplash}}" alt="{{タイトル}}">
<p class="article-meta">📅 {{YYYY-MM-DD}} · 🏷️ {{カテゴリ}}</p>
<h1>{{タイトル}}</h1>
<p>{{リード}}</p>
<h2>{{見出し1}}</h2><p>{{本文}}</p>
<h2>{{見出し2}}</h2><p>{{本文}}</p>
<h2>まとめ</h2><p>{{結論+CTA}}</p>
<p style="color:#6b7280;font-size:0.8rem;margin-top:40px;">※ クレジットカードの年会費・還元率・特典・キャンペーン条件は各社の予告なく変更されます。最新情報は必ず各社公式サイトでご確認ください。審査・与信判断は各社が独自に行います。</p>
<a href="../index.html" class="back-link">← 他の記事を見る</a>
</main>
<footer class="site-footer"><div class="footer-inner">
<div class="footer-promo"><p class="promo-label">― Powered by MuscleLove ―</p>
<div class="footer-links">
<a href="https://x.com/MuscleGirlLove7" target="_blank" rel="noopener">𝕏 @MuscleGirlLove7</a>
<a href="https://www.patreon.com/MuscleLove" target="_blank" rel="noopener">💪 Patreon</a>
<a href="https://musclelove-777.github.io/ai-fukugyo-compass/" target="_blank" rel="noopener">🧭 AI副業</a>
<a href="https://musclelove-777.github.io/ai-tenshoku-compass/" target="_blank" rel="noopener">🚀 AI転職</a>
<a href="https://musclelove-777.github.io/ai-money-compass/" target="_blank" rel="noopener">💰 AIマネー</a>
<a href="https://musclelove-777.github.io/furusato-compass/" target="_blank" rel="noopener">🍱 ふるさと納税</a>
<a href="https://musclelove-777.github.io/hikari-compass/" target="_blank" rel="noopener">📡 光回線</a>
<a href="https://musclelove-777.github.io/sim-compass/" target="_blank" rel="noopener">📱 格安SIM</a>
</div></div>
<p class="copyright">© 2026 クレカコンパス</p></div></footer>
</body></html>
```

## 守ること
- 毎日3本、タイトル重複NG
- 与信・審査の保証表現NG
- pages.yml は変更しない
- 7部作姉妹サイト全リンク必須
