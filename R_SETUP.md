# R_SETUP.md

`Cox_FM_PH_model1.ipynb` は Python から R を呼ぶため，R と `rpy2` が必要です．

## 1) R のインストール

- Windows/macOS/Linux：CRAN から R をインストールしてください．
- インストール後，ターミナル（または R コンソール）で `R --version` が動くことを確認します．

## 2) Python 側：rpy2 の導入

`requirements.txt` に `rpy2` を入れています．
インストール時に R を検出できない場合は，R のパス設定が必要です（Windows では特に）．

## 3) R 側パッケージ

ノートブック内で次を自動インストールします：
- survival
- riskRegression
- prodlim

環境によって `survival::veteran` が見つからない場合の保険として `cancer` を使う分岐が入っています
（不要なら分岐を外しても構いません）．

手動で入れる場合は，R コンソールで以下を実行します：

```r
install.packages(c("survival","riskRegression","prodlim"))
# 必要なら
install.packages("cancer")
```

## 4) よくあるトラブル

- `rpy2` のインストールで R が見つからない：
  - R を先に入れ，環境変数（PATH など）を通してから再試行してください．
- ノートブック上で `%%R` が動かない：
  - 最初のセル（`%load_ext rpy2.ipython`）が実行されているか確認してください．
