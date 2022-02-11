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
- `pip install astropy` (なぜか失敗したが、後日やり直したら無事入った)

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

## git

初期設定をする (名前とメールアドレスは適宜自分のものに置き換える)
```
git config --global user.name "My Name"
git config --global user.email myaddress@myaddress
```
設定の確認をするには
```
git config -l   
```

## zoom

M1対応済。[公式](https://zoom.us/jp-jp/meetings.html)からインストーラをダウンロードして入れる。画面共有をするには セキュリティとプライバシー > プライバシー > 画面収録にzoomを追加する必要があるので注意。

## Slack

App storeからデスクトップアプリをインストールできる。

## VScode

[vscode.md](/vscode.md) に別途記載する。

## Spark

thunderbirdからの移行のテストにインストール。App storeからM1対応のものがインストールできる。(おそらくGmailで送信元アドレスとして登録されていれば) Gmailアカウントの送信元アドレスの変更は 環境設定 > アカウント > メールエイリアス に変更したいアドレスを入力すれば可能。

## Thunderbird

やっぱりthunderbirdを入れることにする。M1ネイティブ対応済。[公式](https://www.thunderbird.net/ja/)からダウンロードしインストール。gmailアドレスを入力し初期設定後
- ツール > アカウント設定
    - デフォルト差出人情報のメールアドレスを変更
    - SMTPサーバーを編集
- ツール > アカウント設定 > サーバー設定
    -  `新着メールがないか1分ごとに確認する` (1分に設定)
    -  `終了時にゴミ箱を空にする`をチェック
- ツール > アカウント設定 > 送信控えと特別なフィルター
    -  `次のメールアドレスをBccに追加する`をチェックしアドレス入力
    -  `アーカイブの保存先`のチェックを外す
- ツール > アカウント設定 > 編集とアドレス入力
    -  `HTML形式でメッセージを編集する`のチェックを外す
- ツール > アカウント設定 > ディスク領域
    - `最近30日分のメールをローカルに同期する`をチェック
- Thunderbird > 設定 > 一般
    - `ファイルと添付`で`次のフォルダーに保存する`をチェックし`ダウンロード`を選択
    - `既読と表示`で`アドレス帳に登録されている人については...`のチェックを外す
    - `ディスク領域`の`最適化する前に毎回確認する`のチェックを外す
    - `設定エディター`で`mail.wrap_long_lines`を`false`にする

- Thunderbird > 設定 > 編集
    - `次のサイズより大きなファイルの添付時に...`のチェックを外す

## Microsoft 365

サイトライセンスがあるので[サインインしてOfficeをダウンロードしインストール](https://support.microsoft.com/ja-jp/office/microsoft-365-または-office-2021-を-pc-または-mac-にダウンロードしてインストール-または再インストールします-4414eaaf-0478-48be-9c42-23adc4716658#bkmk_signintodownload)を参考にインストールする。驚くべきことにTeamsはM1非対応 (2022年2月現在) らしい。WordやExcelは対応済。

## Todo

- python周りの整備
