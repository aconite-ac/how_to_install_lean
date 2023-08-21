# Leanプロジェクトの作り方

## Mathlib4の使用を前提としないLeanプロジェクトの新規作成方法

Mathlib4の使用を前提としないLeanプロジェクト ``my_project`` を新規作成する手順を説明します。まずターミナルを開きます。

* ``cd`` コマンドを使って ``my_project`` を作りたいフォルダに移動します。

* 次のコマンドのいずれかを実行します(どちらでも結果は同じです)。新しいLeanプロジェクトが作成されます。

  ```sh
  lake new my_project
  ```

  あるいは

  ```sh
  mkdir my_project
  cd my_project
  lake init my_project
  ```

## Mathlib4を使うLeanプロジェクトの新規作成方法

Mathlib4を使うLeanプロジェクト ``my_project`` を新規作成する手順を説明します。まずターミナルを開きます。

* ``cd`` コマンドを使って ``my_project`` を作りたいフォルダに移動します。

* 次のコマンドを実行します。Mathlib4への依存関係が設定された新しいLeanプロジェクトが作成されます。

  ```sh
  lake new my_project math
  ```

* 次のコマンドを実行し、作成したLeanプロジェクト内に移動します。

  ```sh
  cd my_project
  ```

* 次のコマンドを実行し、Mathlib4を含む被依存パッケージをダウンロードします。

  ```sh
  lake update
  ```

* 次のコマンドを実行し、Mathlib4のキャッシュされたビルド済ファイルをダウンロードします。

  ```sh
  lake exe cache get
  ```

* 次のコマンドを実行し、Leanファイルを置くためのサブディレクトリ ``MyProject`` を作成します。

  ```sh
  mkdir MyProject
  ```

* VS Codeを開き、画面上部にある ``File`` メニューを開き、``Open folder``(Macの場合は ``Open``)をクリックし、``my_project`` フォルダ(``MyProject`` フォルダではありません)を選択します。

これでMathlib4を使うLeanプロジェクト ``my_project`` の新規作成は完了です。以降、プロジェクトのLeanファイル(拡張子 ``.lean``)は ``MyProject`` フォルダかそのサブフォルダ上に作成してください。

Leanプロジェクトが正常に作成され、Mathlib4内のモジュールがインポートできることを確認するには、次のような方法があります:

* 画面左端のサイドバーのファイルエクスプローラーを開き、``MyProject`` フォルダにカーソルを合わせて右クリックし、``New File`` をクリックし、``test.lean`` という名前のファイルを作成します。

* VS Code上で ``test.lean`` を開き、ファイルに次のように入力します:

  ```lean
  import Mathlib.Topology.Basic
  
  #check TopologicalSpace
  ```

* ``#check TopologicalSpace`` にマウスカーソルを乗せ、VS Codeの右側の「Lean Infoview」に次のように表示されたら確認完了です。

  ```
  TopologicalSpace.{u} (α : Type u) : Type u
  ```

自作Leanファイル内で他の自作Leanファイルをインポートすることもできます。例えば、``my_project/MyProject/Definitions.lean`` と ``my_project/MyProject/Lemmas.lean`` が存在する場合、``Lemmas.lean`` の先頭に次のように書くことで、``Definitions.lean`` の内容が利用可能になります。

```lean
import MyProject.Definitions
```

何らかの理由で右側の「Lean Infoview」が消えてしまった場合は、<kbd>Ctrl</kbd>-<kbd>Shift</kbd>-<kbd>Enter</kbd>(MacOSの場合は <kbd>Cmd</kbd>-<kbd>Shift</kbd>-<kbd>Enter</kbd>)を押すことで「Lean Infoview」を復活させることができます。また、<kbd>Ctrl</kbd>-<kbd>Shift</kbd>-<kbd>p</kbd>(MacOSの場合は <kbd>Cmd</kbd>-<kbd>Shift</kbd>-<kbd>p</kbd>)を押し、コマンドを入力するテキストフィールドを表示させ、「lean doc」と入力し<kbd>Enter</kbd>を押すと、「Mathematics in Lean」や「Theorem Proving in Lean 4」といったドキュメントを読むことができます。

## 既存のプロジェクトにMathlib4への依存関係を追加する方法

現時点でMathlib4に依存していないLeanプロジェクト ``my_project`` にMathlib4への依存関係を追加する手順を説明します。

* ``my_project/lakefile.lean`` を開き、次の記述を追加します。

  ```lean
  require mathlib from git
    "https://github.com/leanprover-community/mathlib4"
  ```

  ブランチを指定することもできます。

  ```lean
  require mathlib from git
    "https://github.com/leanprover-community/mathlib4" @ "master"
  ```

  ハッシュ値を付けてパッケージバージョン(Gitコミット)を固定することもできます。

  ```lean
  require mathlib from git
    "https://github.com/leanprover-community/mathlib4" @
  "9efcb9508435caeb4281b14455f37b88f8ffc2e5"
  ```

* ターミナルを開き、フォルダ ``my_project`` に移動します。

* パッケージバージョンを固定しなかった場合、次のコマンドを実行し、``my_project`` 内で使われるLeanのバージョンを最新のMathlib4内で使われるLeanのバージョンに合わせます。

  ```sh
  curl -L https://raw.githubusercontent.com/leanprover-community/mathlib4/master/lean-toolchain -o lean-toolchain
  ```

* 次のコマンドを実行し、Mathlib4を含む被依存パッケージをダウンロードします。

  ```sh
  lake update
  ```

* 次のコマンドを実行し、Mathlib4のキャッシュされたビルド済ファイルをダウンロードします。

  ```sh
  lake exe cache get
  ```

以上で、既存のプロジェクトからMathlib4への依存関係の追加は完了です。

## Leanプロジェクト内で、被依存パッケージMathlib4をアップデートする方法

* ターミナルを開き、フォルダ ``my_project`` に移動します。

* 次のコマンドを実行し、``my_project`` 内で使われるLeanのバージョンを最新のMathlib4内で使われるLeanのバージョンに合わせます。

  ```sh
  curl -L https://raw.githubusercontent.com/leanprover-community/mathlib4/master/lean-toolchain -o lean-toolchain
  ```

* 次のコマンドを実行し、Mathlib4を含む被依存パッケージをダウンロードします。

  ```sh
  lake update
  ```

* 次のコマンドを実行し、Mathlib4のキャッシュされたビルド済ファイルをダウンロードします。

  ```sh
  lake exe cache get
  ```

以上でMathlib4のアップデートは完了です。

## 参考資料

- [Lean projects - Lean Community](https://leanprover-community.github.io/install/project.html) : 翻訳元、公式。
- [Using mathlib4 as a dependency · leanprover-community/mathlib4 Wiki](https://github.com/leanprover-community/mathlib4/wiki/Using-mathlib4-as-a-dependency) : 公式。
- [leanprover/lake: Lean 4 build system and package manager with configuration files written in Lean.](https://github.com/leanprover/lake) : 公式。``README.md`` に詳細な情報が書かれています。
- [プログラミング言語Lean 4の現状 - 檜山正幸のキマイラ飼育記 (はてなBlog)](https://m-hiyama.hatenablog.com/entry/2022/12/31/183948) : 檜山正幸さんによるLean 4まとめ記事です。「Leanプロジェクト」と「Leanパッケージ」の節を参考にしました。
- [Installation Help - Lean - Zuip Chat](https://leanprover.zulipchat.com/#narrow/stream/113489-new-members/topic/.E2.9C.94.20Installation.20help.2C/near/358005313) : 
Mario Carneiroさんのメッセージを参考にしました。
