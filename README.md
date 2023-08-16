# Leanのインストール方法・elanとLakeの使い方

このドキュメントは有志個人による非公式資料です。

Leanのインストール方法と、LeanのバージョンマネージャelanとパッケージマネージャLakeの使い方を紹介します。主な参考資料は[Lean Community](https://leanprover-community.github.io/index.html)のInstallationカテゴリです。参考資料の一覧は各ページの最後に掲載します。

このドキュメントは[mdBook](https://github.com/rust-lang/mdBook)の[Lean向けフォーク](https://github.com/leanprover/mdBook)を使って生成されました。

## このドキュメントのビルド方法

Rustがインストールされていることを前提とします。

このドキュメントをビルドするには、まず[mdBook](https://github.com/rust-lang/mdBook)の[Lean向けフォーク](https://github.com/leanprover/mdBook)をインストールしてください。
```bash
cargo install --git https://github.com/leanprover/mdBook mdbook
```
次に、このREADMEが置かれているフォルダで以下のコマンドを実行してください。
```bash
mdbook build
```
``./out`` フォルダにhtmlファイル群が生成されます。

## デプロイ方法

次のコマンドでデプロイできます。

```
./deploy.sh
```

デプロイ ``deploy.sh`` を実行する際は、あらかじめpush先のリポジトリをご自身のフォークリポジトリに変更することをお勧めします。
