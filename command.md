# Linux command
## Linux CLI
command で分からない事が有ったらまずは公式マニュアルを見る事
### --help オプション
    <command> --help
#### 例）
    $ ls --help
    使用方法：ls[オプション]...[ファイル]...
- 使用方法、コマンド概要、利用可能なオプション一覧を教えてくれる
### man コマンド(コマンドマニュアル)を表示
    man<調べたいコマンド名>
#### 例）1
    $ man ls
    NAME
    　　ls - list directory contents
#### 例）2
    $ man -k move # moveに関連したモノが出てくる
- --help オプションより詳しい！
#### カーソル移動
- `Ctrl + f`　　　　　1文字次へ移動
- `Ctrl + b`　　　　　1文字前へ移動
- `Ctrl + a`　　　　　行の先頭に移動
- `Ctrl + e`　　　　　行の最後に移動
- `esc  + f`　　　　　一単語次へ移動
- `esc  + b`　　　　　一単語前へ移動
- #### 文字列の編集
- `Ctrl + h`　　　　　カーソルの左を１文字削除
- `Ctrl + d`　　　　　カーソル部分を１文字削除
- `Ctrl + w`　　　　　カーソル位置の単語を削除（カーソルの前部分）
- `Ctrl + u`　　　　　カーソルの位置から行頭まで削除
- `Ctrl + k`　　　　　カーソルの位置から行末まで削除
- `Ctrl + y`　　　　　最後に削除した内容を挿入
#### トラブル時の対応
- `Ctrl + c`　　　　　実行中のコマンドを強制終了
- `Ctrl + l`　　　　　画面の消去。文字化けした時のクリアにも使える
- `Ctrl + s`　　　　　画面表示のロック。（キーボードから文字の入力を受け付けない）
- `Ctrl + q`　　　　　画面表示のロック解除
#### 補完・コマンド履歴
- `Tab　　　　　　　　コマンドやパスの補完
- `Ctrl + p`　　　　　1つ前の履歴を見る
  ※ または ↑ キー
- `Ctrl + n`　　　　　1つ後の履歴を見る
  ※ または ↓ キー
- `Ctrl + r`　　　　　コマンド履歴のインクリメンタル検索
     -  文字の入力　　　　　最後に削除した内容を挿入
     - `Ctrl + r`　　　　　1つ前の検索結果へ移動
     - `Enter`　　　　　　　現在の検索結果を実行
     - `Esc`　　　　　　　　現在の検索結果を表示したままコマンドラインに戻る
     - `Ctrl + g`　　　　　検索結果を破棄し、コマンドラインに戻る
## directory
- fileが保存されている場所
- 入れ子構造になっている
- ルートディレクトリを頂点とした階層構造になっている。
   - 「 directory tree 」と呼ぶ
   - 一番上の " / " をルートディレクトリと呼ぶ
#### directory command
- cd　　　　　　　　　　directory 移動
- pwd　　　　　　　　　カレンdirectory 表示 (自分のいる現在位置)
- ls　　　　　　　　　　directory 中身を表示
- mkdir　　　　　　　　directory 作成
- rkdir　　　　　　　　directory 削除
#### $ pwd 今自分がいる directory の場所
    pwd
#### $ ls -l fileの詳細情報を表示
    ls -l
#### $ ls -a 隠しfile表示
    ls -a
#### $ ls -F file種別を表示
    ls -F
#### 　*　任意の文字列/拡張子がhtmlのfileの一覧を表示
    *.html
#### 　?　任意の１文字/zから始まり４文字で終わるfileを表示
    /bin/z???
- /bin/zcat  /bin/zcmp  /bin/znew
#### $ mkdir directory
    mkdir test
#### $ make directory -p
    midir -p test/2019/08
- 深い directory (入れ子構造)を一度に作成
#### $ rmdir code空の directory 削除
    rmdir code
-  code directory が空であれば削除される
>  ※ 空でない directory を削除しようとするとerror になる。中にfileが残っていることを知らなくて気づかずに削除する事を防げる

>  ※ 隠しfileがあって削除できないことがある
## file の操作
### cat ファイルの中身を表示・確認
