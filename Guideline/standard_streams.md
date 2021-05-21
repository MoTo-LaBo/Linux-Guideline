# 標準ストリーム
標準入出力
- 標準入出力とは、プログラムが、特に何も指定されていない場合に利用するデータの標準的な入出力先
### 標準入出力
- 標準入力　　　　stdin　　　キーボード　ファイル
   - プログラムの標準の入力
   - キーボードが通常は使われる
- 標準出力　　　　stdout　　ディスプレイ
   - プログラムの標準の出力
   - ディスプレイが通常は使われる
- 標準エラー出力　stderr　　ファイル
   - プログラムのエラーメッセージを出力
   - ディスプレイが通常は使われる
> ※ Linux ではコマンドの入出力先を抽象化することで、入出力先を柔軟に変更できる。
- ls コマンドの入力で less コマンドの出力にすることもできる
   - そうすることによって、コマンドを組み合わせて複雑な処理もできる
## { > } リダイレクト　重要！！
- 入出力先を変更する機能
コマンド結果をdisplayではなくファイルに描き込むなどができる
### 入力のリダイレクト
- キーボードの代わりにファイルからの入力にする機能
- ファイルからデータをそのまま渡す
#### dir/test.txt ファイルを入力元にして cat コマンドを実行
    cat < / dir/test.txt
> ※ <(小なり記号)記述が無くてもコマンドは実行できる 。何度も同じコマンドを利用する場合に使う。ミスなどが無くなる。
### 出力のリダイレクト
- コマンドの実行結果をファイルに保存する機能
#### ls コマンドの出力先をls.txtに保存
    ls > output.txt
    cat > output.txt
> ※ 長い結果をファイルでまとめて見れる。いつでも見返すことができる。
### エラー出力とリダイレクト
- 出力とエラー出力は別で、エラー出力は{ 2> }を使用する
### 標準入出力の数値
標準入出力などをOSが識別するための用いる識別子
- 標準入力　　　　　０
- 標準出力　　　　　１
- 標準エラー出力　　２
### エラー出力のリダイレクト
#### エラー結果をdisplayに表示するのではなくファイルに保存する機能
    ls /test.txxt 2> error.txt
- cat error.txt → ls: /test.txt にアクセスできません:
#### 出力とエラー出力をまとめる
    ls //dir > output.txt 2>&1
- まとめる場合は、出力をダイレクトした後に「２＞＆１」と記述
> ※ ２＞＆１は output(&1)へ error(2) を > (出力)するという意味
#### リダイレクトで追記する
    echo Hello! >> output.txt
- ＞ でリダイレクト指定するとファイルを**上書きしてしまう**
- ＞＞ でリダイレクト指定するとファイルを**追記する形になる**
## /dev/null について
入力先として指定しても何も返さず、出力先とし指定してもデータは消え何も表示されない、スペシャルファイル
### 入力先として指定
- 入力が何もない状態になる
- コマンドのテストなどで入力をからにしたい時
- $ cat < /dev/null
   - $
> ※ 何も表示されない
### 出力先として指定
- 結果が何も表示されなくなる
- 結果が大量にあり、結果を非表示にしたい時
- ls / > /dev/null
   - $
> ※ 何も表示されない
## [ | ] パイプラインについて
複数のコマンドを連携させる機能。コマンドの標準出力を別のコマンドの標準入力につなげる。何個でもつなげる事ができる
- [コマンド] | [コマンド]
- $ ls /bin | less
- $ ls /bin | grep systemd | less
   - コマンドを複数つなげることができる。grepというのは指定した文字列で検索して該当するものを表示するコマンドで、結果を絞りたい時によく使う