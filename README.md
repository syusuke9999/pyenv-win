# Windows用pyenv

[pyenv][1]は素晴らしいツールです。これをWindowsに移植しました。このライブラリを改善するためのあなたの意見や、プロジェクトの成長に役立つフィードバックが必要です。

既存のPythonユーザーには[pip経由でのインストール](#インストール)をサポートしています。

コントリビューターや興味のある方は、@[Slack](https://join.slack.com/t/pyenv/shared_invite/zt-f9ydwgyt-Fp8tehxqeCQi5mi77RxpGw)で参加してください。あなたの助けが私たちのモチベーションを維持します！

[![pytest](https://github.com/pyenv-win/pyenv-win/actions/workflows/pytest.yml/badge.svg)](https://github.com/pyenv-win/pyenv-win/actions/workflows/pytest.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub issues open](https://img.shields.io/github/issues/pyenv-win/pyenv-win.svg?)](https://github.com/pyenv-win/pyenv-win/issues)
[![Downloads](https://pepy.tech/badge/pyenv-win)](https://pepy.tech/project/pyenv-win)
[![Rate this package](https://badges.openbase.com/python/rating/pyenv-win.svg?token=hjylt9qszl1DzDMCXNqMQZ6ijtlNCYzG3dKZNF+hgk4=)](https://openbase.com/python/pyenv-win?utm_source=embedded&amp;utm_medium=badge&amp;utm_campaign=rate-badge)

- [はじめに](#はじめに)
- [pyenv](#pyenv)
- [pyenv-winコマンド](#pyenv-winコマンド)
- [インストール](#インストール)
- [インストールの確認](#インストールの確認)
- [使い方](#使い方)
- [pyenvのアップデート方法](#pyenvのアップデート方法)
- [お知らせ](#お知らせ)
- [よくある質問](#よくある質問)
- [変更履歴](#変更履歴)
- [貢献方法](#貢献方法)
- [バグトラッカーとサポート](#バグトラッカーとサポート)
- [ライセンスと著作権](#ライセンスと著作権)
- [著者と謝辞](#著者と謝辞)

## はじめに

Python用の[pyenv][1]は素晴らしいツールですが、Ruby開発者向けの[rbenv][2]と同様に、Windowsを直接サポートしていません。Python開発者からのフィードバックと調査の結果、彼らはWindowsシステムでも同様の機能を求めていました。

このプロジェクトは、[rbenv-win][3]からフォークし、[pyenv][1]用に変更されました。多くの異なるコントリビューターからの助けを得て、現在ではかなり成熟したものになっています。

## pyenv

[pyenv][1] はシンプルな Python バージョン管理ツールです。複数の Python バージョンを簡単に切り替えることができます。シンプルで邪魔にならず、1つのことをうまくやる UNIX 伝統のシングルパーパスツールに従っています。

## クイックスタート

1. PowerShell で pyenv-win をインストールします。

   ```pwsh
   Invoke-WebRequest -UseBasicParsing -Uri "https://raw.githubusercontent.com/pyenv-win/pyenv-win/master/pyenv-win/install-pyenv-win.ps1" -OutFile "./install-pyenv-win.ps1"; &"./install-pyenv-win.ps1"
   ```

2. PowerShell を再度開きます
3. `pyenv --version` を実行して、インストールが成功したかどうかを確認します。
4. `pyenv install -l` を実行して、pyenv-win に対応する Python バージョンのリストを確認します
5. `pyenv install <version>` を実行して、対応するバージョンをインストールします
6. `pyenv global <version>` を実行して、Python バージョンをグローバルバージョンに設定します
7. 使用している Python バージョンとそのパスを確認します

   ```plaintext
   > pyenv version
   <version> (set by \path\to\.pyenv\pyenv-win\.python-version)
   ```

8. Python が機能していることを確認します

   ```plaintext
   > python -c "import sys; print(sys.executable)"
   \path\to\.pyenv\pyenv-win\versions\<version>\python.exe
   ```

## pyenv-winコマンド

```yml
   commands     使用可能なすべての pyenv コマンドを一覧表示します
   local        ローカルのアプリケーション固有の Python バージョンを設定または表示します
   global       グローバルな Python バージョンを設定または表示します
   shell        シェル固有の Python バージョンを設定または表示します
   install      1 つ以上の Python バージョンをインストールします
   uninstall    1 つ以上の Python バージョンをアンインストールします
   update       キャッシュされたバージョン DB を更新します
   rehash       pyenv shims を再ハッシュします（Python バージョンを切り替えた後に実行してください）
   vname        現在の Python バージョンを表示します
   version      現在の Python バージョンとその由来を表示します
   version-name 現在の Python バージョンを表示します
   versions     pyenv で利用可能なすべての Python バージョンを一覧表示します
   exec         選択された Python を使用するように PATH を準備した後に実行可能ファイルを実行します
   which        実行可能ファイルへのフルパスを表示します
   whence       指定された実行可能ファイルを含むすべての Python バージョンを一覧表示します
```

## インストール

現在、以下の方法に対応しています。お好みの方法を選択してください:

- [PowerShell](docs/installation.md#powershell) - 最も簡単な方法
- [Git Commands](docs/installation.md#git-commands) - デフォルトの方法 + 手動設定の追加
- [Pyenv-win zip](docs/installation.md#pyenv-win-zip) - 手動インストール
- [Python pip](docs/installation.md#python-pip) - 既存のユーザー向け
- [Chocolatey](docs/installation.md#chocolatey)
- [How to use 32-train](docs/installation.md#how-to-use-32-train)
  - [お知らせの確認](#お知らせ)

詳細については、[インストール](./docs/installation.md)ページを参照してください。

## インストールの確認

1. コマンドプロンプトを再度開いて、`pyenv --version`を実行します。
2. 次に、`pyenv`と入力して使用方法を確認します。

"**command not found**"エラーが表示される場合は、以下の注意事項を確認し、[設定を手動で確認してください](#設定の手動確認)。

Visual Studio Codeや組み込みターミナルを持つ他のIDEの場合は、再起動して再度確認してください。

***

### 設定の手動確認

すべての環境変数がGUI経由で高い優先度で正しく設定されていることを確認してください。

```plaintext
このPC
   → プロパティ
      → システムの詳細設定
         → 詳細 → 環境変数...
            → PATH
```

**注意:** Windows 10 1905以降を実行している場合は、スタート > "アプリ実行エイリアスの管理"から、Pythonの"アプリインストーラー"エイリアスをオフにして、組み込みのPythonランチャーを無効にする必要があるかもしれません。

## 使い方

- pyenv windowsでサポートされているPythonバージョンのリストを表示するには：`pyenv install -l`
- リストをフィルタリングするには：`pyenv install -l | findstr 3.8`
- Pythonバージョンをインストールするには：`pyenv install 3.5.2`
  - _注意：一部の非サイレントインストールではインストールウィザードが表示されることがあります。インストール中にウィザードをクリックして進めてください。オプションを変更する必要はありません。また、-qオプションを使って静かなインストールができます。_
  - 複数のバージョンを一度にインストールすることもできます：`pyenv install 2.4.3 3.6.8`
- Pythonバージョンをグローバルバージョンとして設定するには：`pyenv global 3.5.2`
  - これは、ローカルバージョン（下記参照）が設定されていない場合にデフォルトで使用されるPythonのバージョンです。
  - _注意：まずバージョンをインストールする必要があります。_
- Pythonバージョンをローカルバージョンとして設定するには：`pyenv local 3.5.2`
  - このフォルダ内で`python`が呼び出されると、指定されたバージョンが使用されます。これは仮想環境とは異なり、明示的にアクティブ化する必要がありません。
  - _注意：まずバージョンをインストールする必要があります。_
- pipを使ってライブラリを（アン）インストールしたり、バージョンのフォルダ内のファイルを変更したりした後は、`pyenv rehash`を実行して、Pythonとライブラリの実行ファイルの新しいシムをpyenvに更新する必要があります。
  - _注意：これは`.pyenv`フォルダの外で実行する必要があります。_
- Pythonバージョンをアンインストールするには：`pyenv uninstall 3.5.2`
- 使用中のPythonとそのパスを表示するには：`pyenv version`
- このシステムにインストールされているすべてのPythonバージョンを表示するには：`pyenv versions`
- pyenv-winの`2.64.x`および`2.32.x`バージョン用のコマンド`pyenv update`を使用して、検出可能なPythonバージョンのリストを更新します。

## pyenvのアップデート方法

- pipでインストールした場合
  - pyenv-winのインストールパスを、site-packages内にある`easy_install.pth`ファイルに追加してください。これにより、pipがpyenv-winをインストール済みとして認識します。
  - pipを使ってアップデートを取得します。`pip install --upgrade pyenv-win`
- Gitでインストールした場合
  - `%USERPROFILE%\.pyenv\pyenv-win`（インストールされたパス）に移動し、`git pull`を実行します。
- zipでインストールした場合
  - 最新のzipをダウンロードして解凍します。
  - `%USERPROFILE%\.pyenv\pyenv-win`に移動し、ダウンロードした新しい`libexec`と`bin`フォルダで既存のものを置き換えます。
- インストーラーでインストールした場合
  - Powershellターミナルで以下を実行します。`&"${env:PYENV_HOME}\install-pyenv-win.ps1"`

## お知らせ

[pyenv][1]のLinux/Mac版と同期を保つために、pyenv-winはデフォルトで64ビット版をインストールするようになりました。古いバージョンのpyenv-winとの互換性をサポートするために、32ビット版（ブランチ）を別のリリースとして維持しています。

どちらのリリースも64ビットと32ビットのPythonバージョンをインストールできますが、バージョン名に違いがあります。例えば：

- 64ビット版（master）、つまりpyenvバージョン _2.64.x_

```plaintext
> pyenv install -l | findstr 3.8
....
3.8.0-win32
3.8.0
3.8.1rc1-win32
3.8.1rc1
3.8.1-win32
3.8.1
3.8.2-win32
3.8.2
3.9.0-win32
3.9.0
....
```

- 32bit-train、すなわちpyenvバージョン_2.32.x_

```plaintext
> pyenv install -l | findstr 3.8
....
3.8.0
3.8.0-amd64
3.8.1rc1
3.8.1rc1-amd64
3.8.1
3.8.1-amd64
3.8.2
3.8.2-amd64
....
```
  
Python 2.4未満のバージョンに対するサポートは、2.4以降のバージョンのようにインストーラーが「クリーンに」インストールすることができず、ほとんどの環境で使用/サポートされていないため、廃止されました。

## よくある質問

[よくある質問](./docs/faq.md)ページをご覧ください。

## 変更履歴

[変更履歴](./docs/changelog.md)ページをご覧ください。

## 貢献方法

- プロジェクトをフォークし、ローカルにクローンします。
- 上流リモートを作成し、ブランチを切る前にローカルのコピーを同期します。
- それぞれの作業に対してブランチを作成します。テストケースを書くことは良い習慣です。
- 作業を行い、適切なコミットメッセージを書き、もし存在するならCONTRIBUTINGファイルを読んでください。
- `tests\bat_files\test_install.bat` と `tests\bat_files\test_uninstall.bat` を実行して変更をテストします。
- 自分のオリジンリポジトリにプッシュします。
- GitHubで新しいプルリクエストを作成します。

## バグトラッカーとサポート

- pyenv-winに関する提案、バグ報告、不満などは、[GitHubバグトラッカー](https://github.com/pyenv-win/pyenv-win/issues)を通じて報告してください。

## ライセンスと著作権

- pyenv-winは[MIT](http://opensource.org/licenses/mit-license.php) _2019_ の下でライセンスされています。

   [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 著者と謝辞

pyenv-winは[Kiran Kumar Kotari](https://github.com/kirankotari)と[Contributors](https://github.com/pyenv-win/pyenv-win/graphs/contributors)によって開発されました。  
最新のメジャーリリースを辛抱強くサポートしてくれたすべてのコントリビューターとサポーターに感謝します。

[1]: https://github.com/pyenv/pyenv
[2]: https://github.com/rbenv/rbenv
[3]: https://github.com/nak1114/rbenv-win
