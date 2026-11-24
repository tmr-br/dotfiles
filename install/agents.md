# コーディングエージェントの導入

各エージェントの導入と認証の要点。バージョンや手順は変わりやすいので、導入前に必ず公式の現行ドキュメントを確認すること（古い解説記事やパッケージ名が旧世代を指していることがある）。認証情報そのものはこのリポジトリに書かない。

最終確認: 2026-11

## Claude Code

- 導入: 公式インストーラ、または npm パッケージ `@anthropic-ai/claude-code`
- 認証: claude.ai アカウントでサインイン
- 非対話実行は標準入力を閉じて起動する（開いたままだと入力待ちで固まる）

## Codex

- 導入: openai/codex の GitHub リリースから取得する（CLI のバージョンで使えるモデルが変わるため、バージョンは現行に揃える）
- 認証: ChatGPT アカウントのデバイス認証
- 非対話実行は標準入力を閉じて起動する

## OpenCode

- 導入: v2 のインストーラを使う

  ```sh
  curl -fsSL https://opencode.ai/v2/install | bash
  ```

  `~/.opencode/bin/opencode` に配置される。npm パッケージ `opencode-ai` や旧インストーラは v1 が入るので使わない
- 認証: `opencode auth login opencode`（OpenCode Console へのデバイス認証）。API キーは不要
- 非対話実行: `opencode run ... </dev/null`（標準入力を閉じないと固まる）

## Grok Build

- 導入:

  ```sh
  curl -fsSL https://x.ai/cli/install.sh | bash
  ```

  `~/.grok/bin/grok` に配置される
- 認証: `grok login --device-auth`
- ヘッドレス実行では承認を聞けないので、自動承認のオプションが要る

## T3 Code

- 導入: デスクトップアプリを両方の Mac に入れる
- 外部エージェント連携: 公式の MCP 機能（Outside agents）を使う。接続は T3 Connect のリレー経由で、OAuth（認可コード + PKCE）で認証する
- 環境同士のリンク（Linked environments）は一方向ずつ設定する。双方向に使いたい場合は逆向きも作る

## Orca

- 導入: デスクトップアプリ
- Mac 同士の接続は、サーバー側のアプリで「このアプリをサーバーとして公開」して接続リンクを発行し、クライアント側で取り込む方式を使う（ヘッドレス専用コマンドは使わない）
- 運用方針: 閲覧と操作は T3 Code、サーバーの常駐と自動化は Orca、という併用を想定
