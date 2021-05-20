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
## file の操作
## $ cat ファイルの中身を表示・確認
concatenate の略  ：結合
- 今回はLinuxだが、Mac ターミナル(zsh)の場合は cat Desktop/test/test.txt  スラッシュ/は必要ない！
#### $ cat [オプション]<ファイル名>
    cat /Desktop/test/test.txt
#### $ cat -n 行番号を表示する
    cat /Desktop/test/test.txt
#### $ cat <ファイル名><ファイル名> 複数指定できる ※順表示になる
    cat /Desktop/test/test.txt /Desktop/test2/test2.txt
## $ less ファイルの中身をスクロール表示させる
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
## $ touch ファイルの作成
touch の略：空のファイルを作成するコマンド
#### $ touch <新規ファイル><新規ファイル２>
    touch README.md
- 間違っている存在しているファイルを指定しても上書きされない
- ファイルがあるときはタイムスタンプを更新する
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
## $ mv ファイル移動/ファイル名変更
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
##
