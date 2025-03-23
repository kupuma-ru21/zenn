---
title: "VSCodeでタブを切り替えてもカーソル位置をキープ！Cursorghostを作った話"
emoji: "🧙‍♂️"
type: "tech" # tech or idea
topics: ["vscode", "extension", "cursor", "typescript"]
published: true
slug: "vscode-cursorghost-extension"
---

VSCodeで複数ファイルを編集しているとき、タブを切り替えた際に「さっきのカーソル位置どこだっけ…？」ってなること、ありませんか？

私はこの問題に悩まされていたので、自作で解決しました。

## 🧠 作った拡張機能：Cursorghost

[🔗 Cursorghost - Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=kupuma-ru21.Cursorghost)

この拡張機能は、**ファイルタブを切り替えたときにカーソル位置をタブ間で自動で同期する**というextensionです。

---

## 🎯 解決したかった課題

VSCodeで複数タブを行き来しながら編集していると、**どこを編集していたのか見失う**ことが多々ありました。

---

## 🔨 どうやって実装したか

Cursorghostは以下のような仕組みで動いています：

- `onDidChangeActiveTextEditor` を使ってアクティブなタブの変化を検知
- タブを離れるときに、そのファイルとカーソルのlineを記録
- 再びそのタブに戻ったとき、自動的にそのlineにカーソルを移動

実装はTypeScriptで書いています。
拡張のコードはGitHubにも公開しているので、興味がある方はぜひ見てください👇

🔗 [GitHub - kupuma-ru21/cursorghost](https://github.com/kupuma-ru21/cursorghost)

---

## 🚀 使い方

1. VSCodeの拡張機能で `Cursorghost` を検索
2. インストール
3. タブを切り替えるだけでOK！

設定不要で、自動的にカーソルを記憶・復元してくれます。

---

## 🙏 最後に

「ちょっと便利な改善」で、コーディング体験は大きく変わると実感しました。

この記事が役に立ったら、ぜひ拡張機能の⭐️やZennのいいねで応援してもらえると嬉しいです！
