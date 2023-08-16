# Debian/UbuntuにLean 4をインストールする方法 - 簡単な手順

ここでは、Debianから派生したLinuxディストリビューション(Debian、Ubuntu、LMDEなど)にLeanをインストールする簡単で高速な手順を説明します。この手順を使うと、Lean、そのサポートツールであるelanとLake、コードエディタVS CodeとそのLeanプラグイン、そしてcurlやgitのような既にインストールされている可能性のある依存関係パッケージがインストールされます。

ただし、この方法はbashスクリプトによるsudoコマンドの実行を含むほか、インストールプロセスの細部が分からないというデメリットもあります。ここで紹介するコマンドや、コマンド内で実行されるbashスクリプトが信頼できない場合は、この方法は使わず、代わりに[より詳細なインストール手順](./debian-ubuntu-detailed.md)をご覧ください。

ターミナルを開き、次のように入力して実行すると、簡単で高速にLean 4をインストールすることができます。

```bash
wget -q https://raw.githubusercontent.com/leanprover-community/mathlib4/master/scripts/install_debian.sh && bash install_debian.sh ; rm -f install_debian.sh && source ~/.profile
```

## 参考資料
- [How to install Lean 4 on Debian/Ubuntu - Lean Community](https://leanprover-community.github.io/install/debian.html) : 翻訳元、公式。
