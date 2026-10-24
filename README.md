# Badminton Apps

https://aohaus.github.io/Badminton/

バドミントン関連アプリの集約先です。旧 dechatgpt.com/Badminton/ と、アプリごとの個別リポジトリから移行しました。

| アプリ | URL | 移行元 | バージョン |
|---|---|---|---|
| PairPlay | [/Badminton/PairPlay/](https://aohaus.github.io/Badminton/PairPlay/) | aohaus/PairPlay | v1.5.0 |
| RallyScore | [/Badminton/RallyScore/](https://aohaus.github.io/Badminton/RallyScore/) | aohaus/RallyScore | v2.1.3 |
| ErrorZero | [/Badminton/ErrorZero/](https://aohaus.github.io/Badminton/ErrorZero/) | aohaus/ErrorZero | v1.2.1（前の安定版は `ErrorZero/v1.0.4.html`） |
| Shatomin | [/Badminton/Shatomin/](https://aohaus.github.io/Badminton/Shatomin/) | aohaus/Shatomin | v1.0.5 |
| TacticsLab | [/Badminton/TacticsLab/](https://aohaus.github.io/Badminton/TacticsLab/) | （新規） | v1.1.0（戦術14シナリオ＋スカウティング9問） |

## 開発版

| アプリ | URL | 内容 |
|---|---|---|
| PairPlay | [/Badminton/PairPlay/dev.html](https://aohaus.github.io/Badminton/PairPlay/dev.html) | 次の開発用（現在は v1.5.0 と同じ内容） |
| ErrorZero | [/Badminton/ErrorZero/dev.html](https://aohaus.github.io/Badminton/ErrorZero/dev.html) | 次の開発用（現在は v1.2.1 と同じ内容） |
| ErrorZero | [/Badminton/ErrorZero/dev-v1.1.0.html](https://aohaus.github.io/Badminton/ErrorZero/dev-v1.1.0.html) | v1.1.0 の保存版（戻す場合はこれを dev.html にコピー。Git ではコミット `1264eef` の状態） |

開発版で確認できたら `dev.html` の内容を `index.html` に反映して安定版にします。

各アプリは 1 ファイル完結の HTML で、ビルドは不要です。旧バージョン（`v1.x.x.html` など）は移行元リポジトリに残しています。

## ポータルへの戻り方（各アプリ共通）

各アプリの画面レイアウトを崩さないよう、既存のヘッダーやメニューにポータル（`../`）へのリンクを置いています。

| アプリ | 戻り方 |
|---|---|
| PairPlay | 左上の「Badminton Apps」 |
| RallyScore | 下中央の「⋯」→「⌂ Badminton Apps」 |
| ErrorZero | タイトル左のアイコン、または「⋯」→「⌂ Badminton Apps」 |
| Shatomin | 上部の「‹ Badminton Apps」 |
| TacticsLab | 左上の「‹ Badminton Apps」 |

## 構成

```
index.html          ポータル
icons/              共通アイコン（旧 aohaus/Hub/icons）
ErrorZero/          ErrorZero
RallyScore/         RallyScore
PairPlay/           PairPlay（「Open in RallyScore」で ../RallyScore/ に対戦カードを渡す）
Shatomin/           Shatomin（docs/ にルール・FAQ・免責のメモ）
TacticsLab/         TacticsLab（単一HTML。Tailwind はファイル内にコンパイル済みで埋め込み）
migration/          旧 URL に置く転送ページ（このサイト自体では使わない）
```

## 移行時の変更点

- PairPlay: ルート絶対パスを相対パスに変更
  - `/RallyScore/index.html?...` → `../RallyScore/index.html?...`
  - `/RallyHub/icons/pairplay-icon-180.png` → `../icons/pairplay-icon-180.png`
  - ホームリンク `/`（dechatgpt Studio）→ `../`（Badminton Apps）
- RallyScore: `../Hub/icons/rallyscore-icon-180.png` → `../icons/rallyscore-icon-180.png`

## 保存データ（localStorage）

キー名は変更していません（`errorzero_*`, `rallyScore.settings.v1`, `dechatgpt.badminton.memory.v1` など）。
localStorage はドメイン単位のため、dechatgpt.com で保存したデータは github.io には引き継がれません。

## 旧 URL の転送

- `migration/dechatgpt.com/` … dechatgpt.com の同じパスに置く転送ページ
- `migration/old-repos/<App>/index.html` … 旧リポジトリの `index.html` を置き換える転送ページ

どちらもクエリ文字列（`?source=PairPlay&...`）とハッシュを保ったまま新 URL に転送します。
