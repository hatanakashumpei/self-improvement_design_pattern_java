# design_pattern_java: Dev Container 開発手順

このリポジトリは VS Code Dev Containers を使って、ローカル環境を汚さずに Java 開発できます。

## 1. 前提条件

以下をホスト環境にインストールしてください。

- Docker
- Visual Studio Code
- VS Code 拡張: Dev Containers (`ms-vscode-remote.remote-containers`)

## 2. コンテナ起動手順

1. VS Code でこのフォルダを開く
2. コマンドパレットを開く (`Ctrl+Shift+P`)
3. `Dev Containers: Rebuild and Reopen in Container` を実行

初回はイメージ作成に数分かかることがあります。

## 3. コンテナ構成

- 定義ファイル: `.devcontainer/devcontainer.json`
- Dockerfile: `.devcontainer/Dockerfile`
- ベースイメージ: `eclipse-temurin:21-jdk-jammy`
- ワークスペース: `/code`

## 4. Java 動作確認

コンテナ内ターミナルで以下を実行します。

```bash
java -version
javac -version
```

期待結果:

- Java 21 系のバージョンが表示される
- `javac` が利用可能である

## 5. サンプルのビルドと実行例

例として Observer パターンのサンプルを実行します。

```bash
cd /code/src/Observer/Sample
javac *.java
java Main
```

他のサンプルも同様に、対象ディレクトリへ移動して `javac` と `java` で実行できます。

## 6. よく使う運用

- 依存関係や設定を更新したとき: `Dev Containers: Rebuild Container`
- 一時停止後に再接続したいとき: `Dev Containers: Reopen in Container`

## 7. トラブルシューティング

### コンテナが起動しない

- Docker が起動しているか確認
- VS Code のコマンドで `Rebuild and Reopen in Container` を再実行
- 失敗ログは `Dev Containers` のログ出力を確認

### Java が見つからない

- コンテナ内で `java -version` を再確認
- 反映不整合の可能性があるためコンテナを再ビルド

### 拡張機能が入らない

- ネットワーク制限下ではインストール失敗する場合あり
- コンテナ再起動後に自動インストールされるか確認

## 8. 補足

このリポジトリにはデザインパターンのサンプル実装が多数含まれています。
各ディレクトリで個別にコンパイル・実行して学習できます。
