# OGP画像（1200×630）

`../../ogp.png` の原本。SNS（X・LINE・Facebook・Slack）でシェアされたときのカード画像。
文言を変えたら `src.html` を直して、下を流す（パスは絶対パスで）。

```bash
"/c/Program Files/Google/Chrome/Application/chrome.exe" --headless=new --disable-gpu --hide-scrollbars \
  --window-size=1200,630 --screenshot="C:/Users/user/engineer-lp/ogp.png" \
  "file:///C:/Users/user/engineer-lp/tools/ogp/src.html"
```

- ⚠ はみ出しても警告なく切れる。**出力したPNGは必ず目で見る。**
- フォントはWindowsのもの（游明朝／游ゴシック）。Hiraginoは書いても効かない。
- 数字・実績などの主張は入れない（LP本文と同じく、一次ソースの無い数字を載せない方針）。
- ロゴは同じリポジトリ直下の `logo-white.png`（原本 `C:\Users\user\ロゴ素材\dist\`）。
