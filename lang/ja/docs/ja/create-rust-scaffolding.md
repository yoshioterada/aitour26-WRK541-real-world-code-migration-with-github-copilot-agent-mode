# Rust スキャフォールディングを作成

> *このステップ以降は GitHub Copilot を Agent Mode で使いましょう。*

プロジェクトとテストの理解ができたら、Rust スキャフォールディングを作成します。
まず **Copilot Instructions** ファイルを用意します。リポジトリルートに配置する
`.github/copilot-instructions.md` に以下を記述します（空ファイルを用意済み）。

```markdown
Whenever you are providing suggestions for a Rust project always use the
actix-web framework using serde for serialization
```

<!-- markdownlint-disable MD046 -->
??? warning
    新しいチャットを開始するとコンテキストがリセットされ、Copilot がより鮮明に動作する場合があります。
    Copilot チャット上部の ![New Chat Button on GitHub Copilot](./media/copilot-newchat.png)
    をクリックしてください。
<!-- markdownlint-enable MD046 -->

複雑度が上がるため **Edit Mode** から離れ、**Agent Mode** のみで進めます。
切り替えたら、Rust プロジェクトのスキャフォールディング作成を Copilot に依頼し、開始手順とコマンドも聞きましょう。

<!-- markdownlint-disable MD046 -->
??? question "Tip"
    Prompt *(Agent Mode)*

     ```text
     #file:rust-app create the Rust scaffolding in rust-app folder, where we are
     going to migrate the python project. Don't perform any code migration for
     now.
     Provide me with guided steps to run the project afterwards.
     ```
<!-- markdownlint-enable MD046 -->
フレームワークとシリアライザは指示ファイルを参照して自動的に含まれるはずです。繰り返したくない指示はこのファイルに追記できます。

Copilot がスキャフォールディングを作成したら、`rust-app` フォルダー内を確認します。
`Cargo.toml` と `src/main.rs` があるはずです。ファイルの目的や役割に疑問があれば Copilot に質問してください。
