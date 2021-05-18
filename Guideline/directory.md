# directoryについて
## directory
- fileが保存されている場所
- 入れ子構造になっている
- ルートディレクトリを頂点とした階層構造になっている。
   - 「 directory tree 」と呼ぶ
   - 一番上の " / " をルートディレクトリと呼ぶ
#### ディスクを directory として扱う「 マウント 」
- ドライブという概念がない。１つの directory tree しか持たない
>  ※ windows の様なディスクが、Ｃドライブ、Dドライブがあり、ドライブから始まって２つの directory tree を持つ。
#### /bin
- 実行fileを格納
- Linuxの動作に最低限度必要な重要度が高いコマンドの実行file
#### /dev
- デバイスファイル（ハードウェアをfileとして扱えるようにしたfile）格納
#### /etc
- 設定file格納
- Linuxで動作するアプリケーションの設定file
- Linux自体の設定に関わるfile
#### /home **基本はこちらで作業する**
- ホームdirectory（userごとに割り当てられた個人用directory）
- user は home directory 内に自由にfileやdirectoryを作成できる
#### /sbin
- 管理者 user 向けのコマンドの実行file格納
#### /tmp
- 一時的なfile格納
- アプリケーションの実行中に結果をを一時的にfileとして保存する場合に使用
>  ※ 定期的に削除されるので、ずっと保存したfileはNG
#### /usr
- 各種アプリケーションとそれに付随するfileを格納
- 実行file、ドキュメント、ライブラリーがこの下の下層に置かれる
#### /var
- 変化するデータを格納
- アプリケーションを動作する上で作成されたログなどを格納
#### directory command
- cd　　　　　　　　　　directory 移動
- pwd　　　　　　　　　カレンdirectory 表示 (自分のいる現在位置)
- ls　　　　　　　　　　directory 中身を表示
- mkdir　　　　　　　　directory 作成
- rkdir　　　　　　　　directory 削除
## pwd コマンド
カレンディレクトリを表示するコマンド
- print name of working directory
>  ※ 自分のいる現在位置
#### $ pwd 今自分がいる directory の場所
    pwd
- /home/moto
## ls コマンド
- list の略
#### $ ls -l fileの詳細情報を表示
    ls -l
- drwxrwxrwx 1 moto moto　4096 May 4 11:12　vscode
1. drwxrwxrwx　　　　ファイルタイプ・ファイルモード
2. 1　　　　　　　　　リンク数
3. moto　　　　　　　所有者
4. moto　　　　　　　所有者グループ
5. 4096　　　　　　　サイズ
6. May 4 11:12　　　　タイムスタンプ
7. vscode　　　　　　directory名
#### $ ls -a 隠しfile表示
    ls -a
- .bash_history　.bashrc　.gitconfig
#### $ ls -Ffile種別を表示
    ls -F
- dev/   init*  lib64@  home
- /　　　　　　directory
- @　　　　　　シンボリックリンク
- *　　　　　　実行可能ファイル
- 記号なし　　　通常ファイル
### パス名展開
パス名展開を使用すると複数fileを一度に指定できる
#### 　*　任意の文字列
    # 拡張子がhtmlのfileの一覧を表示
    *.html
- index.html  home.html  contact.html
#### 　?　任意の１文字
    # zから始まり４文字で終わるfileを表示
    /bin/z???
- /bin/zcat  /bin/zcmp  /bin/znew
## mkdir コマンド
directory 作成
#### $ mkdir directory
    mkdir code
- code という directory ができる
>  ※ directory名は英語で表記。日本語だと文字化けする恐れがある
#### $ make directory -p
    midir -p test/2019/08
- 深い directory を一度に作成
1. test directory の中に
2. 2021 directory があって
3. 2021 directory の中に
4. 05   directory がある
## rmdir コマンド
空の directory 削除
- remove directory
#### $ rmdir code
    rmdir code
- 空であれば code directory は削除される
>  ※ 空でない directory を削除しようとするとerror になる。中にfileが残っていることを知らなくて気づかずに削除する事を防げる

>  ※ 隠しfileがあって削除できないことがある
## パスについて
パスは directory や file の住所情報
> ※　directory 階層の区切りは「 / 」で表現
#### 絶対パス
- / (ルートディレクトリ) から始まる
   - /home/kume/code/READKE.md
#### 相対パス
- / (カレントディレクトリ) から始まる
   - code/READKE.md
#### 使い分け point
- 確実に指定したいときは、絶対パス
- 簡単に指定したいときは、相対ぱす
>  ※ 実際はケースバイケースである事が多い
#### 特別な directory 表記
1. 絶対パス
- /home/kume/code/READKE.md
   - / 　　　　　　　　　　　　　　→　ルート directory
   - /home　　　　　　　　　　　　→　親　directory
   - /home/kume　　　　　　　　　→　カレント directory (現在位置)
   - /home/kume/code
   - /home/kume/code/README.md
1. 相対パス
-  .  (ドッド)はカレントdirectory
-  .. (ドッド２つ)は親 directory
#### /home/kume/code/READKE.md
   - ../..　　　　　　　　　 /
   - ..　 　　　　　　　　　　/home
   - .　 　　　　　　　　　　　/home/kume
   - code または ./code　 /home/kume/code
   - ./code/work　　　　　 /home/kume/code/README.md
   - code/work　　　　　　 /home/kume/code/README.md
