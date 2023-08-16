# 既存のLeanプロジェクトの使い方

既存のLeanプロジェクトの使い方を説明します。ここでは、[Mathematics in Lean](https://github.com/leanprover-community/mathematics_in_lean)を例にとります。まずターミナルを開きます。

* もしelanとLeanのインストールに使ったターミナルを閉じずに使い続けている場合、LeanやelanやLake等にパスを通すために次のコマンドを実行してください。コマンドはOSに応じて変わります。

  ```sh
  source ~/.profile
  ```

  または

  ```sh
  source ~/.bash_profile
  ```

* ``cd`` コマンドを使って使いたいパッケージを置きたいフォルダに移動します。Leanプロジェクト用のサブフォルダは自動的に作られるため、手動で作る必要はありません。

* 移動先のフォルダ上で次のコマンドを実行し、Leanプロジェクト「Mathematics in Lean」をクローンします。

  ```sh
  git clone https://github.com/leanprover-community/mathematics_in_lean.git
  ```

* 次のコマンドを実行し、クローンしたプロジェクトのルートディレクトリに移動します。

  ```sh
  cd mathematics_in_lean
  ```

* 次のコマンドを実行し、キャッシュされたビルド済みファイルをダウンロードします。(このコマンドは現在、``mathlib4`` をインポートするプロジェクト内でしか機能しません)

  ```sh
  lake exe cache get
  ```

* アプリケーションメニューから、あるいはコマンド ``code .`` を実行して、VS Codeを起動します。(Mac OSユーザーがコマンドラインからVS Codeを立ち上げるためには、[もう1ステップ](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line)作業する必要があります。)

* VS Codeを起動したら、画面上部にある ``File`` メニューを開き、``Open folder``(Macの場合は ``Open``)をクリックし、``mathematics_in_lean`` フォルダを選択します(``mathematics_in_lean`` フォルダ内のサブフォルダを選ばないように注意してください)。

* 左端のサイドバー内のファイルエクスプローラーを使ってサブフォルダ ``MIL`` の中を探し、開きたいLeanファイルを開きます。この本の練習問題に取り組む方法は[MIL instructions](https://github.com/leanprover-community/mathematics_in_lean/blob/master/README.md)に書かれています。

## 参考資料

- [Lean projects - Lean Community](https://leanprover-community.github.io/install/project.html) : 翻訳元、公式。
- [leanprover-community/mathlib4: The math library of Lean 4](https://github.com/leanprover-community/mathlib4/) : 公式。
- [leanprover/lake: Lean 4 build system and package manager with configuration files written in Lean.](https://github.com/leanprover/lake) : 公式。``README.md`` に詳細な情報が書かれています。

## おすすめのLeanプロジェクト教材

- [Mathematics in Lean](https://github.com/leanprover-community/mathematics_in_lean)
- [The mechanics of proof](https://github.com/hrmacbeth/math2001)
(後日更新予定)
