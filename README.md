# 倒立振子コントロールラボ

古典制御と強化学習の入門向け・対話型学習アプリ。カートポール（倒立振子）の3Dモデルを対象に、**PID制御のゲイン調整**と**Q学習（表形式強化学習）の訓練過程**を同じ画面で見比べられます。

## 使い方

`index.html` をブラウザで開くだけです。ビルド・サーバ・ネット接続は不要です。

## 機能

### PID制御モード
- Kp / Ki / Kd / カート位置ゲインをスライダーで調整
- P項・I項・D項・位置項の寄与を実時間バー表示
- 外乱ボタン（左右から突く）、転倒カウント、RMS角度・制御力RMS
- Kd=0での発振、Kp不足での転倒など、教科書の現象を体験可能

### Q学習モード
- 状態を 3×3×6×3=162マスに離散化した表形式Q学習が**ブラウザ内でリアルタイムに学習**
- 学習率α / 割引率γ / ε減衰率 / 学習速度（steps/frame）を調整可能
- 学習カーブ（エピソードリターン＋移動平均）、学習済み方策の実演モード
- 「Q学習の見ている世界」— 現在状態のQ値と最善行動を格子表示

### 共通
- three.js（WebGL PBR）によるレール・カート・振子の3D表示、制御力の矢印表示
- θ・xの時系列チャート、手動操作モード（矢印キー）
- ポール長・質量の変更、ライト／ダークテーマ、レスポンシブ

## 理論モデル

標準的なカートポール力学（Barto & Sutton 1983 / OpenAI Gym CartPole相当）。検証として、無制御での転倒・PIDによる静定（±0.12°）・Q学習の成長（平均リターン22→135/2000エピソード）を自動テストで確認済み。

## 技術構成

- 単一HTMLファイル（three.js r147同梱）
- 物理・PID・Q学習はすべて素のJavaScript。ニューラルネット・外部ライブラリ不使用

## 参考文献

アプリ内の「参考文献」パネルと同じ内容です。

### 欧文文献

1. K. J. Åström, R. M. Murray. *Feedback Systems: An Introduction for Scientists and Engineers*, 2nd ed. Princeton University Press, 2021. — PID・状態空間モデル・LQR
2. B. D. O. Anderson, J. B. Moore. *Optimal Control: Linear Quadratic Methods*. Prentice Hall, 1990（Dover 復刊 2007）. — LQR
3. K. J. Åström, K. Furuta. Swinging up a pendulum by energy control. *Automatica*, 36(2), 287–295, 2000. [doi:10.1016/S0005-1098(99)00140-5](https://doi.org/10.1016/S0005-1098(99)00140-5) — スイングアップ
4. A. G. Barto, R. S. Sutton, C. W. Anderson. Neuronlike adaptive elements that can solve difficult learning control problems. *IEEE Transactions on Systems, Man, and Cybernetics*, SMC-13(5), 834–846, 1983. [doi:10.1109/TSMC.1983.6313077](https://doi.org/10.1109/TSMC.1983.6313077) — 本アプリの物理モデルの出典
5. E. Hairer, C. Lubich, G. Wanner. *Geometric Numerical Integration*, 2nd ed. Springer, 2006. [doi:10.1007/3-540-30666-8](https://doi.org/10.1007/3-540-30666-8) — 数値積分（本アプリは半陰的オイラー法、Δt=1/120 s）

### 和文文献

6. 川田昌克 編著，東 俊一 ほか 共著. 『倒立振子で学ぶ制御工学』. 森北出版, 2017. ISBN 978-4-627-79221-0 — PID・状態空間モデル・非線形制御
7. 杉江俊治，藤田政之. 『フィードバック制御入門』（システム制御工学シリーズ 3）. コロナ社, 1999. ISBN 978-4-339-03303-8 — PID・古典制御
8. 小郷 寛，美多 勉. 『システム制御理論入門』（実教理工学全書）. 実教出版, 1979. ISBN 4-407-02205-1 — 状態空間モデル・LQR
9. 齊藤宣一. 『数値解析入門』（大学数学の入門 9）. 東京大学出版会, 2012. ISBN 978-4-13-062959-1 — 常微分方程式の数値解法

---
🤖 Generated with [Claude Code](https://claude.com/claude-code)
