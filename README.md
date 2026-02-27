[index.html](https://github.com/user-attachments/files/25602701/index.html)
<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>DAYTRADE — デイトレード管理システム</title>
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@300;400;500;700&family=Bebas+Neue&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#050507;--s1:#0c0c14;--s2:#13131e;--s3:#1a1a28;
  --c:#00d4ff;--g:#00e87d;--r:#ff3358;--y:#ffd600;--p:#b06aff;--o:#ff8c42;
  --tx:#dde0f0;--txm:#5a5a78;--txd:#8888aa;
  --bd:rgba(255,255,255,0.06);--bd2:rgba(255,255,255,0.11);
}
*{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{background:var(--bg);color:var(--tx);font-family:'Noto Sans JP',sans-serif;font-weight:300;line-height:1.75;overflow-x:hidden;min-height:100vh}

/* GRID BG */
body::before{content:'';position:fixed;inset:0;background:repeating-linear-gradient(0deg,transparent,transparent 47px,rgba(0,212,255,0.018) 47px,rgba(0,212,255,0.018) 48px),repeating-linear-gradient(90deg,transparent,transparent 47px,rgba(0,212,255,0.018) 47px,rgba(0,212,255,0.018) 48px);pointer-events:none;z-index:0}

/* GLOW */
body::after{content:'';position:fixed;top:-200px;left:50%;transform:translateX(-50%);width:800px;height:600px;background:radial-gradient(ellipse,rgba(0,212,255,0.06) 0%,transparent 70%);pointer-events:none;z-index:0}

/* HERO */
.hero{position:relative;z-index:1;max-width:900px;margin:0 auto;padding:100px 24px 64px;text-align:center}
.eyebrow{font-family:'Bebas Neue',sans-serif;font-size:11px;letter-spacing:8px;color:var(--c);opacity:.6;margin-bottom:24px;animation:fadeUp .6s ease both}
.title{font-family:'Bebas Neue',sans-serif;font-size:clamp(64px,14vw,140px);line-height:.85;letter-spacing:3px;margin-bottom:16px;animation:fadeUp .6s .1s ease both}
.title .t1{background:linear-gradient(135deg,#fff 20%,var(--c) 80%);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;display:block}
.title .t2{background:linear-gradient(135deg,var(--y) 10%,var(--o) 80%);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;display:block;font-size:60%}
.sub{font-size:12px;letter-spacing:5px;color:var(--txm);margin-bottom:28px;animation:fadeUp .6s .15s ease both}
.desc{font-size:14px;color:var(--txd);max-width:500px;margin:0 auto;line-height:2;animation:fadeUp .6s .2s ease both}

/* TICKER */
.ticker{position:relative;z-index:1;background:var(--s1);border-top:1px solid var(--bd2);border-bottom:1px solid var(--bd2);overflow:hidden;padding:10px 0;margin-bottom:0}
.ticker-track{display:flex;gap:56px;animation:ticker 24s linear infinite;width:max-content}
@keyframes ticker{0%{transform:translateX(0)}100%{transform:translateX(-50%)}}
.t-item{font-family:'Bebas Neue',sans-serif;font-size:12px;letter-spacing:2px;display:flex;align-items:center;gap:8px;white-space:nowrap}
.t-up{color:var(--g)}.t-dn{color:var(--r)}.t-yl{color:var(--y)}.t-sep{color:var(--txm);font-size:8px}

/* PAGES GRID */
.pages{position:relative;z-index:1;max-width:900px;margin:0 auto;padding:64px 24px 80px;display:grid;grid-template-columns:1fr 1fr;gap:16px}
@media(max-width:600px){.pages{grid-template-columns:1fr}}

.page-card{background:var(--s1);border:1px solid var(--bd);border-radius:10px;padding:32px 28px;text-decoration:none;display:block;position:relative;overflow:hidden;transition:transform .25s,box-shadow .25s,border-color .25s;animation:fadeUp .6s ease both}
.page-card:hover{transform:translateY(-4px)}
.page-card::before{content:'';position:absolute;inset:0;opacity:0;transition:opacity .3s}
.page-card:hover::before{opacity:1}

/* card colors */
.card-guide{border-top:3px solid var(--c)}
.card-guide:hover{border-color:var(--c);box-shadow:0 8px 40px rgba(0,212,255,0.12)}
.card-guide::before{background:radial-gradient(ellipse at top left,rgba(0,212,255,0.06),transparent 70%)}

.card-strategy{border-top:3px solid var(--y)}
.card-strategy:hover{border-color:var(--y);box-shadow:0 8px 40px rgba(255,214,0,0.1)}
.card-strategy::before{background:radial-gradient(ellipse at top left,rgba(255,214,0,0.06),transparent 70%)}

.card-journal{border-top:3px solid var(--p)}
.card-journal:hover{border-color:var(--p);box-shadow:0 8px 40px rgba(176,106,255,0.1)}
.card-journal::before{background:radial-gradient(ellipse at top left,rgba(176,106,255,0.06),transparent 70%)}

.card-tool{border-top:3px solid var(--g)}
.card-tool:hover{border-color:var(--g);box-shadow:0 8px 40px rgba(0,232,125,0.1)}
.card-tool::before{background:radial-gradient(ellipse at top left,rgba(0,232,125,0.06),transparent 70%)}

.card-vol{font-family:'Bebas Neue',sans-serif;font-size:10px;letter-spacing:4px;margin-bottom:14px;opacity:.5}
.card-guide .card-vol{color:var(--c)}
.card-strategy .card-vol{color:var(--y)}
.card-journal .card-vol{color:var(--p)}
.card-tool .card-vol{color:var(--g)}

.card-icon{font-size:36px;margin-bottom:16px;display:block}
.card-title{font-family:'Bebas Neue',sans-serif;font-size:30px;letter-spacing:3px;line-height:1.1;margin-bottom:10px;color:#fff}
.card-en{font-size:10px;letter-spacing:3px;color:var(--txm);margin-bottom:16px;display:block}
.card-desc{font-size:12.5px;color:#9090aa;line-height:1.85;margin-bottom:20px}
.card-tags{display:flex;flex-wrap:wrap;gap:6px}
.ctag{font-size:10px;letter-spacing:1px;padding:2px 8px;border-radius:2px;border:1px solid var(--bd2);color:var(--txm)}
.card-guide .ctag{border-color:rgba(0,212,255,0.2);color:rgba(0,212,255,0.6)}
.card-strategy .ctag{border-color:rgba(255,214,0,0.2);color:rgba(255,214,0,0.6)}
.card-journal .ctag{border-color:rgba(176,106,255,0.2);color:rgba(176,106,255,0.6)}
.card-tool .ctag{border-color:rgba(0,232,125,0.2);color:rgba(0,232,125,0.6)}

.card-arrow{position:absolute;bottom:24px;right:24px;font-family:'Bebas Neue',sans-serif;font-size:13px;letter-spacing:2px;opacity:.3;transition:opacity .2s,transform .2s}
.page-card:hover .card-arrow{opacity:.8;transform:translateX(4px)}
.card-guide .card-arrow{color:var(--c)}
.card-strategy .card-arrow{color:var(--y)}
.card-journal .card-arrow{color:var(--p)}
.card-tool .card-arrow{color:var(--g)}

/* ANIM DELAYS */
.page-card:nth-child(1){animation-delay:.25s}
.page-card:nth-child(2){animation-delay:.32s}
.page-card:nth-child(3){animation-delay:.39s}
.page-card:nth-child(4){animation-delay:.46s}

@keyframes fadeUp{from{opacity:0;transform:translateY(20px)}to{opacity:1;transform:translateY(0)}}

/* FOOTER */
footer{position:relative;z-index:1;background:var(--s1);border-top:1px solid var(--bd2);padding:28px 24px;text-align:center;font-size:11px;color:var(--txm);letter-spacing:2px;line-height:2.4}
footer a{color:var(--txd);text-decoration:none}
footer a:hover{color:var(--c)}
</style>
</head>
<body>

<!-- HERO -->
<header class="hero">
  <p class="eyebrow">PERSONAL TRADING SYSTEM</p>
  <h1 class="title">
    <span class="t1">DAYTRADE</span>
    <span class="t2">MANAGEMENT</span>
  </h1>
  <p class="sub">デイトレード管理システム — 完全ガイド・戦略・日誌・ツール</p>
  <p class="desc">基礎知識から取引ルール・日誌・リアルタイム管理ツールまで、<br>自分のトレードを一元管理するパーソナルシステム。</p>
</header>

<!-- TICKER -->
<div class="ticker">
  <div class="ticker-track">
    <span class="t-item"><span class="t-up">▲ 日経225</span><span class="t-sep">◆</span>Nikkei 225</span>
    <span class="t-item"><span class="t-yl">⚡ 1%ルール</span><span class="t-sep">◆</span>ポジションサイズ</span>
    <span class="t-item"><span class="t-up">▲ 半導体</span><span class="t-sep">◆</span>SEMICONDUCTOR</span>
    <span class="t-item"><span class="t-dn">▼ 損切り</span><span class="t-sep">◆</span>STOP LOSS</span>
    <span class="t-item"><span class="t-up">▲ 重工業</span><span class="t-sep">◆</span>HEAVY INDUSTRY</span>
    <span class="t-item"><span class="t-yl">⚡ PDCA</span><span class="t-sep">◆</span>週次検証</span>
    <span class="t-item"><span class="t-up">▲ 勝率</span><span class="t-sep">◆</span>WIN RATE ≥55%</span>
    <span class="t-item"><span class="t-dn">▼ 日次上限</span><span class="t-sep">◆</span>DAILY LIMIT −3%</span>
    <span class="t-item"><span class="t-up">▲ RR比</span><span class="t-sep">◆</span>RISK REWARD ≥1.5</span>
    <span class="t-item"><span class="t-yl">⚡ エクイティカーブ</span><span class="t-sep">◆</span>EQUITY CURVE</span>
    <span class="t-item"><span class="t-up">▲ 日経225</span><span class="t-sep">◆</span>Nikkei 225</span>
    <span class="t-item"><span class="t-yl">⚡ 1%ルール</span><span class="t-sep">◆</span>ポジションサイズ</span>
    <span class="t-item"><span class="t-up">▲ 半導体</span><span class="t-sep">◆</span>SEMICONDUCTOR</span>
    <span class="t-item"><span class="t-dn">▼ 損切り</span><span class="t-sep">◆</span>STOP LOSS</span>
    <span class="t-item"><span class="t-up">▲ 重工業</span><span class="t-sep">◆</span>HEAVY INDUSTRY</span>
    <span class="t-item"><span class="t-yl">⚡ PDCA</span><span class="t-sep">◆</span>週次検証</span>
    <span class="t-item"><span class="t-up">▲ 勝率</span><span class="t-sep">◆</span>WIN RATE ≥55%</span>
    <span class="t-item"><span class="t-dn">▼ 日次上限</span><span class="t-sep">◆</span>DAILY LIMIT −3%</span>
    <span class="t-item"><span class="t-up">▲ RR比</span><span class="t-sep">◆</span>RISK REWARD ≥1.5</span>
    <span class="t-item"><span class="t-yl">⚡ エクイティカーブ</span><span class="t-sep">◆</span>EQUITY CURVE</span>
  </div>
</div>

<!-- PAGE CARDS -->
<div class="pages">

  <a href="daytrade-all-in-one.html" class="page-card card-guide">
    <div class="card-vol">COMPLETE GUIDE — VOL.0</div>
    <span class="card-icon">📚</span>
    <h2 class="card-title">完全ガイド</h2>
    <span class="card-en">DAYTRADE COMPLETE GUIDE</span>
    <p class="card-desc">板読み・ローソク足・テクニカル指標・チャートパターン・銘柄選び・信用取引・税金まで全18セクション。TradingViewのリアルタイムチャートも搭載。</p>
    <div class="card-tags">
      <span class="ctag">板読み</span>
      <span class="ctag">チャート分析</span>
      <span class="ctag">信用取引</span>
      <span class="ctag">税金</span>
      <span class="ctag">リアルタイム株価</span>
    </div>
    <span class="card-arrow">→ OPEN</span>
  </a>

  <a href="strategy-book.html" class="page-card card-strategy">
    <div class="card-vol">STRATEGY BOOK — VOL.1</div>
    <span class="card-icon">📋</span>
    <h2 class="card-title">戦略ブック</h2>
    <span class="card-en">PERSONAL RULEBOOK</span>
    <p class="card-desc">自分のKPI・固定取引ルール・半導体／重工業のエントリーパターン・リスク管理計算式・用語集をまとめたマスタードキュメント。</p>
    <div class="card-tags">
      <span class="ctag">KPI・目標</span>
      <span class="ctag">取引ルール</span>
      <span class="ctag">半導体</span>
      <span class="ctag">重工業</span>
      <span class="ctag">用語集</span>
    </div>
    <span class="card-arrow">→ OPEN</span>
  </a>

  <a href="trade-journal.html" class="page-card card-journal">
    <div class="card-vol">JOURNAL & PDCA — VOL.2</div>
    <span class="card-icon">📓</span>
    <h2 class="card-title">日誌・検証ログ</h2>
    <span class="card-en">TRADE JOURNAL & PDCA</span>
    <p class="card-desc">毎日の日誌テンプレ・1トレード記録シート・週次PDCAフォーマット・月次レビューの手順をまとめた記録ハブ。感情の記録が最大の資産になる。</p>
    <div class="card-tags">
      <span class="ctag">日次日誌</span>
      <span class="ctag">PDCA</span>
      <span class="ctag">検証ログ</span>
      <span class="ctag">月次レビュー</span>
    </div>
    <span class="card-arrow">→ OPEN</span>
  </a>

  <a href="trade-tool.html" class="page-card card-tool">
    <div class="card-vol">MANAGEMENT TOOL — VOL.3</div>
    <span class="card-icon">⚙️</span>
    <h2 class="card-title">取引管理ツール</h2>
    <span class="card-en">TRADE MANAGEMENT TOOL</span>
    <p class="card-desc">口座資金から1%リスク額を自動計算。取引履歴の記録・勝率・エクイティカーブ・時間帯別分析・CSVエクスポート。日次−3%で画面ロック機能付き。</p>
    <div class="card-tags">
      <span class="ctag">自動計算</span>
      <span class="ctag">勝率グラフ</span>
      <span class="ctag">エクイティカーブ</span>
      <span class="ctag">CSV出力</span>
      <span class="ctag">日次ロック</span>
    </div>
    <span class="card-arrow">→ OPEN</span>
  </a>

</div>

<footer>
  <p style="font-size:13px;letter-spacing:1px;color:var(--txd);margin-bottom:6px">DAYTRADE MANAGEMENT SYSTEM</p>
  <p>デイトレード完全ガイド ／ 戦略ブック ／ 日誌・検証ログ ／ 取引管理ツール</p>
  <p style="margin-top:4px">投資にはリスクが伴います。余裕資金の範囲内で、自己責任のもとに取引を行いましょう。</p>
</footer>

</body>
</html>
