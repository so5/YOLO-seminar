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
m1 macではlabelImgの依存ライブラリ(pyqt5)がインストールできないため
通常のpipコマンドによるインストールは失敗します。

ここでは、githubからpyside6に対応したバージョンを取得して
ソースからインストールします。

初めに、インストール時に使うpipenvをインストールします
```
pip3 install pipenv
```

続いてソースコードをgithubから取得し、pyside6ブランチに切り替えてビルドします。
```
git clone https://github.com/tzutalin/labelImg.git
cd labelImg
git checkout pyside6
pipenv run pip install pyside6 lxml
pipenv run make pyside6
```
最後に次のコマンドを入力してlabelImgが起動するか確認してください
```
pipenv run python3 labelImg.py
```
