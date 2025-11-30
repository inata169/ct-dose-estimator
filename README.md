# CT Dose Estimator

CT撮影条件から被ばく線量（CTDIvol・DLP・実効線量）を推定するWebツール

## デモ

GitHub Pages: https://inata169.github.io/ct-dose-estimator/

## 機能

### 入力項目
- 撮影部位（頭部 / 頸部 / 胸部 / 腹部 / 骨盤 / 胸腹部 / 全身）
- 管電圧（80 / 100 / 120 / 135 / 140 kV）
- mAs（管電流時間積）
- スキャン長（cm）

### 出力
- **CTDIvol**（容積線量指標）: mGy
- **DLP**（線量長さ積）: mGy・cm
- **実効線量**: mSv

## 計算方法

### CTDIvol
```
CTDIvol = 基準CTDIvol × (kV / 120)^2.5 × (mAs / 100)
```

### DLP
```
DLP = CTDIvol × スキャン長
```

### 実効線量
```
実効線量 = DLP × k-factor
```

### 部位別 k-factor（ICRP Publication 103 準拠）

| 部位 | k-factor (mSv/mGy・cm) |
|------|------------------------|
| 頭部 | 0.0021 |
| 頸部 | 0.0059 |
| 胸部 | 0.014 |
| 腹部 | 0.015 |
| 骨盤 | 0.015 |

## 技術仕様

- HTML / CSS / JavaScript 単一ファイル構成
- 外部ライブラリ不使用
- レスポンシブデザイン（スマートフォン対応）
- ダークモード対応
- GitHub Pages で公開可能

## 注意事項

この計算結果は概算値です。実際の被ばく線量は以下の要因により異なります：

- 使用するCT装置の機種
- 撮影プロトコル
- 患者の体格
- ピッチ設定

正確な線量は各施設のCT装置の線量レポートをご確認ください。

## 参考文献

- ICRP Publication 103: The 2007 Recommendations of the International Commission on Radiological Protection
- AAPM Report No. 96: The Measurement, Reporting, and Management of Radiation Dose in CT

## ライセンス

MIT License
