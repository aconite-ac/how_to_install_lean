# FAQ

## Leanのインストール方法

<span class="Q">Q.</span> <span class="question">VSCodeで ``lean4`` 拡張機能をインストールしたいのですが、「lean4」で検索しても複数の拡張機能がヒットします。どれをインストールしたらいいですか？</span>

<span class="A">A.</span> Leanのインストール手順で紹介されている ``lean4`` 拡張機能は「``leanprover.lean4``」という一意の名前(Extension ID)を持ちます。「lean4」の代わりに「leanprover.lean4」で検索すれば拡張機能が1件だけヒットしますので、それをインストールしてください。

<hr />

<span class="Q">Q.</span> <span class="question">``elan``・``lean``・``lake`` のバイナリはどのフォルダにインストールされますか？</span>

<span class="A">A.</span> ``elan``・``lean``・``lake`` のバイナリは ``~/.elan/bin``(``$HOME/.elan/bin``) にインストールされます。

<hr />

<span class="Q">Q.</span> <span class="question">``elan``・``lean``・``lake``(以下、「``lean`` 等」とする) へのパスは自動で通りますか？</span>

<span class="A">A.</span> 例えば、Windowsで[QuickStarkインストール](./how-to-install/windows-quickstart.md)を行った場合は環境変数に``~/.elan/bin``が自動で追加されます。また、Debianでbashをお使いの環境でインストールを行った場合は、設定ファイル``~/.profile``(あるいは ``~/.bash_profile``) が自動で更新され、パスが通ります。zshをお使いの場合も設定ファイルが自動で更新されます。したがって、インストール後にターミナルを再起動すれば ``lean`` 等へのパスは通ります。
   
   ターミナルを再起動したくない場合は、コマンド ``source ~/.elan/env`` を実行すれば現在のターミナルでパスが通ります。``~/.elan/env`` の内容は次の通りです。

   ```sh
   export PATH="$HOME/.elan/bin:$PATH"
   ```

   しかし、ターミナル fish をお使いの場合は自動でパスが通らないことが報告されています。他のターミナルをお使いの場合も自動でパスが通らない可能性が考えられます。その際は、``~/.elan/env`` の内容を参考にして各自設定ファイルを編集し、パスを通してください。

## Lake: Leanパッケージマネージャ編

<span class="Q">Q.</span> <span class="question">``lake new <project_name>`` を実行してもLeanプロジェクトが作られません。どうしたらいいですか？</span>

<span class="A">A.</span> まずはお使いのコンピュータに ``Git`` がインストールされていることを確認してください。

<hr />

<span class="Q">Q.</span> <span class="question">Leanプロジェクトにおいて ``lake update`` を実行すると次のようなエラーが出ます。どうしたらいいですか？</span>
   ```
   error: .\lakefile.lean:x:x error: unknown attribute [defaultTarget]
   ```

<span class="A">A.</span> ``lean`` のバージョンアップに伴い、属性 ``[defaultTarget]`` が ``[default_target]`` に変更されたようです。このエラーが出た場合、``lake`` のバージョンが古い可能性があります。``elan update`` で ``elan``・``lean``・``lake`` をアップデートしてからLeanプロジェクトを作り直すか、``lakefile.lean`` 内の ``[defaultTarget]`` を ``[default_target]`` に置換してください。

<hr />

<span class="Q">Q.</span> <span class="question">Mathlibを使うLeanプロジェクトにおいて、コンパイルエラーが発生します。どうしたらいいですか？</span>

<span class="A">A.</span> Mathlibの ``lean-toolchain`` が指定するLeanのバージョンと、Leanプロジェクトの ``lean-toolchain`` が指定するLeanのバージョンが食い違うことによるエラーの可能性があります。Mathlib4のバージョンを固定していない場合は、[Leanプロジェクト内で、被依存パッケージMathlib4をアップデートする方法](./lake-package-manager/how-to-create-project.md#leanプロジェクト内で被依存パッケージmathlib4をアップデートする方法)を実行すれば解決する可能性があります。

<hr />

<span class="Q">Q.</span> <span class="question">Mathlibを使うLeanプロジェクト内のLeanファイルを開きましたが、``import`` がいつまで経っても終わりません。どうしたらいいですか？</span>

<span class="A">A.</span> キャッシュされたビルド済ファイルが正常にダウンロードされていない可能性があります。コマンド ``lake exe cache get`` が未実行ならこのコマンドを実行してください。``lake exe cache get`` が実行済みならコマンド ``lake exe cache get!`` を試してみてください。``lake exe cache get!``はキャッシュされたビルド済ファイルのダウンロードをやり直します。

## 出典
Discordサーバー「code for math」の「#lean」チャンネル
