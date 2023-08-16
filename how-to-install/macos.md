# MacOSにLean 4をインストールする方法 - 簡単な手順

ここでは、MacOSにLeanをインストールする手順を説明します。

特に、M1 Macs / Apple Siliconの場合はやや複雑な手順を含みます。行き詰まった場合は、[Lean - Zulip Chat (英語)](https://leanprover.zulipchat.com/)で助けを求めてください。

**注意**: 以下では翻訳元に従い、Intel Macsについては ``curl`` を利用する方法、M1 Macs / Apple Siliconについては複雑な手順を紹介していますが、翻訳元ならびに以下の記述はLean 3のときの情報から更新されていない可能性があります。少なくとも、**M1 Macs**におけるLeanのインストールについては、Windowsと同様に[VS Codeのlean4拡張機能にelanとLeanをインストールしてもらう簡単な方法](https://aconite-ac.github.io/how_to_install_lean/how-to-install/windows-quickstart.html)が有効だったという報告があります。MacOSへのインストールに関して、以下の記述を更新しうる情報をお持ちの方は、[GitHubのIssues](https://github.com/aconite-ac/how_to_install_lean/issues)へ連絡して頂けると幸いです。

## Intel Macs

ここでは簡単で高速なインストール方法を紹介します。この手順を使うと、Lean、そのサポートツールである ``elan`` と ``lake``、コードエディタVS CodeとそのLeanプラグインがインストールされます。

ただし、この方法はbashスクリプトによるsudoコマンドの実行を含むほか、インストールプロセスの細部が分からないというデメリットもあります。ここで紹介するコマンドや、コマンド内で実行されるシェルスクリプトが信頼できない場合は、この方法は使わず、代わりに[より詳細なインストール手順](./macos-detailed.md)をご覧ください。

ターミナルを開き、次のように入力して実行すると、簡単で高速にLean 4をインストールすることができます。

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/leanprover-community/mathlib4/master/scripts/install_macos.sh)" && source ~/.profile
```

## M1 Macs / Apple Silicon

GitHub Actionsが[まだApple ARM上でのビルドをサポートしていない](https://github.com/actions/virtual-environments/issues/2187)ため、Leanのインストール方法はやや複雑です。

具体的には、Leanのバージョンマネージャ ``elan`` は、通常の方法でインストールされた場合、インストールされたデバイス上のLeanバイナリをフェッチすることができません。

以下の手順は[Fedor Pavutnitskiy](https://leanprover.zulipchat.com/#narrow/stream/113489-new-members/topic/M1.20Macs.3A.20Installing.20the.20Lean.203.20toolchain/near/262832039)氏からの引用です。この手順を使うと、[Rosetta](https://developer.apple.com/documentation/apple-silicon/about-the-rosetta-translation-environment) を通して ``elan`` をインストールすることができます。

1. 新しいターミナルウィンドウを開き、次のコマンドを実行します。XCode Command Line ToolsとRosetta 2がインストールされます。

   ```
   xcode-select --install
   softwareupdate --install-rosetta
   ```

2. x86版のHomebrewをインストールします。最も簡単な方法は、Rosetta 2を使ってx86が動作するシェルを立ち上げる方法です。まず、次のコマンドを実行し、x86が動作するシェルを立ち上げます。

   ```
   arch -x86_64 zsh
   ```
   
   以降のコマンドはこのx86が動作するシェルウィンドウの中で実行しますが、一度インストールが完了すれば、インストールされたツールはどのシェルでも動作するはずです。

3. 次のコマンドを実行し、x86版のHomebrewをインストールします。これは ``/opt`` ではなく ``/usr/local`` に自動的にインストールされるはずです。

   ```
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

4. 今インストールしたバージョンの ``brew`` を使って、[MacOSへの詳細なインストール手順](./macos-detailed.md)と同様の次のコマンドを実行します。

   ```
   /usr/local/bin/brew install elan-init
   elan toolchain install stable
   elan default stable
   ```

5. 次のコマンドを実行してVisual Studio CodeとそのLean拡張機能をインストールします。コマンド内で ``brew`` のバージョンが指定されていませんが、x86版の ``brew`` でもARM版の ``brew`` でも正常に動作するはずです。

   ```
   brew install --cask visual-studio-code && code --install-extension leanprover.lean4
   ```

[Zulipスレッド (英語)](https://leanprover.zulipchat.com/#narrow/stream/113489-new-members/topic/M1.20macs)にインストール過程の詳細とアドバイスが書かれています。問題が起きたときは、遠慮なく助けを求めてください。

新しいターミナルを開いたときに ``command not found`` エラーが発生した場合は、MacOSからログアウトして再度ログインすれば解決するはずです。

## 参考資料
- [How to install Lean 4 on MacOS - Lean Community](https://leanprover-community.github.io/install/macos.html) : 翻訳元、公式。
