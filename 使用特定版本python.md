# 在系統中已有一個python時使用另一個版本的python
為了解決64位元版本的python在使用pyinstaller封裝的程式無法在32為原版本電腦上執行的問題

## Step 1 下載embed版本的python
[python-windows連結](https://www.python.org/downloads/windows/)

尋找標示為embeddable package的檔案，注意python版本可能會與系統有相容性問題，解壓縮後即可得到python本體，為了避免混亂可以將python.exe重新命名，這不會影響執行

## Step 2 安裝pip
下載 [get-pip.py](https://bootstrap.pypa.io/get-pip.py)，在embed-python目錄下使用新的python執行

## Step 3 修改路徑
`pythonxx._pth`檔案末尾記述了該python獨有的路徑，在末尾加上希望保留的路徑。
```vbnet
.
./Lib
./Lib/site-packages
```
如此才可以安全執行pip，注意想要使用pip需要直接調用`.\Scripts\pip.exe`

## Step 4
後續執行時如果出現找不到自定義包時可以將執行路徑也加入._pth檔案中

## 追加 pyinstaller
直接將欲打包的所有檔案放入`site-packages/Pyinstaller`位置，然後使用`__main__.py`打包即可
