# my_PKGBUILD

## 個人のPKGBUILD置き場。

Archを使うなら、カーネルビルドしてカスタムカーネルくらい作りたい。そしてカーネルトレースしていじりたい。
ということでカーネルのPKGBUILDです。straceやperfもいいですが、やはりftrace、kprobeをやりたい。
そんなわけでカーネルコンフィグレーションを有効にしてみました。

しかし、debugfsがtracefsに移行したため、カーネルビルドは不要と判明。(古いカーネルでは多分必要)
ということであまり意味はありませんが、ftraceを使ってみます。

ftraceの使い方は簡単。trace-cmdを入れるだけ。以下はUbuntu系の例。

*# apt-get install trace-cmd*

lsコマンドについてトレースログを取得するには以下を実行。

*$ sudo trace-cmd record -p function_graph ls*

trace.datファイルが作成されるので、以下のコマンドで表示。

*$ trace-cmd report | less*

これはLinux Mint での実行結果。

![トレースログ](https://user-images.githubusercontent.com/55984656/71972734-a0840300-3250-11ea-99ad-37c44af96fca.png)


straceでコマンドのスタックトレースをするには、

*$ strace ls /home/hoge/*

などどすれば、端末に表示されます。

*$ strace -p [pid]*

などもできるらしい。


