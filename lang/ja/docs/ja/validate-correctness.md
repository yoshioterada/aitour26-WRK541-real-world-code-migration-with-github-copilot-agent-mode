# 正しさを検証し、エンドポイントを追加

## 9. 正しさを検証

C# の全エンドポイントが Python テストで合格したら、Copilot にファイル全体のレビューを依頼し、
潜在的な落とし穴や性能問題を特定しましょう。
例えば、各エンドポイントが毎回ファイルをデシリアライズしていると性能問題です。Copilot に指摘させます。

??? question "Tip"
    Prompt *(Agent Mode)*

    ```text
    Identify any potential problems with my Program.cs file.
    Specifically I am interested in understanding redundancy and any code
    that is doing unnecessary work.
    Do not generate any code, just explain.
    ```

### 10. エンドポイントとテストを追加

Python と C# が 1:1 で対応したら、新しいエンドポイントとテストを追加してみましょう。
例: `/countries/{country}`（Python には未実装だが C# に追加可能）。

- `Program.cs` を開き、他にも有用なエンドポイントを Copilot に尋ねる
- Python の `test_main.py` を開き、新エンドポイントのテスト追加を依頼
- テストを実行し、失敗があれば修正

??? question "Tip"
    Prompt *(Ask Mode)*

    ```text
    The C# API now has full parity with the Python application,
    but I want you to suggest me other potential endpoints that might be useful.
    ```

??? question "Tip"
    Prompt *(Agent Mode)*

    ```text
    #file:Program.cs implement /countries/{country} endpoint
    and add a test to assess it.
    ```
