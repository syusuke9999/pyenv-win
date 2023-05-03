# インストール

現在、以下の方法をサポートしています。お好みの方法を選択してください。

- [PowerShell](#powershell) - 最も簡単な方法
- [Gitコマンド](#Gitコマンド) - デフォルトの方法 + 手動での設定追加
- [Pyenv-win zip](#pyenv-win-zip) - 手動インストール
- [Python pip](#python-pip) - 既存のユーザー向け
- [Chocolatey](#chocolatey)
- [32-trainの使用方法](#32-trainの使い方)
  - [お知らせを確認する](../README.md#お知らせ)

やった！インストールが完了したら、[インストールの確認](../README.md#インストールの確認)の手順に進んでください。

_注意:_ Windows 10 1905以降を実行している場合は、スタート > "アプリ実行エイリアスの管理"から、Python用の"アプリインストーラー"エイリアスをオフにして、組み込みのPythonランチャーを無効にする必要があるかもしれません。

***

## **PowerShell**

pyenv-winをインストールする最も簡単な方法は、PowerShellターミナルで以下のインストールコマンドを実行することです:

```pwsh
Invoke-WebRequest -UseBasicParsing -Uri "https://raw.githubusercontent.com/pyenv-win/pyenv-win/master/pyenv-win/install-pyenv-win.ps1" -OutFile "./install-pyenv-win.ps1"; &"./install-pyenv-win.ps1"
```

以下のような **UnauthorizedAccess** エラーが発生した場合は、Windows PowerShellを「管理者として実行」オプションで起動し、`Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine`を実行してください。その後、上記のインストールコマンドを再度実行してください。

```plaintext
& : ファイル C:\Users\kirankotari\install-pyenv-win.ps1 は、このシステムでスクリプトの実行が無効になっているため読み込めません。詳細については、about_Execution_Policies を参照してください。https:/go.microsoft.com/fwlink/?LinkID=135170。
1行目の文字:173
+ ... n.ps1" -OutFile "./install-pyenv-win.ps1"; &"./install-pyenv-win.ps1"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~ 
 + CategoryInfo          : SecurityError: (:) [], PSSecurityException 
 + FullyQualifiedErrorId : UnauthorizedAccess
```

'デジタル署名'や'セキュリティ警告'に関する詳細情報は、次の問題 [#332](https://github.com/pyenv-win/pyenv-win/issues/332) を参照してください。

インストールが完了しました！

[READMEに戻る](../README.md#インストール)

***

## **Gitコマンド**

pyenv-win をインストールするデフォルトの方法は、Windows 用の git/git-bash をインストールする必要があります。

PowerShell や Git Bash を使用している場合は、`%USERPROFILE%` の代わりに `$HOME` を使用してください。

コマンドプロンプトを使用して git clone するには、`git clone https://github.com/pyenv-win/pyenv-win.git "%USERPROFILE%\.pyenv"` を実行します。

[システム設定を追加する](#add-system-settings)手順

_注意:_ 上記のリンクをチェックすることを忘れないでください。インストールを完了するための最終手順が含まれています。

インストールが完了しました！

[README に戻る](../README.md#インストール)

***

## **Pyenv-win zip**

pyenv-winの手動インストール手順

PowerShellやGit Bashを使用している場合は、`%USERPROFILE%`の代わりに`$HOME`を使用してください。

1. [pyenv-win.zip](https://github.com/pyenv-win/pyenv-win/archive/master.zip)をダウンロードします。

2. コマンドプロンプトで`.pyenv`ディレクトリを作成します。`mkdir %USERPROFILE%/.pyenv`（存在しない場合）

3. ファイルを`%USERPROFILE%\.pyenv\`に展開して移動します。

4. `%USERPROFILE%\.pyenv\pyenv-win`の下に`bin`フォルダがあることを確認します。

[システム設定を追加](#add-system-settings)する手順

_注意:_ 上記のリンクをチェックするのを忘れないでください。インストールを完了するための最終手順が含まれています。

インストールが完了しました！

[README](../README.md#インストール)に戻る

***

## **Python pip**

既存のPythonユーザー向け

### コマンドプロンプト

`pip install pyenv-win --target %USERPROFILE%\\.pyenv`  

上記のコマンドでエラーが発生した場合は、代わりに以下を使用してください（[#303](https://github.com/pyenv-win/pyenv-win/issues/303)）：

`pip install pyenv-win --target %USERPROFILE%\\.pyenv --no-user --upgrade`

### PowerShellまたはGit Bash

上記と同じコマンドを使用しますが、`%USERPROFILE%`を`$HOME`に置き換えます。

### 最終手順

[システム設定の追加](#add-system-settings)に進んでください。

インストールが完了するはずです！

[README](../README.md#インストール)に戻る

***

## **Chocolatey**

これには、chocoコマンドを使ってインストールする必要があります。[インストールリンク](https://chocolatey.org/install)

Chocolateyコマンド `choco install pyenv-win`

Chocolateyページ: [pyenv-win](https://chocolatey.org/packages/pyenv-win)

インストールが完了しました！

インストールの確認

[README](../README.md#インストール)に戻る

***

## **システム設定の追加**

ここではPowerShellを使用する簡単な方法を紹介します。

1. 環境変数にPYENV、PYENV_HOME、PYENV_ROOTを追加します。

   ```pwsh
   [System.Environment]::SetEnvironmentVariable('PYENV',$env:USERPROFILE + "\.pyenv\pyenv-win\","User")

   [System.Environment]::SetEnvironmentVariable('PYENV_ROOT',$env:USERPROFILE + "\.pyenv\pyenv-win\","User")

   [System.Environment]::SetEnvironmentVariable('PYENV_HOME',$env:USERPROFILE + "\.pyenv\pyenv-win\","User")
   ```

2. 次に、以下のパスをUSER PATH変数に追加して、pyenvコマンドにアクセスできるようにします。

   ```pwsh
   [System.Environment]::SetEnvironmentVariable('path', $env:USERPROFILE + "\.pyenv\pyenv-win\bin;" + $env:USERPROFILE + "\.pyenv\pyenv-win\shims;" + [System.Environment]::GetEnvironmentVariable('path', "User"),"User")
   ```

インストールが完了しました。おめでとうございます！

[README](../README.md#インストール)に戻る

***

## **32-trainの使い方**

- **Gitを使用する場合**
  1. 32-trainの前提条件は、[Gitを使用してpyenv-winをインストールする](#git-commands)ことです。
  2. .pyenvディレクトリに移動するコマンド`cd %USERPROFILE%\.pyenv`
  3. `git checkout -b 32bit-train origin/32bit-train`を実行します。
  4. `pyenv --version`を実行し、_2.32.x_が表示されることを確認します。

- **pipを使用する場合**
  1. `pip install pyenv-win==2.32.x --target %USERPROFILE%\.pyenv`を実行します。
  2. [システム設定を追加する](#add-system-settings)手順に進みます。

- **Zipを使用する場合**
  1. [pyenv-win.zip](https://github.com/pyenv-win/pyenv-win/archive/32bit-train.zip)をダウンロードします。
  2. [Pyenv-win zip](#pyenv-win-zip)の手順2に従います。
  3. [システム設定を追加する](#add-system-settings)手順に進みます。

[README](../README.md#インストール) に戻る

***