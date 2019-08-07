---
title: conda経由でインストールしたgraphvizが動かない問題の対処方法
---

## 環境

- OS: Windows 10
- Miniconda: Miniconda3-4.5.4 (64bit)
- Python: 3.6
- pydot: 1.2.4
- graphviz: 2.38
- python-graphviz: 0.8.4

## 再現方法

- `conda`を使って, `python-graphviz`と`pydot`をインストールした仮想環境を作成する.
- 作成した仮想環境を有効にして, `python`インタプリタから, `import pydot; pydot.Dot.create(pydot.Dot())`を実行する.
- `FileNotFoundError: [WinError 2] "dot.exe" not fount in path.`が発生する.

```shell
> conda create -n dot python=3.6 pydot python-graphviz
> conda activate dot
> python
>>> import pydot
>>> pydot.Dot.create(pydot.Dot())
FileNotFoundError: [WinError 2] "dot.exe" not found in path.
```

## 影響範囲
`pydot.Dot.create(pydot.Dot())`が使用されているライブラリ.

例)
- `Keras` (モデルの可視化)

## 原因
- `graphviz`の実行ファイル(`dot.ext`)が別の名前(`dot.bat`)でインストールされている.

## 解決方法
- `dot.exe`のあるとこにパスを通す. (リンクでも可?)
- `pydot.py`を編集し, `dot.bat`をさがすように変更する. (https://github.com/ContinuumIO/anaconda-issues/issues/1666)
- `conda`を使わない. (Windowsだとパスなどが面倒)

## まとめ

近いうちに修正されると思いますが, このようにすれば解決できます.
