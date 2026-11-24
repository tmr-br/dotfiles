# cambozola

自宅の常時稼働マシン。

## スペック

- Mac mini（2018）
- Intel Core i5（6コア）
- メモリ 32GB
- Intel UHD Graphics 630

## 役割

- コーディングエージェントの実行ホスト（常時稼働）
- Xcode が不要な実装・調査・量産タスクの既定の受け皿

## 制約と注意

- Intel 機なので、ツールや OS の対応状況はタスクごとに確認する
- 最新の Xcode が要る作業は割り当てない（Xcode / iOS は mimolette 専任）
- リポジトリは ghq 配下に揃える

## セットアップ

1. [brew/Brewfile.cambozola](../brew/Brewfile.cambozola) を `brew bundle` で入れる
2. [install/agents.md](../install/agents.md) の手順でエージェントを導入する
3. 常駐系（エージェント基盤、リモートアクセス）は再起動後に自動で戻ることを確認する
