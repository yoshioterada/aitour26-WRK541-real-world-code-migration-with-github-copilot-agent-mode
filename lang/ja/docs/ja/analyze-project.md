# プロジェクト分析

## 4. GitHub Copilot と戦略を立てる

> *Ask Mode を使って進めてみましょう。*

プロジェクト理解が深まったら、GitHub Copilot と戦略を練りましょう。
**Ask Mode** で、このプロジェクトを C# に書き換える際に Python テストが役立つ理由を質問します。

- GitHub Copilot にテストの概要を要約してもらう

??? question "Tip"
    Prompt *(Ask Mode)*

    ```text
    #file:test_main.py provide a summary of the tests for the python
    application in this repository
    ```

- Copilot に、Python テストが C# 移行の検証に有効な理由を聞く

??? question "Tip"
    Prompt *(Ask Mode)*

    ```text
    #file:test_main.py why are the Python tests in test_main.py a good way to
    validate the C# rewrite?
    ```

- プロジェクトを適切に書き換える方法の提案を依頼する

!!! note
    Copilot はコード全文を出力しがちです。ブレインストーミングではコード生成を避けるよう指示しましょう。

??? question "Tip"
    Prompt *(Ask Mode)*

    ```text
    Just provide suggestions on how to properly rewrite this project in C#.
    Keep this high level.
    Do not change any code. 
    ```

## 5. 不足テストの洗い出し

Python テストがすべてのケースを網羅していない可能性があります。GitHub Copilot を使って不足テストを見つけ、C# 書き換え前にカバレッジを高めましょう。

このステップでは **Agent Mode** を使います。

- `test_main.py` を開き、不足テストを Copilot に特定してもらう
- 不足テストを実装する
- テストを実行し、失敗したら修正する

??? question "Tip"
    Prompt *(Agent Mode)*

    ```text
    Analyze the python application.
    Help me run the Python tests in src/python-app/webapp/test_main.py and check
    that they pass.
    In case of failure, help me address the failures to get the tests passing
    ```
