## ツール類のインストール
まずcmake以外のツールをインストールします。
```
apt update && apt install gcc g++ git libopencv-dev python3-pip
```
ubuntu 20.04LTSのリポジトリに含まれるcmakeのバージョンは3.16で
darknetのビルドには3.18以降が必要なので、kitware(cmakeの開発元)の
APT repositoryを追加してそちらからインストールします

```
apt install pgp wget
wget -O - https://apt.kitware.com/keys/kitware-archive-latest.asc 2>/dev/null | gpg --dearmor - |tee /usr/share/keyrings/kitware-archive-keyring.gpg >/dev/null
echo 'deb [signed-by=/usr/share/keyrings/kitware-archive-keyring.gpg] https://apt.kitware.com/ubuntu/ focal main' | tee /etc/apt/sources.list.d/kitware.list >/dev/null
apt update
rm /usr/share/keyrings/kitware-archive-keyring.gpg
apt install kitware-archive-keyring
apt install cmake
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
