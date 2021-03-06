## ツール類のインストール
### MS Build tool
次のURLからMS Build toolのインストーラをダウンロードします。

<https://visualstudio.microsoft.com/ja/downloads/#build-tools-for-visual-studio-2022>

ダウンロードしたインストーラを起動し`C++によるデスクトップ開発`を選択してインストールボタンをクリックします。

![img](./img/buildTool.png "buildTool")


### OpenCV
次のURLからOpenCVをダウンロードします。

<https://sourceforge.net/projects/opencvlibrary/files/4.6.0/opencv-4.6.0-vc14_vc15.exe/download>

自己解凍式のアーカイブなので、ダウンロードしたexeファイルを実行して展開します。

### POSIX Threads for Windows
次のURLから`pthreads-w32-2-9-1-release.zip`をダウンロードし、展開してください。

<https://sourceforge.net/projects/pthreads4w/files/>

### python
次のURLにアクセスします。

<https://www.python.org/downloads/windows/>

"StableReleases" と書かれた側の最新バージョン(一番上のバージョン)のうち
"Windows installer"とかかれたexeファイルをダウンロードしてください。
32bit版と64bit版がありますので、お使いの環境に合わせて選んでください。

インストーラを起動すると、次の画面が表示されるので、最下部の`Add Python 3.10 to PATH`にチェックを入れてから、`Install Now`をクリックしてください。

![img](./img/pyhthonInstaller.png "pythonInstaller")

## darknetのビルド
次のURLにアクセスして`Code`と書かれたボタンをクリックし、`Download ZIP`を選択します。

<https://github.com/AlexeyAB/darknet>

![img](./img/downloadDarknet.png "downloadDarknet")

ダウンロードしてきたzipファイルは適当な場所に展開しておいてください。

gitが使える環境の方は次のコマンドを実行してソースコードをcloneしても構いません。
```
git clone https://github.com/AlexeyAB/darknet.git
```

スタートメニューから、`Developper Command Prompt for VS・・・`と書かれた
コマンドプロンプトを起動し、ソースディレクトリに移動してビルドします

![img](./img/cmdprompt.png "cmdprompt")

```
cd darknet
mkdir build_release
cd build_release
cmake -DCMAKE_PREFIX_PATH=C:\Users\sogo\Desktop\opencv\build -DENABLE_CUDA=OFF ..
cmake --build . --target install
```

cmakeの引数-DCMAKE_PREFIX_PATH`の後には、opencvのアーカイブを展開して生成されたディレクトリ内の`build`
ディレクトリのパスを指定してください。


正常にビルドできたら、darknetディレクトリの直下に`darknet.exe`という実行ファイルが生成されているので確認しましょう。
```
ls -l ../darknet.exe
```

### ライブラリのパス設定
事前にダウンロードしたOpenCVとpthreadのdllファイルをdarknet.exeと同じディレクトリにコピーするか
それぞれ環境変数PATHに追加してください

OpenCV: `opencv\build\x64\vc15\bin\opencv_world460d.dll`

pthread: `pthreads-w32-2-9-1-release\Pre-build.2\dll\x64\pthreadVC2.dll`

## labelImgのインストール
次のコマンドを実行します
```
pip install labelImg
```

最後に次のコマンドを入力してlabelImgが起動するか確認してください
```
labelImg
```
