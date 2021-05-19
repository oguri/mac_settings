# VScode 設定メモ

これまでemacsを使っていたが、思い立ってVScodeを使ってみることにする。インストールは[公式](https://code.visualstudio.com)からユニバーサルバイナリをダウンロードするだけ。しばらくは英語版のままで使ってみる。

## codeコマンドの設定

`Cmd+Shift+P` から `Shell Command: install 'code' command in PATH` を選ぶ。これでターミナルから
```
code .
```
などで立ち上げることができるようになる。

## extensionのインストール

- Awesome Emacs Keymap 
- Python
- C/C++ 
- Jupiter
- Code Spell Checker
- HTML Preview
- Latex Workshop
- Markdown PDF
- terminal-command-keys

## 設定 (Code > Preferences > Settings)

- `Latex-workshop > Latex > Auto Build: Run` を `never` にする
- `Markdown-pdf: Executable Path` に以下のパスを追加
```
/Applications/Google Chrome.app/Contents/MacOS/Google Chrome
```

## terminal-command-keys

`Cmd+Shift+P` から `Preferences: Open Keyboard Shortcuts (JSON)` を選び設定を書く。現在の設定は
```
[
    {
        "key": "ctrl+z",
        "command": "undo",
        "when": "editorTextFocus"
    },
    {
        "key": "cmd+r",
        "command": "latex-workshop.refresh-viewer"
    }
]
```

## Todo

- PDFがすんなりと表示できないことがあるのを直せないか？
