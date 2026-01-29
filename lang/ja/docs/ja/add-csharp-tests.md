# C# テストの追加

## 11. C# テストでプロジェクトを仕上げる

Python テストですべてのエンドポイントの動作を確認できたので、任意で C# ネイティブテストを追加して C# コードベースを直接検証しましょう。
Python テストは HTTP API 経由で Python/C# 両方を検証するのに十分でしたが、
必要なら MSTest（または xUnit/NUnit）を使って C# プロジェクトを独自のテストで検証できます。

- Copilot に C# プロジェクトのテスト配置場所を尋ねる（通常は別プロジェクト、例: `WeatherApi.Tests`）
- テスト実行方法を尋ねる
- 1 テストずつ追加して検証するやり方も有効。同じプロセスで一つずつ集中できます
- あるいは Copilot にテストプロジェクト全体をスキャフォールドし、すべてのエンドポイントのテストをまとめて追加させることも可能

このステップでは **Plan Mode** を試してください。まず要件に基づく計画を Copilot に作らせ、
計画を確認してから実行を依頼します.

??? question "Tip"
    Prompt *(Plan Mode)*

    ```text
    Now that we have all endpoints in C# I want native C# unit tests
    using MSTest.
    Create a test project so that I can verify correctness with C# tests
    alongside the Python tests.
    If not existing, create a new solution at the root of the c# app
    [src\csharp-app] and add the main project and the new test project to it.
    Create tests for each endpoint, one at a time, and validate them.
    ```

ここまで来たら C# アプリは十分にテストされているはずです。お疲れさま！時間があれば残りのタスクにも挑戦してみてください。
