# Debian/UbuntuにLean 4をインストールする方法 - 詳細な手順

ここでは、Debianから派生したLinuxディストリビューション(Debian、Ubuntu、LMDEなど)にLean 4をインストールする、より詳細な手順を説明します。[簡単で高速なインストール手順](./debian-ubuntu.md)もありますが、この手順を利用するには実行されるコマンドやbashスクリプトを信頼する必要があります。

厳密にいえば、ここで紹介する手順もシェルスクリプトの実行を含みます。[elan_init](https://github.com/leanprover/elan/blob/master/elan-init.sh)を読むことで、以下のインストール手順のより細部を知ることができます。

* Lean自体を動かすために必要なパッケージは少ないですが、``elan`` のインストールや ``lake`` を使ったLeanプロジェクト作成には ``git`` と ``curl`` が必要です。したがって、まずは ``git`` と ``curl`` をインストールします。
  ```bash
  sudo apt install git curl
  ```

* 次は、``elan`` と呼ばれる小さなツールをインストールします。このツールは、Leanをアップデートしたり、Leanプロジェクトの要求に応じたバージョンのLeanを提供したりします。コマンドの実行中に質問が表示されたらEnterキーを押してください。elanは ``$HOME/.elan`` にインストールされ、``$HOME/.profile`` に1行追加されます。
  ```bash
  curl https://raw.githubusercontent.com/leanprover/elan/master/elan-init.sh -sSf | sh
  ```

* VS Code、Emacs、Neovimの3つのエディタ上でLeanを使うことができます。おすすめのエディタは[Visual Studio Code (VS Code)](https://code.visualstudio.com/)です。Leanにとって、VS Codeは最も完成度が高く、よくテストされたサポートを提供するエディタです。次のコマンドにより、VS Codeがインストールされます。
  ```bash
  wget -O code.deb https://go.microsoft.com/fwlink/?LinkID=760868
  sudo apt install ./code.deb
  rm code.deb
  code --install-extension leanprover.lean4
  ```

以上の手順が終わったら、VS Codeを開き、Leanが動作していることを確認してください。例えば、ファイルに ``test.lean`` と名前を付けて保存し、``#eval 1+1`` と入力してみてください。``#eval 1+1`` の下部に緑色の線が表示され、そこにマウスを乗せたときに ``2`` と表示されたらインストール成功です。

他の選択肢として、Emacsと[lean4-mode](https://github.com/leanprover/lean4-mode)を使ってLeanを扱うこともできます。また、Neovimと[lean.nvim extension](https://github.com/Julian/lean.nvim)を使うことも可能です。

## 参考資料
- [Controlled installation of Lean 4 on Debian/Ubuntu - Lean Community](https://leanprover-community.github.io/install/debian_details.html) : 翻訳元、公式。
