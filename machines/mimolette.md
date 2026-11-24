# mimolette

メインマシン。

## スペック

- MacBook Pro
- Apple M1 Pro
- メモリ 16GB
- SSD 512GB

## 役割

- 唯一の Xcode / iOS 開発環境。iOS アプリのビルド、署名、シミュレータはここでしかできない
- 本人の手元の作業全般

## 制約と注意

- メモリと SSD がボトルネック。重い常駐ジョブや大量のエージェント実行は cambozola に逃がす
- 後継機（MacBook Pro または Mac mini）を検討中。移行時はこのリポジトリの手順で環境を再構築する

## セットアップ

1. [brew/Brewfile.mimolette](../brew/Brewfile.mimolette) を `brew bundle` で入れる
2. [install/agents.md](../install/agents.md) の手順でエージェントを導入する
3. Xcode は Mac App Store から入れ、コマンドラインツールの向く先を確認する
