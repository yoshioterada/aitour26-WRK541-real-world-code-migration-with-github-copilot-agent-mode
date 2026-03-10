# Rust テストの追加

## 11. Rust テストでプロジェクトを仕上げる

すべてのエンドポイントとテストがパスしたので、Rust ネイティブテストで正しさを検証しましょう。
シェルテストは HTTP API 経由で Python/Rust 両方を検証するのに十分でしたが、
Rust プロジェクトを Rust テストで直接検証できます。

- Copilot に Rust プロジェクトのテスト配置場所を尋ねる（`main.rs` と同じファイル、または別ファイル）
- テスト実行方法を尋ねる
- テストは 1 つずつ追加し、その都度検証する。同じプロセスで集中しやすくなります

??? question "Tip"
    Prompt *(Agent Mode)*

    ```text
    Now that we have all endpoints in Rust I want native Rust unit tests.
    Add them to main.rs so that I can verify correctness without having to use
    the bash script
    ```

ここまで来れば、Rust アプリは十分にテストされているはずです。お疲れさま！時間があれば他のタスクにも挑戦してみてください。
