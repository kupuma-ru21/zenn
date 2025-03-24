---
title: "VSCodeのdiffエディタでカーソル位置をキープ！Cursorghostを作った話"
emoji: "🧙‍♂️"
type: "tech"
topics: ["vscode", "extension", "typescript"]
published: true
slug: "vscode-cursorghost-diff-extension"
---

VSCodeでコードの差分（diff）を確認しているときに、**片方のペインでカーソルを動かすと、もう片方に切り替えた際に「さっきどこ見てたっけ…？」と迷子になること**、がよくありました。

この問題を解決するために、VSCodeの拡張機能を作りました。

---

## 🧠 作った拡張機能：Cursorghost

[🔗 Cursorghost - Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=kupuma-ru21.Cursorghost)

この拡張機能は、**diffエディタで左右のペインを切り替えたときに、前回見ていたカーソル位置を自動で復元**してくれるVSCode拡張です。

---

## 🎯 解決したかった課題

コードレビューや変更確認のためにdiffビューを開いているとき、
左右のペインを行き来すると**カーソル位置がリセットされてしまい、前に見ていた行を見失う**ことがよくありました。

---

## 🔨 どうやって実装したか

Cursorghostは以下のような仕組みで動いています：

- `onDidChangeTextEditorSelection` で、diffエディタ内で現在アクティブな行を記録
- `onDidChangeActiveTextEditor` でdiffエディタ間の切り替えを検知
- `TabInputTextDiff` を使って「diffビューであること」を判定
- 切り替え先のペインに、自動的にカーソル位置を復元

差分エディタ専用の挙動なので、通常のファイル編集中には影響を与えません。

ソースコードはTypeScriptで書いており、GitHubでも公開しています👇

🔗 [GitHub - kupuma-ru21/cursorghost](https://github.com/kupuma-ru21/cursorghost)

---

## 🚀 使い方

1. VSCodeの拡張機能で `Cursorghost` を検索
2. インストール
3. diffエディタを開いて、カーソルを動かしてみてください！

左右のペインを切り替えるだけで、自動的に前のカーソル位置に戻ってくれるようになります。

---

## 🙏 最後に

VSCodeは強力なツールですが、「ほんのちょっとしたUXのズレ」が集中力を削ぐこともあります。

Cursorghostはそんな “ちょっとした不便” を解消する小さな魔法のような拡張機能です。

もし便利だと感じたら、ぜひ拡張機能に⭐️やZennのいいねをしていただけると励みになります！
