# MacBook 設定メモ (2024年9月)

詳細

- MacBook Air (M3, 2024)
- macOS: Sonoma
- memory: 24GB
- storage: SSD 2TB
- USキーボード

移行アシスタントを使わず一から設定する。

## 基本的な設定

ソフトウェアアップデート後、様々な基本設定

- Apple ID
    - iCloud Drive、Safari、Macを探すのみiCloudを使用
- システム環境設定 > サウンド 
    - `起動時にサウンドを再生`のチェックを外す 
- システム環境設定 > 集中モード
    - `デバイス間で共有`のチェックを外す
- システム環境設定 > 一般 > 情報
    - コンピュータ名を変更しておく
- システム環境設定 > 一般 > 共有
    - コンピュータ名を変更しておく
- システム環境設定 > コントロールセンター
    - `最近使った書類、...の表示数`を`なし`にする
- システム環境設定 > SiriとSpotlight
    - `プライバシー`にtmpを追加
- システム環境設定 > プライバシーとセキュリティ
    - `フルディスクアクセス`に`ターミナル`を追加-
- システム環境設定 > デスクトップとDock 
    - `画面上の位置:` を左に、またサイズを適当に調整
    - `Dockを自動的に表示/非表示`をチェック
    - `アプリの提案と最近使用したアプリをDockに表示`のチェックを外す
    - Mission Controlの`最新の使用状況に基づいて操作スペースを自動的に並べ替える`のチェックを外す
    - またCtrl+上でミッションコントロールを開き、仮想ディスプレイを追加しておく
- システム環境設定 > 壁紙
    - 壁紙を自分のデフォルトのものに変更
    - `スクリーンセーバー`の`ホットコーナー`で左上にスクリーンセーバーの開始を割り当てる
- システム環境設定 > バッテリー
    -  `オプション`で`電源アダプタ使用時はディスプレイがオフのときに自動でスリープさせない`をチェック
- システム環境設定 > キーボード 
    - `キーボードショートカット...`の`修飾キー`で Caps Lock と Controlを入れ替える
    - `キーボードショートカット...`の`入力ソース`のチェックを二つ外す
- システム環境設定 > トラックパッド
    - `ポイントとクリック`の`タップでクリック`をチェック
    - `スクロールとズーム`の`ナチュラルなスクロール`のチェックを外す
- Finder > 設定
    - `デスクトップに表示する項目:`の`ハードディスク`をチェック
    - `新規Finderウィンドウで次を表示`でホームディレクトリを選択
    - `すべてのファイル名拡張子を表示`をチェック
    - `サイドバーに表示する項目`から`最近の項目`を除く
    - `サイドバーに表示する項目`にホームディレクトリを追加
- Ctrl+クリック > 表示オプションを表示
    - アイコンサイズを調節

## zsh

デフォルトがzsh。他のmacから`.zshrc`をコピーすれば良い。

## Xcode

コマンラインツールのみ入れる。
```
xcode-select --install
```

## Karabiner-Elements

