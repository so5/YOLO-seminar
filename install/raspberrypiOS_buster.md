## ツール類のインストール
まずcmake以外のツールをインストールします。
```
apt update && apt install gcc g++ git libopencv-dev python3-pip libssh-dev
```

## cmakeのビルド
ラズパイOS(buster)のリポジトリに含まれるcmakeのバージョンは3.16で
darknetのビルドには3.18以降が必要なので、まずcmakeをソースからビルドします

kitwareの[webサイト](https://cmake.org/download/)からソースコードを取得します。

ソースを展開してビルドします
```
tar xfz cmake-3.*.tar.gz
cd cmake-3.??.?
./bootstrap --prefix=/usr/local
make
sudo make install
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
次のコマンドを実行します
```
apt install python3-pyqt5
pip install labelImg
```
最後に次のコマンドを入力してlabelImgが起動するか確認してください
```
labelImg
```
