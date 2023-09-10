# 針對所有套件分別獨立下載
```
pip install -r requirements.txt
```
是很好用的指令，但是如果遇到當中有一個套件無法安裝的話會停止並全數回滾，因此有
```
cat requirements.txt | xargs -n 1 python -m pip install
```
的作法