# engineer-lp — 未経験からエンジニア転職LP（求職者向け）

- 公開URL: https://engineer.agent-best.net/ （GitHub Pages・HTTPS強制）
- 構成: `index.html` 1ファイル完結。CSS/JSはインライン、**外部CDNは読み込まない**。`CNAME` あり。

## ⚠ 名前が紛らわしいので注意

- **これ** ＝ `engineer.agent-best.net` / `agentbest/engineer-lp` / 他業種→**エンジニア**になりたい人向け
- **別物** ＝ `eng.agent-best.net` / `agentbest/engineer-consultant` ＝ **エンジニア→コンサル**
- 旧 `inexperiencedengineer.agent-best.net`（Tailwind CDN版・2025年制作）の後継。**旧リポジトリの扱いは未決**。削除するならDNSのCNAMEも一緒に消さないと**サブドメイン乗っ取りリスク**がある。301リダイレクト化を推奨として提示済み・返答待ち。

## ターゲットと訴求（誠実さを設計に組み込んでいる）

他業種からITエンジニアを目指す層（20〜30代）。

- ヒーロー「**「未経験OK」だけで選ぶと、3年後に困る。**」
- 核になる事実: 経産省「IT人材需給に関する調査」は2030年に最大79万人不足とする一方、**従来型IT人材はむしろ余剰・不足するのは先端IT人材**と試算している。この非対称性を正面から使い、「入れるか」ではなく「入った先で伸びるか」に論点を移す。
- ヒーロー図は **「3年後の分岐」2ルート図**（ルートA＝入口だけで決めた場合／ルートB＝3年後から逆算した場合）。
- 入口の3条件: 開発工程に入れるか／教えてくれる人がいるか／技術構成が古すぎないか。
- **学習セクションで「スクールは必須ではない」と明言**。当社はスクールの運営も紹介もしていないので中立に答えられる、と書いている。**この中立性の主張を崩す変更（スクール送客等）は入れない。**
- 「今は転職ではなく社内でIT寄りの業務に近づくほうが早い」と伝えることもある、と明記。

## デザイン

ブルー（#1F6FEB系）×シアン、丸みのある太ゴシック、角丸大きめ。**明朝は使わない**（ma-lpとの差別化）。

---

## 求職者向けLP 共通ルール

- **CTA**（「話を聞いてみる」「無料で相談する」「面談予約」）のリンクは `https://calendly.com/r_matsuoka` 固定。`target="_blank" rel="noopener"` で開く。
- **GA4 測定ID** `G-1XXMP8Y1B4`（全サブドメイン共通プロパティ）。
- **ダークモード対応**（`prefers-color-scheme` ＋ `[data-theme]` の両対応）を壊さない。
- 事例・行き先は**社名・ロゴを出さない匿名アーキタイプ**で書く。
- 掲載する数字は**必ず一次ソース付き**。出典が取れない数字は載せず、空欄のままにする。架空の利用者の声や根拠のない自社指標（「年収アップ率○%」「独占求人多数」等）は入れない。
- 棒グラフの `.track` / `.fill` を `<span>` で書くと**描画されない**（inline要素なので width/height が効かない）。`display:block` が必要。pm-lp由来の既知バグで、他LPにも伝播している可能性が高い。
- ローカルプレビューは `file://` だと確認できないので、簡易HTTPサーバー（node）を立てて `http://localhost:<port>/` で見る。

## 相互リンク（求職者向け8本）

| サブドメイン | 内容 | リポジトリ |
|---|---|---|
| pm | PM特化 転職 | agentbest/pm-lp |
| eng | エンジニア→コンサル転職 | agentbest/engineer-consultant |
| ma | 未経験からM&A | agentbest/ma-lp |
| consul | 未経験からコンサル | agentbest/consultant-lp |
| engineer | 未経験からエンジニア | agentbest/engineer-lp |
| embedded | IoT・組込みエンジニア | agentbest/embedded-lp |
| consultingcareerchange50 | ファーム出身者の次のキャリア（50代） | agentbest/consultingcareerchange50 |
| student | 学生キャリア支援 | agentbest/student-career |

フッターに `.ft-links` を再利用した2つ目のnav（`ft-sites-links`）で自分以外の7本を並べる。**新しいLPを足したら既存全部＋コーポレート `agentbest/agentbest-lp` の `src/components/Header.astro` の `specialSites['求職者の方へ']` も更新する。片方向にしない。**

⚠ 一括置換の罠: アンカーに `ft-sites-links` の文字列だけを使うと `<style>` 内のCSS定義にマッチして**ヘッダーnavに誤挿入される**（student-careerで実際にやらかした）。`<nav class="ft-links ft-sites-links">` のようにタグごと指定すること。

採用企業向け（B2B）4本（scout / green / infra / scoutdaikou_offerbox）は読み手が違うので、この相互リンクには**意図的に含めない**。

## push のルール

- ローカルで動作確認（ブラウザ表示・構文チェック）を済ませた変更は、**確認を取らずに commit & push してよい**。コミットメッセージは日本語。**push後は必ず何を変えたか報告する**（無言でpushしない）。
- **以下に触れるときは必ず止まって事前確認する**:
  1. ドメイン・DNS・CNAME（DNSは**Squarespace Domains**管理・松岡さんの手作業）
  2. 個人情報・フォーム・認証
  3. 費用が発生する変更
  4. 既存ページ・データの削除
  5. 複数リポジトリへの一括変更（相互リンク更新など）
- Publicリポジトリ。push前にトークン・APIキーの混入をgrepで確認する。
- `main` への push = **即本番公開**。
