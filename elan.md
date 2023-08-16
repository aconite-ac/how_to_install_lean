# elan: Leanバージョンマネージャ

**elan**は、Leanをインストール・アップデートしたり、Leanプロジェクトの要求に応じたバージョンのLeanを提供したりする、Leanの小さなバージョンマネージャです。

## elanのインストール方法

[インストールページ](./how-to-install.md)に従ってLeanがインストールされていれば、elanもインストールされているはずです。手動でインストールしたい場合はここに挙げる方法を使ってください。

手動でインストールする場合は、ターミナル内で次のコマンドを実行します。

**Linux/macOS/Cygwin/MSYS2/git bash/...**:

```bash
curl https://raw.githubusercontent.com/leanprover/elan/master/elan-init.sh -sSf | sh
```

**Windows**:

```bash
curl -O --location https://raw.githubusercontent.com/leanprover/elan/master/elan-init.ps1
powershell -ExecutionPolicy Bypass -f elan-init.ps1
del elan-init.ps1
```

あるいは、[最新のリリース](https://github.com/leanprover/elan/releases/latest)をダウンロードし、解凍し、その中のインストールプログラムを実行させてelanをインストールすることもできます。

ここで説明したインストール方法を実行した場合、インストーラは ``elan``、``lean``、``lake`` のバイナリを ``~/.elan/bin`` にインストールすること、``~/.profile`` を更新して ``~/.elan/bin`` をPATH環境変数に加えることを説明します。``~/.profile`` の更新により、次回以降シェルを起動した際は自動で ``~/.elan/bin`` にパスが通りますが、現在のシェルにおいてパスを通したい場合はコマンド ``source ~/.elan/env`` を実行してください。

## elanのフォーク元

elanはRustのツールチェイン・インストーラ[rustup](https://github.com/rust-lang/rustup)のフォークです。基本的に、RustとLeanを比較すると、``rustup`` は ``elan`` に、``cargo`` は ``lake`` に相当します。

## elanに関する用語

- toolchain(ツールチェーン) : 特定のバージョンのLean一式のことです。
- channel(チャンネル) : ツールチェーンの系統のことです。Lean4には ``nightly`` と ``stable`` の2つのチャンネルがあります。

## 参考資料
- [leanprover/elan: A Lean version manager - GitHub](https://github.com/leanprover/elan) : 翻訳元、公式。上記の情報に加え、HomebrewやNixを使ったインストール方法や、elanのビルド方法が紹介されています。
