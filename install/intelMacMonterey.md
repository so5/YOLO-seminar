## ツール類のインストール
### Xcode command line tool
terminalアプリを開いて次のコマンドを実行してください。
```
gcc --version
```
ダイアログが表示された場合は、「インストール」をクリックすると、
command line toolのインストールが始まります。

gccのバージョン番号が表示された場合は、command line toolはインストール済なので
homebrewのインストールに進みます。

### homebrewのインストール
次のコマンドを実行してhomebrewをインストールします。
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
最初にsudoのためのパスワードを聞かれるので入力してください。
その後`Y`を入力するとインストールが始まります。

### OpenCV,cmakeのインストール
次のコマンドを入力してdarknetのビルドに必要なパッケージをインストールします。
```
brew install opencv cmake
```

## darknetのビルド
githubからソースを取得します。
```
git clone https://github.com/AlexeyAB/darknet.git
```
cloneしてきたディレクトリに移動してビルドします
```
cd darknet
mkdir build_release
cd build_release
cmake .. -DENABLE_CUDA=OFF
cmake --build . --target install
```

正常にビルドできたら、darknetディレクトリの直下に`darknet`という実行ファイルが生成されているので確認しましょう。

```
ls -l  ../darknet
```

## labelImgのインストール
デフォルトのpip3(20.2.3)ではlabelImgのインストールに失敗するので
先にpipのアップデートを行ないます。
```
/Library/Developer/CommandLineTools/usr/bin/python3 -m pip install --upgrade pip
```
続けて、pip3を使ってlabelImgをインストールします。
```
pip3 install labelImg
```
最後に次のコマンドを入力してlabelImgが起動するか確認してください
``
~/Library/Python/3.8/bin/labelImg
```