[公式](https://karabiner-elements.pqrs.org)からダウンロードしてインストール。指示にしたがって色々設定。
- セキュリティとプライバシー > 入力監視
    - `karabiner-grabber`と`karabiner-observer`を許可
- システム環境設定 > キーボード 
    - Karabinerについても`修飾キー`で Caps Lock と Controlを入れ替える

Karabiner-Elementsを起動し、Complex modification > Add predefined rule > Import more rules from the Internet を選んでブラウザ上で International > For Japanese (日本語環境向けの設定) を import する。その後`コマンドキーを単体で...`を enable すればCommandキーによる日本語入力切り替えができるようになる。

## Safari

ブックマークはiCloudで共有する。`表示`でお気に入りバーを常に表示にする。Ctrl+クリックでツールバーをカスタマイズする。
- 一般
    - `Safariの起動時:`を新規ウインドウに
    - `新規ウインドウを開く場合`と`新規タブを開く場合`を空のページに
    - `ホームページ`を自分のページに設定
    - `履歴からの削除`を一週間後に設定
    - `ダウンロード後安全なファイルを開く`のチェックを外す。

## Chrome

[公式](https://www.google.com/intl/ja_jp/chrome/)からダウンロードする。

## zoom

[公式](https://zoom.us/jp-jp/meetings.html)からインストーラをダウンロードして入れる。画面共有をするには プライバシーとセキュリティ > 画面収録にzoomを追加する必要があるので注意。
- 設定 > 画面の共有
    - `画面を共有している場合のウィンドウサイズ`を`現在のサイズを保持する`に変更
- 設定 > レコーディング
    - `レコーディングの保存場所`を変更

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

## FortiClient VPN

VPNで使用。証明書をインストールしその後[情報戦略機構](https://www.imit.chiba-u.jp/index.html)の研究用VPNのページからアプリをインストール。

## Thunderbird

[公式](https://www.thunderbird.net/ja/)からダウンロードしインストール。gmailアドレスを入力し初期設定後
- メニュー > 表示 > レイアウト
    - `クラシック表示`に変更
- メニュー > アカウント設定
    - デフォルト差出人情報のメールアドレスを変更
    - SMTPサーバーを編集
    - `差出人情報を管理`から署名を追加
          - `メッセージ送信時に自動的にコピーを作成する`のチェックを外す
          - `次のメールアドレスをBccに追加する`をチェックしアドレス入力
          - `アーカイブの保存先`のチェックを外す
          - `HTML形式でメッセージを編集する`のチェックを外す
          - `署名を挿入する位置`を`返信部の下`に
          - `転送メッセージに自分の署名を挿入する`をチェック
- メニュー > アカウント設定 > サーバー設定
    - `新着メールがないか1分ごとに確認する` (1分に設定)
    - `終了時にゴミ箱を空にする`をチェック
- メニュー > アカウント設定 > 送信控えと特別なフィルター
    - `メッセージ送信時に自動的にコピーを作成する`のチェックを外す
    - `次のメールアドレスをBccに追加する`をチェックしアドレス入力
    - `アーカイブの保存先`のチェックを外す
- メニュー > アカウント設定 > 編集とアドレス入力
    - `HTML形式でメッセージを編集する`のチェックを外す
    - `署名を挿入する位置`を`返信部の下`に
    - `転送メッセージに自分の署名を挿入する`をチェック
- メニュー > アカウント設定 > 同期とディスク領域
    - `最近30日分のメールをローカルに同期する`をチェック
- メニュー > 設定 > 一般
    - `Thunderbirdスタートページ`で`起動時にスタートページを表示する`のチェックを外す
    - `ファイルと添付`で`次のフォルダーに保存する`をチェックし`ダウンロード`を選択
    - `既読と表示`で`アドレス帳に登録されている人については...`のチェックを外す
    - `ディスク領域`の`最適化する前に毎回確認する`のチェックを外す
    - `設定エディター`で`mail.wrap_long_lines`を`false`にする
    - `設定エディター`で`mailnews.wraplength`を`0`にする
    - `設定エディター`で`mailnews.send_plaintext_flowed`を`false`にする
    - `設定エディター`で`mail.identity.???.suppress_signature_separator`を`true`にする
- メニュー > 設定 > 編集
    - `次のサイズより大きなファイルの添付時に...`のチェックを外す

## カレンダー

最初からインストールされている。使っているgoogleアカウントを追加。

## Microsoft 365

サイトライセンスがあるので[マイアカウント](https://portal.office.com)からOfficeアプリに行きダウンロード。

## Notion

[公式](https://www.notion.so/ja-jp/desktop)からダウンロードしインストール。

## Slack

[公式](https://slack.com/intl/ja-jp/downloads/mac)からダウンロードしインストール。

## Goodnotes

App Storeからインストール。

## homebrew

[公式](https://brew.sh)に従ってターミナルからインストール
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
- `brew install python`

`/opt/homebrew/opt/python/libexec/bin`をパスに追加する。pipはそのままでは使えないので仮想環境を作成する。

```
python -m venv .python/venv
```

.zshrcに`source .python/venv/bin/activate`を追加すると、自動的に仮想環境が起動しpipも使える。

- `pip install scipy`
- `pip install matplotlib`
- `pip install pandas`  
- `pip install setuptools_scm`
- `pip install cython`
- `pip install jupyter`
- `pip install astropy`
- `pip install colossus`
- `pip install healpy`
- `pip install ligo.skymap` [エラーが出た]
- `pip install japanize_matplotlib`

## latex

[Tex Wiki](https://texwiki.texjp.org/?TeX%20Live%2FMac)を参考にするとよい。GUIは使わないのでhomebrewでmactex-no-guiを入れる。
```
brew install --cask mactex-no-gui
```
入ったらターミナルを再起動して
```
sudo tlmgr update --self --all
sudo tlmgr paper a4
```

## ds9

[公式](https://sites.google.com/cfa.harvard.edu/saoimageds9)からAqua版をインストール。

## Apex One

サイトライセンスがあるのでインストール。

