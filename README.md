# Flow Matching / 統計デモ集（Jupyter notebooks）

本リポジトリは，生成モデル（主に Flow Matching）を「統計モデルの拡張・校正」として使うための最小デモ（ノートブック）をまとめたものです．
GitHub 上でそのまま閲覧できるように，各ノートの先頭に短い概要を付けています．

## 収録ノートブック

- `SM-ML_GMM1.ipynb`：Gaussian Graphical Model（GGM）における Penalized MLE と Penalized Score Matching の比較
- `FM_Copula1.ipynb`：Copula（S 字依存）の学習を Flow Matching で行うデモ
- `OT_Coupling1.ipynb`：ミニバッチ内 Optimal Transport（Hungarian）coupling を使った Flow Matching（two-moons）
- `MI-FM1.ipynb`：Flow Matching を用いた Multiple Imputation（多重代入）の最小デモ（IterativeImputer との比較の土台）
- `RF_FM1.ipynb`：介入分布 p(y | do(A=a)) の推定（RF の平均＋スケール＋残差再標本化 vs Flow Matching）
- `Cox_FM_PH_model1.ipynb`：Cox PH 診断と Cox+Flow(tt) による校正（rpy2 で R を呼びます）

> 実行方法・入出力・注意点は，各ノート先頭の「概要」セルにまとめています．

## クイックスタート（Python）

### 1) 仮想環境の作成（推奨）
```bash
python -m venv .venv
# Windows (PowerShell)
.venv\Scripts\Activate.ps1
# macOS/Linux
source .venv/bin/activate
```

### 2) 依存関係のインストール
```bash
pip install -U pip
pip install -r requirements.txt
```

### 3) Jupyter を起動
```bash
jupyter lab
```
ブラウザで開いたら，各ノートブックを上から順に実行（Run All）してください．

## Cox ノート（R 連携）について

`Cox_FM_PH_model1.ipynb` は `rpy2` を使って R を呼びます．
R 本体が未導入の場合は，先に R をインストールしてください．
R 側パッケージはノート内で自動インストールするようにしていますが，
オフライン環境などでは事前インストールが必要です．

- 必須（R）：`survival`, `riskRegression`, `prodlim`
- 場合により：`cancer`（`veteran` データが `survival` 側で取れない環境向けの保険）

詳細は `R_SETUP.md` を参照してください．

## 再現性メモ

- 多くのノートで乱数を使います（サンプリング，学習の初期値など）．
- 研究用途では，冒頭セルで `seed` を固定してから実行することを推奨します．
- GPU は任意です（`torch` が CUDA 対応なら自動で利用可能なことがあります）．

## ライセンス

公開目的に合わせて `LICENSE` を追加してください（例：MIT License）．
