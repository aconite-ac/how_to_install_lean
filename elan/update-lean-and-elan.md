# Leanとelanのアップデート

以下のコマンドは全てターミナル上で実行するものです。また、``#`` はコメントを表します(rootユーザでのコマンドの行頭の記号を表すものではありません)。

## elanのヘルプ情報を表示する

次のコマンドを実行すると、elanのヘルプ情報(使い方等)を表示することができます。

```sh
elan -h
```

## elanのアップデート

次のコマンドを実行すると、elan自体をアップデートすることができます。Windowsをお使いの場合、VS Codeが起動していない状態でこのコマンドを実行してください。[^1]

```sh
elan self update
```

次のコマンドを実行すると、elanのバージョンが表示されます。

```sh
elan -V
```

## Leanのアップデート

次のコマンドを実行すると、elanとLeanの両方をアップデートすることができます。

```sh
elan update
```

次のコマンドを実行すると、インストール済みのツールチェーンの一覧と現在アクティブなツールチェーンを表示します。

```sh
elan show
```

## デフォルトツールチェーンの変更

次のコマンドを実行すると、指定したツールチェーンをインストールし、そのツールチェーンをデフォルトに設定します。

```sh
# elan default <ツールチェーン名>
elan default leanprover/lean4:nightly
# 例えば、stableチャンネルのツールチェーンに切り替えたいときは次を実行する:
# elan default leanprover/lean4:stable
```

## 参考資料

- [Extended Setup Notes - Lean Manual](https://leanprover.github.io/lean4/doc/setup.html) : 翻訳元、公式。
- [Channels - The rustup book](https://rust-lang.github.io/rustup/concepts/channels.html) : Rust公式。
- [Toolchains - The rustup book](https://rust-lang.github.io/rustup/concepts/toolchains.html) : Rust公式。
- [プログラミング言語Lean 4の現状 - 檜山正幸のキマイラ飼育記 (はてなBlog)](https://m-hiyama.hatenablog.com/entry/2022/12/31/183948) : 檜山正幸さんによるLean 4まとめ記事です。上記の内容に加え、ツールチェーン名の命名パターンが詳説されているほか、具体的なコマンドの実行例が掲載されています。

[^1]: Windowsにおいて、VS Code起動中に ``elan self update`` を実行するとエラーになることが報告されています([Issue #95 · leanprover/elan](https://github.com/leanprover/elan/issues/95))。
