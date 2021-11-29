# my_PKGBUILD

## 個人のPKGBUILD置き場。

Archを使うなら、カーネルビルドしてカスタムカーネルくらい作りたい。そしてカーネルトレースしていじりたい。
ということでカーネルのPKGBUILDです。straceやperfもいいですが、やはりftrace、kprobeをやりたい。
そんなわけでカーネルコンフィグレーションを有効にしてみました。

しかし、debugfsがtracefsに移行したため、カーネルビルドは不要と判明。(古いカーネルでは多分必要)
ということであまり意味はありませんが、ftraceを使ってみます。

ftraceの使い方は簡単。trace-cmdを入れるだけ。以下はUbuntu系の例。

*# apt-get install trace-cmd*

lsコマンドについてトレースログを取得する。

*$ sudo trace-cmd record -p function_graph ls*

カレントディレクトリにtrace.datファイルが作成されるので表示する。

*$ trace-cmd report | less*

Linux Mint での実行結果。

![トレースログ](https://user-images.githubusercontent.com/55984656/71972734-a0840300-3250-11ea-99ad-37c44af96fca.png)


straceでコマンドのスタックトレースをするには、

*$ strace ls /home/hoge/*

などとすれば、端末に表示されます。

*$ strace -p [pid]*

などもできるらしい。KernelSharkを使うとさらにいろいろできる。

以下のサイトを参考にしました。

<http://nopipi.hatenablog.com/entry/2015/12/20/195708>

<https://yohgami.hateblo.jp/entry/20130105/1357409238>

<http://blog.livedoor.jp/sonots/archives/18193659.html>

<https://www.kkaneko.jp/tools/linuxtoolchain/tracecmd.html>

<https://qiita.com/hana_shin/items/c9bff5f5265bed27bb9f>

別にCTFに興味があるわけでもないが、このあたりの話題はrev、pwnなどと関係してくる。ハリネズミ本や徳丸本、迷路本などが参考になるらしい。gdbのbacktrace、gdb-peda、objdump、Ghidraなどがキーワードとして出てくる。CTFに興味ある人は調べてみればいいのでは。



