# dotfiles

開発環境の定義。2台の Mac と、そこで動くコーディングエージェント群の構成・手順・ルールをここに集約する。

新しいマシンが来たら、このリポジトリを clone して手順どおりに進めれば、同じ作業環境が戻ることを目指す。

## マシン構成

| コードネーム | 実機 | 役割 |
|---|---|---|
| mimolette | MacBook Pro（M1 Pro、16GB、512GB） | メインマシン。唯一の Xcode / iOS 開発環境 |
| cambozola | Mac mini 2018（Intel i5、32GB） | 自宅の常時稼働マシン。コーディングエージェントの実行ホスト |

詳細は [machines/](machines/) を参照。

## ルーティングの原則

- Xcode が要る作業は mimolette、それ以外は既定で cambozola に寄せる（mimolette は Xcode / iOS と本人の作業用に空ける）
- 実装の第一選択は Codex。設計とレビューは別モデルから独立に取る
- 複数のエージェントに同じファイルを同時編集させない（git worktree を分ける）

詳細は [docs/agent-routing.md](docs/agent-routing.md) を参照。

## 導入手順

- パッケージ: [brew/](brew/) の Brewfile（マシン別）
- コーディングエージェント: [install/agents.md](install/agents.md)

## セキュリティ方針

このリポジトリは Public で運用する。次は絶対に入れない。

- トークン、API キー、パスワード、秘密鍵などの認証情報そのもの（認証は「方式」だけを書く）
- ネットワークのアドレスやホスト鍵の指紋など、接続先を特定できる情報
- 仕事のクライアント名、案件名、非公開リポジトリ名
- 個人のメールアドレス

設定ファイルは、秘情報を除いたテンプレートだけを [config/](config/) に置く。
