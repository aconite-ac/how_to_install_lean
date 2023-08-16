# WindowsにLean 4をインストールする方法 - 詳細な説明

ここでは、WindowsにLeanをインストールする方法を説明します。

Leanを使うにあたり、まずLeanと、Leanを扱う機能を持つエディタをセットアップする必要があります。Leanを直接インストールする代わりに、Leanをアップデートしたり、Leanプロジェクトの要求に応じたバージョンのLeanを提供する、[elan](https://github.com/leanprover/elan)という名前の小さなプログラム(バージョンマネージャ)をインストールします。elanのインストールは全てのユーザに推奨されます。

## Visual Studio Codeのインストール

全てのWindowsユーザーに対して、エディタ ``Visual Studio Code(VS Code)`` を使ってLeanを扱うことをお勧めします。[https://code.visualstudio.com/download](https://code.visualstudio.com/download)から ``VS Code`` をインストールすることができます。

## gitのインストール

Lean 4 プロジェクト間の依存関係は、gitリポジトリへのポインタを介して実装されています。したがって、Leanプロジェクトを作るには、お使いのコンピュータにgitをインストールする必要があります。

既にgitをインストールしてある場合は、このステップを飛ばすことができます。

もしgitがインストールされていないなら、[Git for Windows](https://gitforwindows.org/)をインストールすることをお勧めします。インストール中、多くの質問を受けますが、デフォルトエディタに関する質問**以外は**デフォルトの選択肢を選ぶことをお勧めします。デフォルトエディタに関する質問では、デフォルト選択肢 ``vi`` の代わりに ``Visual Studio Code`` を選ぶことをお勧めします。

編集するテキストファイルの改行コードを変えないようにするために(改行コードをLFで統一するために)、コマンド ``git config --global core.autocrlf input`` を実行することをお勧めします。

## VS Codeにlean4拡張機能をインストール

``VS Code`` を開き、画面左端の「アクティビティバー」の中にある「拡張機能」アイコン ![(image of icon)](img/new-extensions-icon.png) をクリックします。

検索ボックスが表示されるので、``lean4`` と入力し、検索結果に表示される ``lean4`` 拡張機能を選択します。「Install」ボタンをクリックすると拡張機能がインストールされます。

## elanとLeanのセットアップ

``elan`` と ``lean`` のセットアップについては、``VS Code`` の ``lean4`` 拡張機能に任せることも、手動でセットアップすることもできます。``lean4`` 拡張機能にセットアップを任せることをお勧めしますが、以下では両方の手順を説明します。

### lean4拡張機能にelanとLeanをインストールしてもらう方法

画面上部にある ``File`` メニューを開き、``New text file`` を選びます。``Untitled-1`` とラベルされた新しいウィンドウが開きます。

新しいウィンドウには ``Select a language`` と表示されます。この表示をクリックし、``lean4`` を選びます。(画面右下端に表示される ``Plain text`` をクリックして言語を選択することもできます。また、``Ctrl+Shift+P`` を押して「コマンドパレット」を開き、そこで ``Change language mode`` を選んで言語を選択することもできます。)

言語を ``lean4`` に設定すると、画面右下端に、``Failed to start 'lean' language server`` と書かれた、``Install Lean using Elan`` ボタン付きのダイアログボックスが表示されます。

``Install Lean using Elan`` ボタンをクリックします。そうすると、``VS Code`` 内でターミナルウィンドウが立ち上がり、インストールが始まります。``Lean`` のダウンロードとインストールには1分程度かかります。

インストールが終わったら、``Untitled-1`` ウィンドウに戻り、次のように入力します。

```lean
#eval 18 + 19
```

``#eval`` の下に青い波線が引かれ、右側の ``Lean Infoview`` パネルに ``37`` が表示されたら、Lean 4のインストールは成功です！

### 手動でelanをインストールする方法

コマンドプロンプト(``cmd``)を開き、次のコマンドを実行します。

```shell
curl -O --location https://raw.githubusercontent.com/leanprover/elan/master/elan-init.ps1
powershell -ExecutionPolicy Bypass -f elan-init.ps1
del elan-init.ps1
```

あるいは、``Git Bash`` を開き、次のコマンドを実行します。

```shell
curl https://raw.githubusercontent.com/leanprover/elan/master/elan-init.sh -sSf | sh
```

どちらの方法でも、``elan`` のインストールには1分程度かかります。インストールが終わったら、``VS Code`` を開き、画面上部にある ``File`` メニューを開き、``New text file`` を選びます。新しいテキストが開かれたら、``Select a language`` と書かれた部分をクリックし、``lean4`` を選びます。(あるいは、新しいテキストを ``.lean`` 拡張子で保存します。)

それから、次のように入力して、Leanがユーザーの入力に反応することを確認してください。

```lean
#eval 18 + 19
```

以上でインストールは完了です！

## 参考資料
- [Installing Lean 4 on Windows - Lean Community](https://leanprover-community.github.io/install/windows.html) : 翻訳元、公式。
