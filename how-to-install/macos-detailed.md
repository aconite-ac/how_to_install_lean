# MacOS(Intel Macs)にLean 4をインストールする方法 - 詳細な手順

ここでは、MacOS(Intel Macs)にLean 4をインストールする、より詳細な手順を説明します。[簡単で高速なインストール手順](./macos.md)もありますが、この手順を利用するには実行されるコマンドやbashスクリプトを信頼する必要があります。

Leanを使うにあたり、まずLeanと、Leanを扱う機能を持つエディタをセットアップする必要があります。Leanを直接インストールする代わりに、Leanをアップデートしたり、Leanプロジェクトの要求に応じたバージョンのLeanを提供する、[elan](https://github.com/leanprover/elan)という名前の小さなプログラム(バージョンマネージャ)をインストールします。elanのインストールは全てのユーザに推奨されます。

## elanとLeanのインストール

1. まだHomebrewをインストールしていない場合は、[Homebrew](https://brew.sh/)をインストールします。

2. ターミナルウィンドウ内で次のコマンドを実行し、``elan`` をインストールします。

   ```
   brew install elan-init
   ```

   Homebrewに ``lean`` という名前のformulaがありますが、これはバージョン固定のLeanをインストールすることに注意してください。この場合、``elan`` によってLeanプロジェクトの要求に応じたバージョンのLeanが提供されることはありません。このformulaの使用は**推奨されません**。

3. 次のコマンドを実行し、``lean`` の最新のstableバージョンをインストールします。

   ```
   elan toolchain install stable
   ```

   次のコマンドを使うと、今インストールしたLeanのバージョンをデフォルトバージョンに設定することができます。Leanプロジェクトの外部でLeanを使う際は、このデフォルトバージョンが提供されます。

   ```
   elan default stable
   ```

## エディタのインストールと設定

VS Code、Emacs、Neovimの3つのエディタ上でLeanを使うことができます。このドキュメントでは、VS Codeを使う方法を説明します。VS CodeはLeanに最も良好なサポートを提供します。Emacsを使う場合は、[https://github.com/leanprover/lean4-mode](https://github.com/leanprover/lean4-mode)をご覧ください。Neovimを使う場合は、[https://github.com/Julian/lean.nvim](https://github.com/Julian/lean.nvim)をご覧ください。

1. [VS Code](https://code.visualstudio.com/)をインストールします。
2. VS Codeを起動します。
3. スクリーンの左端のサイドバーにある拡張機能アイコン ![(image of icon)](img/new-extensions-icon.png) (古いバージョンでは ![(image of icon)](img/extensions-icon.png) ) をクリックし(あるいは<kbd>⇧ Shift</kbd><kbd>⌘ Command</kbd><kbd>X</kbd>を押し)、``leanprover`` と検索します。
4. ``lean4`` 拡張機能(``leanprover.lean4`` という一意の名前を持ちます)を選びます。 
5. 「Install」をクリックします。(古いバージョンのVS Codeを使っている場合、インストール後に「reload」をクリックする必要があります。)
6. Leanが動作していることを確認してください。例えば、ファイルに ``test.lean`` と名前を付けて保存し、``#eval 1+1`` と入力してみてください。``#eval 1+1`` の下部に緑色の線が表示され、そこにマウスを乗せたときに ``2`` と表示されたらインストール成功です。

## 参考資料
- [Controlled installation of Lean 4 on MacOS - Lean Community](https://leanprover-community.github.io/install/macos_details.html) : 翻訳元、公式。
