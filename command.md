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
## cat ファイルの中身を表示・確認
- 今回はLinuxだが、Mac ターミナル(zsh)の場合は cat Desktop/test/test.txt  スラッシュ/は必要ない！
#### $ cat [オプション]<ファイル名>
    cat /Desktop/test/test.txt
#### $ cat -n 行番号を表示する
    cat /Desktop/test/test.txt
#### $ cat <ファイル名><ファイル名> 複数指定できる ※順表示になる
    cat /Desktop/test/test.txt /Desktop/test2/test2.txt
## $ less ファイルの中身をスクロール表示させる
#### $ less [オプション]<ファイル名>
    less /Desktop/test/test.txt
- スクロール時の操作
   - space 又は f　　　一画面下にスクロール
   - b　　　　　　　　一画面上にスクロール
   - j　　　　　　　　一行下にスクロール
   - k　　　　　　　　一行上にスクロール
   - q　　　　　　　　less コマンド終了
 - 検索の操作
   - /<文字列>　　　　less コマンド終了
   - ?<文字列>　　　　less コマンド終了
   - n　　　　　　　　次の検索結果に移動
   - N　　　　　　　　前の検索結果に移動
## $ touch ファイルの作成
touch の略：空のファイルを作成するコマンド
#### touch <新規ファイル><新規ファイル２>
    touch README.md
## $ rm ファイル削除　(directoryの削除)
remove の略：rmコマンドは実行すると、**ゴミ箱に行くのではなく本当に削除される**
- rm はfileを削除するコマンド。directory 削除はオプションをつける
####  file 削除
    rm REDME.md
#### -r　をつける directory も合わせて削除
    rm -r dir
- directory の中のファイルやディレクトリー自体もまとめて削除されるので注意！！
#### -f　をつける fileを削除する際に警告文が表示されない
    rm -f file
- 大量のfileを削除する時に使う。あまりお勧めしない
#### -i　をつける fileを削除する前に警告が表示される
    rm -i file
### $ mv ファイル移動/ファイル名変更
move の略
- $ `mv [オプション]<移動元><移動先>`
   - file・directory移動
- $ `mv [オプション]<ファイル名><変更後file名>`
   - file 名の変更
- $ `mv -i <ファイル名><変更後file名>`
   - 上書きする前に確認表示
#### ファイルを directory から出す
    mv test.txt ../
- 今いる directory から１つ上の階層の directory へ上がる
## $ cp コピーコマンド
copy の略：
- $ cp [オプション]<コピー元><コピー先>
#### fileをコピー
    cp test.txt new_test.txt
#### fileをdirectory 内にコピーする
    cp test.txt dir/
- コピー先のファイルがすでにあると上書きするので注意する！！
#### -i　をつける。上書きする前に確認してくれる
    cp -i test.txt new_test.txt
#### -r　をつける。directory をコピーする
    cp -r dir new_dir
- cpコマンドだけでは、directory はコピーできない。-r をつける
- directory の中身も一緒にコピーしてくれる
## $ ln リンクを貼ろう
- $ `ln [オプション]<リンク元ファイル名><リンク名>`
#### ハードリンクを貼る
     ln file1 file2
- オプションをつけないとハードリンクになる
#### シンボリックリンクを貼る
     ln -s file1 file3
## file名を指定して検索　※ **名は大文字・小文字は区別**
    find . -name README.md
#### ワイルドカードが使用できる　※ * を使って指定　' 〇〇 'シングルか” ”で囲う
    find . -name '*.htm' -print
>  ※ ＊(アスタリスク)は任意の文字列に一致する。？も使えて、任意の一文字に一致する。
>  ※ ' か " で囲わないと＊がbashのPATH名展開をしてしまう。.htmlという拡張子がついているfileを拾ってしまい、errorの表示がされる
#### -iname ファイル名を指定してfileを検索　※ **大文字・小文字は区別しない**
    find . -iname readme.md
### -type ファイルの種類で検索
#### -type f 通常のファイル
    find . -type f print
#### -type l シンボリックリンク
    find . -type l print
#### -type d directory
    find . -type f print
#### 複数の検索条件を指定。なお、 -aは省略可能
    find . -type d -a -name images -print
> ※ ディレクトリ名がimagesというものを検索してという意味
