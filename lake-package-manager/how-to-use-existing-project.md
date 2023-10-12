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
- [lean-math-workshop (日本語)](https://github.com/yuma-mizuno/lean-math-workshop) : 『[数学系のためのLean勉強会](https://haruhisa-enomoto.github.io/lean-math-workshop/)』のために作成された教材です。Leanの基本的な使い方を学ぶBasic編と、代数・解析・圏論の各分野における定理を実際に証明するAdvanced編に分かれています。Advanced編で証明する定理には「群の準同型定理」「閉区間[0, 1]のコンパクト性」などが含まれます。
- [Mathematics in Lean (英語)](https://github.com/leanprover-community/mathematics_in_lean) : 論理・集合から測度論・微積分までの数学の定理を実際に形式証明しながらLean 4を学ぶテキストです。
- [The mechanics of proof (英語)](https://github.com/hrmacbeth/math2001) : 計算による等式や不等式の証明から始まり、数論や代数分野の高校数学程度の問題について、形式的な証明の書き方を学べるテキストです。`cancel`など、[Index of Lean tactics](https://hrmacbeth.github.io/math2001/Index_of_Tactics.html)ページにおいて先頭に"*"が付けられたタクティクは、この教材独自のタクティクであり、Leanの標準ライブラリやMathlibで同様のタクティクを使うことはできません。
