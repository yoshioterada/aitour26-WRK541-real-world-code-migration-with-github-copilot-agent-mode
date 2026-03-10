# リポジトリを開く（ローカル / GitHub Codespaces）

自分に合ったワークフローを選びましょう。ローカル環境で作業する場合は、必要ツールが
インストール済みである前提です。事前条件チェックリストは Resources ページを参照してください。
完全ホスト型がよければ GitHub Codespaces を選択します。

!!! note "イベント参加者向け"
    Microsoft イベントのラボ環境を利用できる場合も、好みで **ローカル環境** 手順を実施できます。ローカル手順では、ラボではなく自分の環境で資格情報やリソースを用意することを想定しています。ラボの詳細はイベント案内を参照してください。

=== "ローカル環境"

    1. リポジトリページを開く: [Real World Code Migration with GitHub Copilot Agent Mode](https://github.com/microsoft/aitour26-WRK541-real-world-code-migration-with-github-copilot-agent-mode){:target="_blank"}
    
    1. リポジトリをローカルにクローン:
    
        ```bash
        git clone https://github.com/microsoft/aitour26-WRK541-real-world-code-migration-with-github-copilot-agent-mode.git
        ```
    
    1. VS Code で **File > Open Folder** からクローンしたフォルダーを開く
    
    1. VS Code で GitHub にサインインし、GitHub Copilot を有効化
       （Command Palette → **GitHub: Sign in**）
    
    1. Python プロジェクトの依存を復元:
    
        ```bash
        cd src/python-app
        ```

        ```bash
        pip install -r requirements.txt
        ```
    
    1. これでローカルでワークショップを進められます。ツール一覧は Resources ページの
       **Local environment prerequisites** を参照。

=== "GitHub Codespaces"

    1. リポジトリを開く: [Real World Code Migration with GitHub Copilot Agent Mode](https://github.com/microsoft/aitour26-WRK541-real-world-code-migration-with-github-copilot-agent-mode){:target="_blank"}
    2. GitHub にログイン
    3. 右上の **Star** ボタンをクリック（後で見つけやすくするため）
    4. **<> Code** → **Codespaces** タブ → **+** で新規 Codespace 作成
    
        ![Create a new Codespace](./media/create-new-codespace.png)
    
    5. ブラウザ上で Codespace のプロビジョニング完了を待つ
    6. ブラウザ上の VS Code 画面が表示されたら、そのまま進めるか **Open in VS Code** でデスクトップから接続
    
        ![Open in VS Code button](./media/open-in-vscode.png)

!!! success
    後でワークショップを再開する場合は、GitHub プロフィール画像 → **Your stars** から参照できます。
