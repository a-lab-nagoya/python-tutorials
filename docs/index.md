---
marp: true
theme: gaia
paginate: true
backgroundImage: url('https://marp.app/assets/hero-background.jpg')
---

# Introduction to the programming language Python in radio astronomy

- 2024-04-08 @ Python tutorials #0
- Presented by: Akio Taniguchi (Tamura group)

![bg right:25% 75%](https://openastronomy.org/pyastro/images/pyastro_logo_150px.png)

---

# Contents

- なぜ天文学でPythonを学ぶのか
    - （電波）天文学とプログラミング
    - プログラミング言語Python
- Pythonを学ぶ上で知っておきたいこと
    - 公式の機能・ドキュメントを知る癖をつけよう
    - 「分からないこと」はどんどん質問をしよう
    - Pythonだけで全てを解決しないようにしよう
    - 他者への技術的な思いやりを持った書き方を心がけよう

---

# なぜ天文学でPythonを学ぶのか

![bg blur](https://blueskyproject.io/_assets/scipy-ecosystem.png)
<!-- _footer: https://speakerdeck.com/jakevdp/the-unexpected-effectiveness-of-python-in-science -->

---

# （電波）天文学とプログラミング

- データ解析
    - リダクション：生データから画像・スペクトルデータを生成
    - 要約・可視化：観測データのプロット・統計量への要約など
    - シミュレーション：理論モデルの生成・観測データとの比較
- 装置開発
    - 望遠鏡制御：装置間の通信制御・データ取得・観測計画立案
    - 性能評価：装置の仕様と実観測データの比較・考察

---

![bg](https://static.projects.iq.harvard.edu/files/styles/os_files_xlarge/public/eht/files/20190410-78m-800x466.png?m=1554877319&itok=ogdRX6BW)
<!-- _footer: https://eventhorizontelescope.org/blog/first-ever-image-black-hole-published-event-horizon-telescope-collaboration -->

---

![bg](https://user-images.githubusercontent.com/5890484/74090463-a0865580-4ad1-11ea-964f-0fd1ef07a851.png)
<!-- _footer: https://github.com/numpy/numpy.org/pull/160 -->

---

# プログラミング言語Python

- 特徴
    - 高水準の汎用スクリプト言語（オブジェクト指向言語）
    - シンプルで習得しやすい文法とデータ構造
    - 豊富な標準ライブラリ（battery included）
    - 科学用途の豊富な外部ライブラリ
- 用途
    - 科学計算・機械学習・ウェブ開発・通信制御など
    - 天文学に限らずプログラム初学者が学ぶ言語の筆頭候補

---

![bg fit](https://qph.fs.quoracdn.net/main-qimg-e75e13d665984b797b2f8401f7e03c1d)
<!-- _footer: https://qph.fs.quoracdn.net/main-qimg-e75e13d665984b797b2f8401f7e03c1d -->

---

# プログラミング言語Python

```python
import openai


def answer(question: str) -> str:
    """Return the answer to a given question by GPT-3.5."""
    response = openai.ChatCompletion.create(
        model="gpt-3.5-turbo",
        messages=[{"role": "user", "content": question}],
    )
    return response.choices[0].text


openai.api_key = "*****"
print(answer("Pythonを学ぶには？"))
```

---

# プログラミング言語Python

- 2024年4月時点でのPython
    - 最新バージョン：[3.12](https://docs.python.org/ja/3.12/)（2024年10月に[3.13がリリース予定](https://peps.python.org/pep-0719/)）
    - Google Colaboratoryでは[3.10が採用されている](https://colab.research.google.com/notebooks/relnotes.ipynb)
    - これから始めるなら3.10以上を使いましょう
- 参考：バージョン2.x系のPython
    - 3.x系とは文法等が互換ではないことに注意
        - 例：`3/2 -> 1` (2.x), `3/2 -> 1.5` (3.x)
    - [CASA](http://casa.nrao.edu/)など一部の天文ソフトウェアで必要になることも

---

# プログラミング言語Python

- 科学計算ライブラリ
    - NumPy, xarray, pandas: 多次元配列・表データの処理
    - SciPy, scikit-learn: 科学計算ライブラリ
    - Astropy: 天文計算ライブラリ
- 可視化ライブラリ
    - Matplotlib: 1-2次元データプロット
- その他
    - Jupyter: ブラウザ+ノートブックのPython対話実行環境

---

![bg](https://blueskyproject.io/_assets/scipy-ecosystem.png)
<!-- _footer: https://speakerdeck.com/jakevdp/the-unexpected-effectiveness-of-python-in-science -->

---

# Pythonを学ぶ上で知っておきたいこと

![bg blur](https://cdn.sstatic.net/insights/Img/Survey/2019/tech_network-1.svg)
<!-- _footer: https://insights.stackoverflow.com/survey/2019 -->

---

# 公式の機能・ドキュメントを知ろう

- [標準ライブラリ](https://docs.python.org/ja/3/library/index.html)：これだけでかなりのことができます
    - 時刻計算・並列計算・OS操作などなど
    - 全部覚える必要はないが、機能を探す癖を付けておく
- [言語ドキュメント](https://docs.python.org/ja/3/)
    - 標準ライブラリのヘルプ（引数の意味など）を全て網羅
    - Pythonのインタプリタでは`help(<関数名>)`でも見られる
- 外部ライブラリドキュメント（英語）
    - 例えば`astropy documentation`などで検索してみましょう

---

# 「分からないこと」は質問しよう

- 調べたら分かること
    - エラー（例外）の意味（大抵は検索すればヒットする）
    - ライブラリの使い方（大抵はドキュメントがある）
- 調べても分からないこと
    - ある目的に対するライブラリの使い所（技術選定）
    - 専門知識（天体物理学）を必要とするコード
- ただ、最初のうちはあまり気にせず質問した方が良いかも
    - M1以上は「○○が分からない」的な質問から脱却しましょう
---

# Pythonだけで全てを解決しないように

- Pythonにも得意不得意があります
    - 実行速度はそこまで高速ではないことが多い→外部ライブラリ
    - 文字列操作など、かえってシンプルに書きづらいことも
- 外部ライブラリが使えないかを検討する
    - 例えばNumPyの配列計算は高速な科学計算では必須
- 最適な他のプログラミング言語を検討する
    - 例えばウェブ関連の開発ならJavaScriptなど
    - （ただし、学習コスト・引継ぎコストと要相談）

---

# Pythonだけで全てを解決しないように

- シェルスクリプト（UNIXコマンド）の理解も大事
    - パイプライン：簡潔なデータ連続処理
    - 正規表現：効率的な文字列検索
- よく使われる一般的なデータ形式を知っておく
    - FITS, netCDF: 多次元配列
    - JSON, YAML, TOML: データ記述言語
    - CSV: 表形式
    - オリジナルのデータ形式は極力作らないようにしましょう

---

![bg](https://cdn.sstatic.net/insights/Img/Survey/2019/tech_network-1.svg)
<!-- _footer: https://insights.stackoverflow.com/survey/2019 -->

---

# 他者への技術的な思いやり（難しい）

- Pythonらしい標準的な書き方→tutorialsで学びましょう
    - Pythonには[標準の書き方の指針](https://pep8-ja.readthedocs.io/ja/latest/)がある
    - Pythonicな文法を使いこなす（例えばイテレータ）
- 可読性の高いコードの書き方を理解する
    - コードを複雑にしない書き方（例えば早期リターン）
    - 変数の命名方法（例えば`end`と`last`はどっちを使うべき？）
- ドキュメントを残す（例えば[Azely](https://github.com/astropenguin/azely)のdocstrings）
- **重要：ここでいう他者には「数ヶ月後の自分」も含まれます**

---

# 参考文献・書籍

- Python documentation
    - [Python 標準ライブラリ](https://docs.python.org/ja/3/library/index.html)
    - [Python コードのスタイルガイド](https://pep8-ja.readthedocs.io/ja/latest/)
- Python books
    - [スッキリわかるPython入門 第2版](https://amzn.asia/d/c03aweb)→今回使うテキスト
    - [Python ゼロからはじめるプログラミング](https://amzn.asia/d/39Ysilv)
    - [科学技術計算のためのPython入門](https://www.amazon.co.jp/dp/4774183881/ref=cm_sw_r_tw_dp_U_x_k0TUEbVANHNQMj)
    - （自分が読みやすいものなら正直何でも良いので1冊通読）

---

# 参考文献・書籍

- Library references
    - [NumPy](https://numpy.org), [pandas](https://pandas.pydata.org), [xarray](https://xarray.pydata.org/en/stable/index.html)
    - [Matplotlib](https://matplotlib.org)
    - [SciPy](https://www.scipy.org), [Astropy](https://www.astropy.org)
- Other books
    - [リーダブルコード](https://www.amazon.co.jp/dp/4873115655/ref=cm_sw_r_tw_dp_U_x_WATUEbR6S95N0)
    - [UNIXコマンドブック 第4版](https://www.amazon.co.jp/dp/4797372281/ref=cm_sw_em_r_mt_dp_U_V8pUDbKDTPHAY)
