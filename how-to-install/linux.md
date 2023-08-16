# Linux全般にLean 4をインストールする方法

ここでは、Linux全般にLeanをインストールする方法を説明します。(Debianとその派生ディストリビューションへのインストール方法は[こちらのページ](./debian-ubuntu.md)をご覧ください。)

以下の全てのコマンドはターミナル内で入力してください。

* Lean自体を動かすために必要なパッケージは少ないですが、``elan`` のインストールや ``lake`` を使ったLeanプロジェクト作成には ``git`` と ``curl`` が必要です。したがって、まずは ``git`` と ``curl`` をインストールしてください。

* 次は、``elan`` と呼ばれる小さなツールをインストールします。このツールは、Leanをアップデートしたり、Leanプロジェクトの要求に応じたバージョンのLeanを提供したりします。コマンドの実行中に質問が表示されたらEnterキーを押してください。elanは ``$HOME/.elan`` にインストールされ、``$HOME/.profile`` に1行追加されます。
  ```bash
  curl https://raw.githubusercontent.com/leanprover/elan/master/elan-init.sh -sSf | sh
  ```

* VS Code、Emacs、Neovimの3つのエディタ上でLeanを使うことができます。おすすめのエディタは[Visual Studio Code (VS Code)](https://code.visualstudio.com/)です。Leanにとって、VS Codeは最も完成度が高く、よくテストされたサポートを提供するエディタです。次の手順により、VS Codeがインストールされます。

  1. [VS Code](https://code.visualstudio.com/)をインストールします。
  2. VS Codeを起動します。
  3. スクリーンの左端のサイドバーにある拡張機能アイコン ![(image of icon)](img/new-extensions-icon.png) (古いバージョンでは ![(image of icon)](img/extensions-icon.png) ) をクリックし(あるいは<kbd>Shift</kbd>-<kbd>Ctrl</kbd>-<kbd>X</kbd>を押し)、``leanprover`` と検索します。
  4. ``lean4`` 拡張機能(``leanprover.lean4`` という一意の名前を持ちます)を選びます。 
  5. 「Install」をクリックします。(古いバージョンのVS Codeを使っている場合、インストール後に「reload」をクリックする必要があります。)
  6. Leanが動作していることを確認してください。例えば、ファイルに ``test.lean`` と名前を付けて保存し、``#eval 1+1`` と入力してみてください。``#eval 1+1`` の下部に緑色の線が表示され、そこにマウスを乗せたときに ``2`` と表示されたらインストール成功です。

他の選択肢として、Emacsと[lean4-mode](https://github.com/leanprover/lean4-mode)を使ってLeanを扱うこともできます。また、Neovimと[lean.nvim extension](https://github.com/Julian/lean.nvim)を使うことも可能です。

## 参考資料
- [Installing Lean 4 on Linux - Lean Community](https://leanprover-community.github.io/install/linux.html) : 翻訳元、公式。
