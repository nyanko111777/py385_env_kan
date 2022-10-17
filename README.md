# python385_env

[USBメモリがあればどこでも使えるPython + JupyterLab環境の作り方](https://gammasoft.jp/blog/python-and-jupyterlab-in-usb-stick/)をもとにpython3.8.5の可搬環境を作りました
Windows embeddable package を使用 

## python環境ずくり

### 初期設定
1. 名前を変更 ：　短くしておく、setenv.batと名前を合わせる
1. python38._pthの#import siteの先頭の#を消す
1. get-pip.pyを`https://bootstrap.pypa.io/get-pip.py`からダウンロードして、pythonフォルダに入れる
1. pythonの実行ファイルのあるフォルダで、`python.exe get-pip.py`を実行してpipを入れる
1. python38._pth の名前を変えて無効化する（パスの関係で読み込めない）
   例）python38._pth　→　python38._pth_muko


### ライブラリ
```
python.exe -m pip install jupyterlab
python.exe -m pip install numpy
python.exe -m pip install pandas
python.exe -m pip install pysimplegui
python.exe -m pip install pyperclip
python.exe -m pip install openpyxl
python.exe -m pip install xlwings
python.exe -m pip install pendulum
python.exe -m pip install jupytext
python.exe -m pip install nicegui
python.exe -m pip install justpy
python.exe -m pip install zeep
python.exe -m pip install xmltodict
```

```
python.exe -m pip uninstall jedi
```

### JupyterLab extention

1. outside, do a jupyter lab install of all extensions of interest
1. copy $PREFIX/share/jupyter/lab/static from the outside machine onto a shared/thumb drive
1. inside, overwrite/create that same folder

```

python.exe -m pip pip install jupyterlab-language-pack-ja-JP

jupyter labextension install @jupyterlab/toc

jupyter labextension install @jupyterlab/git
python.exe -m pip install jupyterlab-git
jupyter serverextension enable --py jupyterlab_git

python.exe -m pip install ipywidgets
jupyter labextension install @jupyter-widgets/jupyterlab-manager
jupyter nbextension enable --py --sys-prefix widgetsnbextension

```


### Tkinter
[参考](https://tanakatarou.tech/345/)

1. 必要ファイルをPython embeddable の中にコピーする
   すでにインストールされている環境から以下をコピー。全部直下に入れる
    1．tcl　（フォルダ）
    2．Lib/tkinter　（フォルダ）
    3．DLLs/tcl86t.dll　（ファイル）
    4．DLLs/tk86t.dll　（ファイル）
    5．DLLs/_tkinter.pyd　（ファイル）

### 必要に応じて
```
python.exe -m pip install beautiflsoup4
python.exe -m pip install matplotlib
python.exe -m pip install japanize-matplotlib
python.exe -m pip install seaborn
python.exe -m pip install PyPDF2
python.exe -m pip install docx2txt
python.exe -m pip install python-docx
python.exe -m pip install python-pptx
python.exe -m pip install selenium
python.exe -m pip install img2pdf
python.exe -m pip install pdf2image
python.exe -m pip install pptx2md
python.exe -m pip install mouse
python.exe -m pip install PyMuPDF
python.exe -m pip install cufflinks
```


## nodejs

`https://nodejs.org/ja/download/`からバイナリを落として解凍し、setenv.batに合わせて配置

### jupyterにカーネルを追加

```
npm install -g ijavascript
ijsinstall
jupyter kernelspec list
```

## dotnet

1. dotnet.7zを解凍して、pythonの中に配置
1. setenv.batのpathにdotnet interactiveのexeのパスを通す
1. dotnet interactiveのコマンドでkernelを追加