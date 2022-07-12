## ツール類のインストール
まずcmake以外のツールをインストールします。
```
apt update && apt install gcc g++ git libopencv-dev python3-pip
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
