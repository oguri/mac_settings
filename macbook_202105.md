# MacBook 設定メモ (2021年5月)

詳細

- MacBook Air (M1, 2020)
- macOS: Big Sur
- memory: 16GB
- storage: SSD 2TB
- USキーボード

初のM1 (arm64) のmacなので移行アシスタントを使わず、またしばらくはメインには使わず様子をみる。設定においてはRosetta 2を使わないことを基本方針にする。

## 基本的な設定

ソフトウェアアップデート後、様々な基本設定

- システム環境設定 > デスクトップとスクリーンセーバー 
    - 壁紙を自分のデフォルトのものに変更
- システム環境設定 > Dock 
    - `画面上の位置:` を左に、またサイズを適当に調整
    - `Dockを自動的に表示/非表示`をチェック
    - `最近使ったアプリケーションをDockに表示`のチェックを外す
- システム環境設定 > Mission Control
    - `最新の使用状況に基づいて操作スペースを自動的に並べ替える`のチェックを外す
    - またCtrl+上でミッションコントロールを開き、仮想ディスプレイを追加しておく
- システム環境設定 > セキュリティとプライバシー
    - `プライバシー`の`フルディスクアクセス`に`ターミナル`を追加
- システム環境設定 > サウンド 
    - `起動時にサウンドを再生を外す`のチェックを外す (当初なぜか外せなかったが、Big Surを11.4にアップデートしたらできた)
- システム環境設定 > キーボード 
    - `修飾キー`で Caps Lock と Controlを入れ替える
- システム環境設定 > トラックパッド
    - `タップでクリック`をチェック
    - `スクロールの方向: ナチュラル`のチェックを外す
- システム環境設定 > バッテリー
    -  `電源アダプタ`の`ディスプレイがオフのときにコンピュータを自動でスリープさせない`をチェック
- システム環境設定 > 共有
    - コンピュータ名を変更しておく
- Finder > 環境設定
    - `デスクトップに表示する項目:`の`ハードディスク`をチェック
    - `すべてのファイル名拡張子を表示`をチェック
    - `サイドバーに表示する項目`にホームディレクトリを追加

## VPN接続設定

省略、`すべてのトラフィックをVPN接続経由で送信`をチェックしておく

## zsh

デフォルトがzshのようなのでそのまま使用。他のmacから`.zshrc`をコピーすれば良い。

## Xcode

今回はコマンラインツールのみ入れることにする。
```
xcode-select --install
```

## Karabiner-Elements

M1対応済。[公式](https://karabiner-elements.pqrs.org)からダウンロードしてインストール。指示にしたがって色々設定。
- セキュリティとプライバシー > 入力監視
    - `karabiner-grabber`と`karabiner-observer`を許可
- システム環境設定 > キーボード 
    - Karabinerについても`修飾キー`で Caps Lock と Controlを入れ替える

Karabiner-Elementsを起動し、Complex modification > Add rule > Import more rules from the Internet を選んでブラウザ上で International > For Japanese (日本語環境向けの設定) を import する。その後`コマンドキーを単体で...`を enable すればCommandキーによる日本語入力切り替えができるようになる。

## Safari

ブックマークは他のmacから`~/Library/Safari/Bookmarks.plist`をコピーすれば良い。環境設定で`ダウンロード後安全なファイルを開く`のチェックを外す。

## Chrome

M1対応済。[公式](https://www.google.com/intl/ja_jp/chrome/)からダウンロードする。

## homebrew

M1対応済。[公式](https://brew.sh/index_ja)に従ってターミナルからインストール
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
最後にパスを通すように言われるので`.zshrc`を指示に従って編集。その後いろいろインストールしておく
- `brew install gsl`
- `brew install cfitsio`
- `brew install fftw`
- `brew install imagemagick`
- `brew install wget`
- `brew install gnuplot`
- `brew install --cask emacs`

emacsは文句を言われて開けないので、システム環境設定 > セキュリティとプライバシー > 一般から実行許可を与えると、その後普通に開けるようになる。

brewにより`python`も入っている。`/opt/homebrew/opt/python/libexec/bin`をパスに追加し、pipでいろいろ入れてみる
- `pip install matplotlib`
- `pip install pandas`  
- `pip install jupyter`
- `pip install astropy` **なぜか失敗**、とりあえず保留

miniforgeを入れたほうが良いのかもしれないが、とりあえず後で検討する。

## latex

[Tex Wiki](https://texwiki.texjp.org/?TeX%20Live%2FMac)を参考にするとよい。GUIは使わないのでhomebrewでmactex-no-guiを入れる。
```
brew install --cask mactex-no-gui
```
やたら時間がかかるがひたすら待つ。入ったらターミナルを再起動して
```
sudo tlmgr update --self --all
sudo tlmgr paper a4
```
これも時間がかかったが無事インストールできたようだ。

## zoom

M1対応済。[公式](https://zoom.us/jp-jp/meetings.html)からインストーラをダウンロードして入れる。

## VScode

[vscode.md](/vscode.md) に別途記載する。

## Todo

- メーラー (thunderbirdから移行したい)
- python周りの整備
