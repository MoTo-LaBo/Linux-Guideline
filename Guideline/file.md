# ファイルについて
Linuxのファイルには２種類ある
## テキストファイル
- 文字コードで定められた文字だけが並んで格納されているfile
- 文字コードとは、文字の種類に数値を割り振ったもの
   - pcでは文字は特定の数値の並びで表現されている。０と１でできている
#### **「Linuxではテキストfileはとても大切。OSに関わるほとんどの設定情報をtxtfileとして管理している」**
## バイナリファイル
- 文字コード以外の数値を含むようなファイル
- テキスト以外のものをバイナリファイナルと考えてOK
- cat コマンドなどではバイナリファイナルが文字化けするのは、無理矢理テキストファイルとして解釈しようとして、文字コードに該当した数値をその文字に置き換えて表示した為に理解し難い文字列になった
### $ cat ファイルの中身を表示・確認
concatenate の略  ：結合
- 今回はLinuxだが、Mac ターミナル(zsh)の場合は cat Desktop/test/test.txt  スラッシュ/は必要ない！
#### $ cat [オプション]<ファイル名>
    cat /Desktop/test/test.txt
#### $ cat -n 行番号を表示する
    cat /Desktop/test/test.txt
#### $ cat <ファイル名><ファイル名> 複数指定できる ※順表示になる
    cat /Desktop/test/test.txt /Desktop/test2/test2.txt
### $ less ファイルの中身をスクロール表示させる
less - opposite of more ：逆スクロールもできる
- 長文をfileの中身を確認したい時
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
### $ touch ファイルの作成
touch の略：空のファイルを作成するコマンド
#### touch <新規ファイル><新規ファイル２>
    touch README.md
- 間違っている存在しているファイルを指定しても上書きされない
- ファイルがあるときはタイムスタンプを更新する
### $ rm ファイル削除　(directoryの削除)
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
- $ mv [オプション]<移動元><移動先>
   - file・directory移動
- $ mv [オプション]<ファイル名><変更後file名>
   - file 名の変更
- $ mv -i <ファイル名><変更後file名>
   - 上書きする前に確認表示
#### ファイルを directory から出す
    mv test.txt ../
- 今いる directory から１つ上の階層の directory へ上がる
### $ cp コピーコマンド
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
### $ ln リンクを貼ろう
link の略
- $ ln [オプション]<リンク元ファイル名><リンク名>
### リンクを貼るとはどういうことか？
Linuxではファイルに別名をつける事ができ、別名をつけることを「リンクを貼る」という。Windowsでいうショートカットのようなもの
### ハードリンク
- 1つのファイルの実体に複数の名前をつける機能
- 元のファイルを削除しても消えない
- 全てのハードリンクが無くなった時に削除される
### シンボリックリンク
- リンク先のパス名が書かれた特殊ファイル。リンク先がファイルの実体
- シンボリックリンクを残したままファイル実態を削除したり、ファイル移動するとファイルを参照できなくなる。
>  ※ リンクが壊れたと言われる
#### ハードリンクを貼る
     ln file1 file2
- オプションをつけないとハードリンクになる
#### シンボリックリンクを貼る
     ln -s file1 file3
### リンクをどういう時に使用するのか？
- 長いパスを省略したい時
- 複数バージョンを共有させ最新を区別したい時
>※ ハードリンクとシンボリックリンクだと、シンボリックリンクの方が使う事が多い。ハードリンクはいくつか制限があって、異なるディスクをまたいで作成できなかったり、directoryに対して使えない。シンボリックリンクはそのような制限は受けない。
#### ファイルに引数を書き込む
    echo "hello" > file1
#### $ cat test2.txt で中身の確認
    cat file1
- hello と書き込まれている
#### ln コマンド使用　ハードリンク
    ln file1 file_hard
#### ln コマンド使用　シンボリックリンク
    ln -s file1 file_symbolic
#### 元ファイルfile1を削除で挙動確認　hard
    cat file_hard
- hello と表示される
#### 元ファイルfile1を削除で挙動確認　symbolic
    cat file_symbolic
- cat: file_symbolic: No such file or directory
> ※ そのようなファイル、ディレクトリはありませんと表示される。symbolicが壊れるという事。symbolic link は元のファイルのパス名が記載されているだけなので、元ファイルが無くなるとファイルが存在しなくなる為に上記のような表示になる
### $ find コマンド fileを検索する
find そのまま：ファイルを検索するコマンド
- $ find . -name README.md -print
-  .　　　　　　　　　　　　　検索開始directory(カレントディレクトリ)
- -name README.md　　　　検索条件
- -print　　　　　　　　　　　検索アクション
   - 例）./wordpress/.../README.md
> ※ 引数を起点にした(カレントdirectory)ファイル名がREADME.mdというfileを探して(-name〇〇)、見つかったらPATHを表示してという指示(-print)　※ -print の記述が無くても同じ意味になる
#### file名を指定して検索　※ **名は大文字・小文字は区別**
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
